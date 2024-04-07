---
date: 2024-03-27T05:00:00-00:00
description: "Every Active Directory forest and domain should have LDAPS implemented, but in very few cases it is actually done. The topic can be intimidating because it involves certificates, but once you understand some basic concepts, it's easier to tame than it seems. Let's see how to implement it!"
featured_image: "/images/01-the-lab-episode03-ldaps.jpg"
images:
  - "/images/01-the-lab-episode03-ldaps.jpg"
categories : [ "Identity & Security" ]
tags: [ "Active Directory", "LDAPS", "Video" ]
title: "The LAB - Episode 3 - Implementing LDAPS in Active Directory on-premises"
url: /en/ldaps-active-directory-on-premises
---
Every forest and Active Directory domain should have LDAPS implemented, but in very few cases is it actually implemented. The topic can be intimidating because it involves certificates, but once you understand some basic concepts, it's easier to tame than it seems. Let's see how to implement it!

## Video
You can find the entire video below, or you can continue reading the article.

{{< youtube sqWKhZPsEJU >}}

## Article
With all this talk about the cloud, I realized that I have neglected our beloved Active Directory! We must not and cannot forget about it because in the vast majority of companies, it is the designated authority for identity management, and it is those identities that we synchronize through Azure AD Connect that we need to secure.

Today, I will tell you how to secure the entire Active Directory infrastructure by implementing the secure version of the LDAP protocol: **LDAPS**!

## What is LDAP?
I believe that almost everyone knows what it is, but I'll quickly repeat it just to talk about it, perhaps with younger colleagues or, to put it more elegantly and modernly, with "cloud-native" colleagues. 😉

The LDAP protocol, which stands for Lightweight Directory Access Protocol, is a network protocol used to access and manage information within a directory. For example, any registry application that needs to retrieve data and attributes of a user in our AD uses LDAP to do so. In short, LDAP helps us access and manage the information of the objects stored within it: users, groups, computer accounts, and so on.

## How does it work?
Physically, how do we retrieve this information? Without going into the formally technical details of the protocol and connectivity, let's say that to retrieve what is needed when making an LDAP query, you typically connect to the domain controllers on TCP port 389 and authenticate with a username and password (sent in clear text).
This last operation is called "LDAP bind." So, the bind is nothing more than an authentication operation performed by an LDAP client to establish a connection and gain access to Active Directory or a specific part of it.

As I mentioned earlier, this operation typically has always been done in clear text: when this happens, we refer to it as "simple bind."

{{< youtubestartend sqWKhZPsEJU 134 157 >}}

As you saw, everything happens in clear text, and the fact that it happens in clear text... we don't like it. 😠

And it is precisely this that we will focus on today, with our security axe made up of certificates and other ugly things! LDAPS, in fact, is the secure version of the protocol that will allow us to say "Goodbye" to our simple binds... or Simple Minds... as you wish.

## Implementing and using LDAPS
How does all this happen? LDAPS connections take place on TCP port 636, and the bind will occur through certificates issued by our Certification Authority.

The objective today, therefore, is to ensure that it is no longer possible to perform a clear text LDAP bind.

At a high level, what will we do, and what do we need?
- A certificate template suitable for the occasion.
- Publishing the template in AD.
- Enrolling the certificates on the domain controllers.
- Verifying that connectivity on port 636 is working.
- Configuring a couple of GPOs to instruct the domain controllers to accept only LDAPS queries and instruct clients and servers to only send secure requests in LDAPS.
- Testing that they can no longer perform clear text binds on the DC.

At this point, you may already have some questions, for example:

> *"What happens if there are applications or, more generally, elements of my infrastructure that do not support LDAPS?*

I will try to answer all the doubts that may arise, later in the video. For now, let's focus on how to implement it.

However, as always, the usual concept applies: everything you see in my videos is done in a lab environment, where there are conditions and configurations that are certainly different from your production environment. So, use this video only as a starting point to apply these concepts within your specific reality. Okay?

### Creating the certificate template
Alright, now let's create and publish the certificate template on Active Directory! I have chosen to use the Kerberos Authentication template as a base, with some modifications.

{{< youtubestartend sqWKhZPsEJU 288 375 >}}

### Configuring certificate autoenrollment and testing
For convenience, and since the situation in my lab environment allows it, I have chosen to have the LDAPS certificate managed through autoenrollment directly by the domain controllers. If you noticed earlier, in the permissions tab while creating the template, the domain controller domain group had autoenrollment permissions.

Now let's see the initial state of the domain controller. After that, we will create the GPO for autoenrollment, apply it, and see if the certificate has been distributed correctly!

{{< youtubestartend sqWKhZPsEJU 406 484 >}}

### Testing connection on TCP port 636
If everything went as expected, and it seems so, we should now be able to connect to TCP port 636 of the domain controller. Let's see if that's the case!

{{< youtubestartend sqWKhZPsEJU 493 512 >}}

Perfect, it works!

### Configuring GPOs for LDAPS signing
Now it's time to create a couple of GPOs.

The first one will be applied to the Domain Controllers and will instruct them to accept only secure binds.

{{< youtubestartend sqWKhZPsEJU 525 565 >}}

The second one will be applied to the OUs that contain the computers and servers in your domain, which in this context are LDAP clients. With this GPO, we will configure the LDAP clients to use LDAPS exclusively!

{{< youtubestartend sqWKhZPsEJU 581 638 >}}

### Testing simple bind
After applying the GPOs, let's check if we can perform a simple bind like we were able to do at the beginning of the video.

{{< youtubestartend sqWKhZPsEJU 645 667 >}}

Great, we can no longer perform a simple bind, which is exactly what we wanted!

### What about doubts? How to plan the implementation of LDAPS?
Now I will try to address the main doubt that may have come to your mind while watching this video.

> *Can I implement this configuration as it is?*

The answer is "probably NO" or, at least, "not immediately" because within your infrastructure, there are probably still applications, servers, or, hopefully not, clients that are still performing LDAP queries in clear text.

**How can you know who or what is performing clear text LDAP queries?**

You need to start with an auditing activity, which can be easily implemented by distributing some registry keys on the domain controllers. Here is some fresh and detailed documentation to help you with that:
- [How to discover clients that do not use the Require signing option](https://learn.microsoft.com/en-us/troubleshoot/windows-server/identity/enable-ldap-signing-in-windows-server#how-to-discover-clients-that-do-not-use-the-require-signing-option)
- [How to configure Active Directory and LDS diagnostic event logging](https://learn.microsoft.com/en-GB/troubleshoot/windows-server/identity/configure-ad-and-lds-event-logging)

Once the audit is completed, you will have a complete list of the machines that perform clear text LDAP queries. At that point, you will need to reconfigure these systems/applications to perform LDAPS queries, which are secure. Until then, on the Domain Controller side, you should not set the GPO to "Require Signing" as it could cause some issues.

## Conclusion

As always, having good knowledge and conducting a preliminary analysis of your infrastructure are very useful in understanding how to proceed without causing any damage.

I hope this video has been helpful to you. In this crazy cloud world, Active Directory should never be neglected!
Have you implemented LDAPS? If so, let's discuss it in the comments and on my social profiles!

As always, thank you for following along, and if you enjoyed this video and topics like this, subscribe to my YouTube channel!

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< / rawhtml >}}

Until next time, I'll be waiting... you LEGENDS!