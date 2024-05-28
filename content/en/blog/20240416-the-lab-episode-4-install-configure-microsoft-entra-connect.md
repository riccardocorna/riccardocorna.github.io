---
date: 2024-04-16T05:00:00-00:00
description: "We are finally at a turning point in the creation of our hybrid lab. Today, we are preparing our environment for the installation, configuration, and activation of Entra Connect."
featured_image: "/images/01-the-lab-episode-4-entra-connect.jpg"
images:
  - "/images/01-the-lab-episode-4-entra-connect.jpg"
categories : [ "Identity & Security" ]
tags: [ "Microsoft Entra Connect", "Active Directory", "Video" ]
title: "The Lab - Episode 4 - Install and configure Microsoft Entra Connect"
url: /en/the-lab-espisode-4-install-configure-microsoft-entra-connect
---
Hello IT specialists! We are finally at a turning point in creating our hybrid lab, which until now has been very little hybrid, since we created an AD forest and installed a Certification Authority, all on-prem components.

## Video
Find the full video below, or you can continue reading the article.

{{< youtube SPL4Bwz3Z50 >}}

## Installing and Configuring Microsoft Entra Connect

Today, we prepare our environment for the installation, configuration, and activation of Entra Connect. Yes, we are finally hybridizing our environment, synchronizing identities with Entra ID. Again, various and endless chapters could be opened on how to design and set up a synchronization strategy with Entra ID.

### Design Decisions

Let's look together at the main design and decision-making challenges.

#### Synchronization Mode
Microsoft has long been pushing harder for what is called Cloud Sync, instead of Connect Sync (which we are more accustomed to with the Entra Connect server or, for the nostalgic, Azure AD Connect).

What is Cloud Sync? A more "lightweight" method, so to speak, of synchronizing identities between AD and Entra, based on an agent. It is very useful in specific situations, such as in a multi-forest topology where the forests are disconnected from each other. Then there is the classic Connect Sync.

How to choose between Connect Sync and Cloud Sync? Beyond the specific case I mentioned earlier, to delve deeper into the topic, I'll leave a nice link below!

🔗 [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)

#### Directory and Tenant Topology
How many Active Directory forests do you need to synchronize?  
In the case of a multi-forest environment, are users represented multiple times in the various forests?  
Or do you need to synchronize across multiple tenants?  

You need to plan, design, and prepare everything carefully to avoid unsupported situations that could jeopardize synchronization consistency!

Again, I'll leave a beautiful and clear document on supported Entra Connect topologies, which will greatly help you in this planning phase, certainly one of the most delicate!

🔗 [Topologies for Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/plan-connect-topologies)

#### Hybrid Authentication Architecture
What do we do? Do we synchronize passwords with Password Hash Sync? Do we install an ADFS to ensure that all authentications still happen on Active Directory on-prem?

Or, if we want to keep the endpoint of authentications on our on-premises Active Directory, do we set up Pass Through Authentication with some agents installed on the on-prem servers?

There are several possibilities. Starting from the premise that I would discard ADFS a priori, given that Microsoft itself has been providing tons of tools and has been carrying out major workshops and communication campaigns to convey the idea that it is time to phase out ADFS!

We are left with PHS and PTA. I'll leave here in the description another beautiful document containing a decision flowchart to help you choose the ideal hybrid authentication mode for your environment and goals.

🔗 [Choose the right authentication method for your Microsoft Entra hybrid identity solution](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn)  
🔗 [What is password hash synchronization with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-phs)  
🔗 [User sign-in with Microsoft Entra pass-through authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta)  
🔗 [What is federation with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-fed)

### Configuration Chosen for Our Lab

Back to us: what did I choose for our lab? Let's see it point by point based on the key decisions I talked about earlier:

1. **Synchronization Mode** with **Entra Connect Sync**, because my goal is to test an environment as close as possible to what you might find "out there in the real world," where the vast majority use Entra Connect.
2. **Topology**: here there's not much to choose, it's a lab based **on a single tenant and a single-domain forest**.
3. **Hybrid Authentication Architecture**: I want to try to enable a scenario as cloud-oriented as possible so that I can more easily implement evolutionary actions that help reduce dependency on Active Directory, so the choice is **Password Hash Sync**.

Great, having covered the main design decisions, everything is set, let's get our hands dirty!

### Custom Domain Verification on the Tenant

I already have my verified public domain on the tenant; I didn't document this part because I didn't take videos when I did it. If you want the details, I'll leave a link below to a guide written by my friend Nicola Ferrini from ictpower.it: in the first part of the guide, you'll find an example of how to verify and configure a custom domain.

📌 [Configure Microsoft Entra Connect to synchronize identities with Entra ID](https://www.ictpower.it/cloud/configurare-microsoft-entra-connect-per-sincronizzare-le-identita-con-entra-id.htm)

### Adding the Domain as a UPN Suffix on Active Directory
Let's start preparing our AD by adding our custom domain among the possible suffixes usable in the user's User Principal Name.

{{< youtubestartend SPL4Bwz3Z50 328 339>}}

### IdFix and UPN Remediation
Okay, now we need to ensure that all users we want to synchronize have our custom routable domain as UPN, and that everything is in order, especially regarding special characters and other attributes.

Remember, as the FQDN of our on-premises domain, we chose itspecialist.local, a non-routable domain.

And what if we have users using itspecialist.local as UPN? What do we do?

And what if someone has special or unsupported characters in the username for Entra Connect? What do we do?

We need to find these users and clean them up!

Do we have to do it manually? No, to find them we can use IdFix, a free tool released by Microsoft that, after querying AD, will find all non-compliant situations for us regarding correct synchronization of AD with Entra.

To download it and learn more about its functionality and error codes, I'll leave a link below.

🔗 [Microsoft IdFix tool](https://microsoft.github.io/idfix/)

Let's install it and see it in action, finding users with non-routable UPNs and users with unsupported characters during sync.

{{< youtubestartend SPL4Bwz3Z50 425 468 >}}

Got them! Now we undertake the necessary corrective actions and run the query again to verify we have actually corrected everything.

{{< youtubestartend SPL4Bwz3Z50 476 504 >}}

Great, we've cleaned everything up! Of course, I did it manually because there were only 2 objects, but especially for correcting UPNs, the best solution if you have many users is to script everything with PowerShell!

### Installing Entra Connect

Let's move on, now we are ready, FINALLY, to install Entra Connect!

Let's start the setup and configure it by customizing the options based on the decisions made earlier!

In addition to the configurations derived from the design decisions, as you'll see, I've also set other settings.

I'll preview them here before starting the wizard.

1. I configured Single Sign-On, even though, in theory, we shouldn't need it, but you never know!

2. I let Entra Connect create the service account that will perform the synchronization. This way, Entra Connect handles creating it with minimal permissions, and I don't have to worry about managing its credentials.

3. I configured, as the synchronization scope, only some Organizational Units because I don't want to bring unnecessary objects to the cloud or, HORROR, synchronize privileged users and groups. **Don't do it!**

4. I configured the password writeback, which will be VERY useful when we implement the Self Service Password Reset!

5. Finally, I chose as the anchor (or ImmutableID) the attribute ***ms-DS-ConsistencyGuid***: this is the best choice I recommend even in production environments, and if you are still using ObjectGUID as the anchor, consider an evolutionary action in this sense in your environment, especially if multi-forest!

Great, let's finally see the setup!

{{< youtubestartend SPL4Bwz3Z50 615 766 >}}

Done! Before concluding, let's just check that the sync was successful.

### Sync Verification

{{< youtubestartend SPL4Bwz3Z50 772 787 >}}

Great, we're done, everything synchronized!

## Conclusions
As you saw during the wizard execution, it was all very simple and quick but only and exclusively because we dedicated the right efforts, the right attention, and the right time to the planning and design phase.

If you approach this initial phase correctly, everything becomes simpler, faster, and more natural.

Never underestimate this phase and FIGHT to dedicate the right attention to it!

Today's video was tough, so a double thank you for surviving until the end, with me talking nonsense and saying bla bla bla!

If you liked it and if you like this type of content, subscribe to my YouTube channel: it costs you nothing, just a click, but for me, it is very important!

For all other updates, I also look forward to seeing you on LinkedIn and on my blog ITSpecialist.cloud.

See you soon! AWESOME!
