---
date: 2023-05-24T05:00:00-00:00
description: "How to manage membership of local groups for Azure AD-joined PCs? In this video, we will see how the Local User Group Membership policy works within the scope of Account Protection in Intune. Additionally, we'll provide some tips for easily converting ObjectId and SID of Azure AD groups and roles."
featured_image: "/images/01-intune-account-protection-local-user-group-membership-cover.png"
categories: [ "Modern Endpoint" ]
tags: ["Intune", "Azure AD Join", "Local Administrators"]
title: "Intune Account Protection: Local user group membership"
url: /en/intune-account-protection-local-user-group-membership
---
IT specialists, hello everyone! After playing with [the new Windows LAPS](https://youtu.be/oGbAqOxJOhQ) in my previous video, I was reviewing the list of local administrators on my lab machine, and since the machine is registered in Azure AD Join, the Azure AD user who joined it has become an administrator.

This is a normal and expected behavior, but... we don't like it.

In addition to this, by default, anyone with the Global Admin role or the Azure AD Joined Device Local Administrator role becomes a machine administrator. So, how can we avoid the user of an Azure AD-joined machine from becoming a permanent machine administrator? More generally, what options do we have in Azure AD to manage local machine administrators?

There are several possible options, let's see them!

1. With Autopilot, you can configure the profile so that once the Windows machine is joined to Azure AD, the user is a standard user. However, if, like in my case, the PC is not under Autopilot, we need to think of something else.
2. We can use the additional local administrators management option, which can be found in the Device Settings in Azure AD. However, this approach poses some issues because we end up adding more administrators who will have access to all machines joined to Azure AD. The setting is global and cannot be assigned to a group of machines.
3. A Local User Group Policy that can be set from Account Protection within the Endpoint Security node of Intune.

I have chosen the latter solution! Let's understand what can be done and how it works. With this solution, we can modify the local group membership on a group-by-group basis, adding or even replacing the existing memberships with what we want. Additionally, we can add existing local machine users (such as the LAPS user), directory users, groups, and even Azure AD roles. Finally, we can target and deploy policies to groups of machines, differentiating the settings if necessary.

In short, it seems to be exactly what we need!

As mentioned earlier, we can manage local groups by adding Azure AD users, groups, and roles. However, we need to be careful with the format in which these entries are added:

- For cloud users: AzureAD\username@domain.com
- For users synchronized from on-premises AD: DOMAIN\samAccountName
- For groups: we need to use the SID
- For roles: we need to use the SID

And here's the interesting part: converting between ObjectId and SID for groups is quite easy. You can simply provide one of the two parameters to a PowerShell script or (as I did) an online tool. If we want to include a group in our policy, we can go to the portal, convert the ObjectId to a SID, and then enter the SID in our policy. As for Azure AD roles, neither the SID nor the ObjectId are directly exposed in the portal. For example, if we want to include those with the Azure AD Joined Device Local Administrator role among the administrators, how can we verify their SID?

We'll see that in a moment, but first, a brief overview of the environment and what you will see exactly, as well as what we aim to achieve.

I have a Windows 11 machine joined to Azure AD.

In the local administrators group, there are a few accounts that we can overlook, my standard user with which I performed the Azure AD Join (and who is an administrator), and as you will see, there are two SIDs. One belongs to the Global Admin role, and the other belongs to the Azure AD Joined Device Local Administrator role. How do we determine which SID belongs to which role?

We'll find out shortly, but let's first see how the machine is configured before implementing the policy!

{{< youtubestartend wFiocHs-MQ4 253 280 >}}

The list of administrators is what I mentioned earlier.

Now, what configuration do I want to achieve? I want the only local administrators on the machine to be the LAPS user and anyone with the Azure AD Joined Device Local Administrator role, that's it!

A note about this configuration: I have set it up this way purely for educational purposes, to show that it's possible to include roles and to demonstrate how to find the SID and ObjectId of an Azure AD role. From a security standpoint, this configuration potentially exposes our PCs to lateral movement since we added an entire Azure AD role to the local administrators, albeit not the Global Admin role. It is not the topic of this video to discuss the possible configurations because every environment is different, and every situation has its own requirements. This type of policy should always be shared and agreed upon with the client or the relevant parties before being put into production.

However, we can certainly consider:

- Removing the Global Admins
- Adding the LAPS user, who is essentially the renamed built-in Administrator and must be included, otherwise the policy will fail, in replace mode
- If you decide to keep the Azure AD Joined Device Administrator role, as I did, you might consider putting it under Privileged Identity Management (PIM).

I won't discuss this configuration now, but if you want me to make a video about it, leave a comment.

Great, now let's see which of the two SIDs corresponds to the role we have chosen to remain in the local admins, convert it to an ObjectId, and query Microsoft Graph to verify that we have the correct SID!

{{< youtubestartend wFiocHs-MQ4 385 439>}}

Luckily, I chose the right role, the one with the very long name! 😉 Now, all that's left is to implement the Intune policy. But first, one final clarification.

Within the policies, we have three actions available:
1. Add in Update: specifies who to add to the group, and any existing members not specified in our list will not be affected in any way.
2. Remove in Update: specifies who to remove, and similarly to before, any existing members not specified in our list will not be affected.
3. Add in Replace: this has a more significant impact because we specify the group members, and the end result will be that any existing member not in our list will be removed, so be careful!
As I mentioned before, since we are in a lab environment and have already made all the necessary considerations, I will add the LAPS user and the Azure AD Joined Device Local Administrator role in Replace mode.

So what do we expect? That all other machine administrators are swept away, including the Global Admins and my user who joined the PC to Azure AD. Only what I have included in the list should remain.

Let's see how to configure the policy!

{{< youtubestartend wFiocHs-MQ4 521 603>}}

And now let's see what happened to our administrators.

{{< youtubestartend wFiocHs-MQ4 608 626>}}

Perfect, it worked! The only local administrators now are the LAPS user and anyone with the Azure AD Joined Device Local Administrator role!

Repetita Iuvant: What I have done is a rather strong configuration. Before implementing something similar in production, perform all the necessary checks and analysis.

If you want to delve deeper into the topic, as always, I provide you with some fresh documentation that smells like fabric softener!

And you, dear IT specialists, have you already used this policy? If yes, how did you configure it? Let's discuss it in the comments or on my social profiles!

And... speaking of social profiles, subscribe to my YouTube channel! It means a lot to me, it doesn't cost you anything, and this way you'll be sure not to miss any content! I'll be waiting for you!

See you soon... You rock guys!

Riccardo