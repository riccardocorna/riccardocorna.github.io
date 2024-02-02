---
date: 2024-02-14T05:00:00-00:00
description: "Finally, we are truly getting our hands dirty in this lab: today, we create the on-premises Active Directory forest (and domain) needed for our hybrid environment."
featured_image: "/images/01-the-lab-episodio-1-new-active-directory-forest.jpg"
images:
  - "/images/01-the-lab-episodio-1-new-active-directory-forest.jpg"
categories: ["Identity & Security"]
tags: ["The Lab", "Active Directory", "Episode 1", "Domain Controller"]
title: "The Lab - Episode 1 - Creating a New Active Directory Forest"
url: /en/the-lab-episode-1-nuova-foresta-active-directory
---
IT Specialists, hello everyone! Finally, we are truly getting our hands dirty in this lab: today, we create the on-premises Active Directory forest (and domain) needed for our hybrid environment.

## Video
Find the entire video below, or you can continue reading the article.

{{< youtube NIYKflNX2BY >}}

## Before We Begin
Just a couple of observations.

First observation: as mentioned in the previous video, what I will show you in building the lab will be seen more from the perspective of identity (users and devices) and their security.

Anything related to proper sizing of Active Directory, data center-related issues, and capacity will not be covered in this series of videos. There are channels and resources more focused on these topics than I can provide.

To cover all bases, I will try to leave you with all the possible and useful in-depth links in the descriptions of each video.

Second observation: if it's not clear yet, this is a lab! So, what does that mean? It means that, no matter how hard I try to follow every best practice, we might not do everything "perfectly," in a "super orthodox" manner, for various reasons.

1. Despite having an Azure subscription obtained through the MVP status, I don't have infinite resources on Azure. Like everyone else, I need to optimize compute resources. Most likely, excluding the dedicated domain controller, I will install several other roles on the same machine. Of course, all within the limits of compatibility between services and, obviously, not for production use.

2. To keep the lab alive, I have to manage it, and like everyone else, I don't relish the idea of managing another super-complex environment in my free time, in addition to the ones I already deal with daily.

3. It's a lab with a fairly specific purpose (check out the introduction video if you haven't seen it, I'll leave the link below in the description), so, for purely technical and editorial choices, I will only delve into aspects relevant to the purpose of this series.

Of course, if you think I've forgotten something, write it in the comments! It could be an idea to add later in this lab!

## Setting up Active Directory Domain Services Role
Alright, here we go! I already have a machine ready on Azure, with a couple of interesting configurations on the Azure side that we'll see later, but I think we're ready to start.

Let's begin with the standard Windows role installation wizard.

{{< youtubestartend NIYKflNX2BY 179 222 >}}

## DCPromo
Perfect, all good, now let's do the exciting part: let's create a new Active Directory forest, with the Windows Server 2016 functional level, the highest and latest available as of the moment I'm recording this video.

> **NOTE:** With the next release of Windows Server 2025, I expect changes in functional levels.

### Choosing the FQDN: routable or non-routable?
As you'll see, I chose a non-routable FQDN different from the actual domain we will use publicly. In my view, this avoids some hassles in DNS and UPN management. If you want to delve into this aspect, I've left a link below in the description to clarify any doubts!

{{< youtubestartend NIYKflNX2BY 313 335 >}}

### Choosing the Directory Service Restore Mode Password
Make sure to choose a secure Directory Service Restore Mode password, note it down, and keep it safe.

In a production environment, it is typically stored in a safe or in a secure password repository, such as CyberArk or similar.

{{< youtubestartend NIYKflNX2BY 362 381 >}}

### Where to place the database, logs, SYSVOL
Where to place the DB, logs, and various AD folders? On this machine, I have a second disk, so I'm putting everything there.

From my field experience, I can say I've seen every approach: some do it, some put everything on C:, it depends on many factors.

I did it this way because I believe it's a good practice, and also because, being my DC on Azure, there's an issue related to host caching that Active Directory doesn't like very much. So, I want to make sure I have a disk without host caching.

I'll show you the setting on the Azure portal quickly.

{{< youtubestartend NIYKflNX2BY 421 428 >}}

### Conclusion of DCPromo
Now let's proceed with DCPROMO and finish it!

{{< youtubestartend NIYKflNX2BY 433 469 >}}

Perfect, the server has restarted, and we are almost done with this first phase!

## Active Directory Subnets and Sites
I'll make one last setting on Active Directory sites: I only have one, but I still want to do it, and I'll add the IP address space of our virtual network.

{{< youtubestartend NIYKflNX2BY 487 499 >}}

## Creating Organizational Units Tree
Alright, now we're ready to create some Organizational Units!

Of course, I made up the logical tree, putting OUs that are typically found almost everywhere but done in this way could be very useful for Active Directory tiering.

Let's see!

{{< youtubestartend NIYKflNX2BY 520 574 >}}

## DNS Setting for Azure Virtual Network
Last thing, on the Azure side: I set the private address of my domain controller as the DNS for the entire Virtual Network.

By doing this, every other server I create in this virtual network will use our domain controller as the DNS server from the start.

Of course, this is a configuration that suits me as a lab: in production, you might have a completely different network topology, so make the necessary checks before setting up something like this.

{{< youtubestartend NIYKflNX2BY 606 612 >}}

## Conclusion
Alright, I'd say we're done! In the next video, we will see the installation of the Certification Authority because, from my point of view, implementing LDAPS is mandatory right from the start!

As always, thank you for following me so far. If you enjoyed this video and like these topics, subscribe to my YouTube channel and follow me on my blog ITSpecialist.cloud.

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< / rawhtml >}}

Until next time, I'll be waiting... LEGENDARY!
