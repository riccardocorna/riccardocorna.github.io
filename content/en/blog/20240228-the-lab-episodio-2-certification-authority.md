---
date: 2024-02-28T05:00:00-00:00
description: "Today a very fast but fundamental video: we add the second piece of the lab, putting a Certification Authority on track."
featured_image: "/images/01-the-lab-episode-2-enterprise-certification-authority.jpg"
images:
  - "/images/01-the-lab-episode-2-enterprise-certification-authority.jpg"
categories : [ "Identity & Security" ]
tags: [ "The Lab", "Certification Authority", "Episode 2" ]
title: "The Lab - Episode 2 - Installing an Enterprise Certification Authority"
url: /en/the-lab-episodio-2-certification-authority
---
IT Specialists, hello everyone! Today a very fast but fundamental video: we add the second piece of the lab, putting a Certification Authority on track.

## Video
Find the entire video below, or you can continue reading the article.

{{< youtube 4U9W6x399Ms >}}

## Why is a Certification Authority useful in the lab?
Here's why a Certification Authority can be useful in the lab:
1. Because a CA is always useful, regardless. 😊
2. Because I want to implement LDAPS on Active Directory right away (and the next video will talk about this).
3. Because, later in the lab, I want to implement Certificate Based Authentication directly on Microsoft Enter.

## Tips and resources for designing a real PKI infrastructure
As you'll see shortly, we'll get straight to the point without too many frills. It's not the purpose of this video to explain in detail how many and what types of Certification Authorities exist or to fully explore how to design a PKI infrastructure.

Let's just say that, in a lab environment, it's more than enough to install an Enterprise CA to leave it always active and at our disposal.

**In a production environment, however, it needs to be designed much more carefully.**

It could be a 2 or 3-tier infrastructure, in the most complex cases, and last but not least, it's a good idea to turn off the Root CA and keep everything in a secure location.

But, as I said, the topic is far too vast to cover it here in our lab.

So, to delve into the topic, I leave you with a series of great articles from Microsoft Tech Community:

- [Designing and Implementing a PKI: Part I Design and Planning](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-i-design-and-planning/ba-p/396953)
- [Designing and Implementing a PKI: Part II Implementation Phases and Certificate Authority Installation](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-ii-implementation-phases/ba-p/397198)
- [Designing and Implementing a PKI: Part III Certificate Templates](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-iii-certificate-templates/ba-p/397860)
- [Designing and Implementing a PKI: Part IV Configuring SSL for Web Enrollment and Enabling Key Archival](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-iv-configuring-ssl-for-web/ba-p/399104)
- [Designing and Implementing a PKI: Part V Disaster Recovery](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-v-disaster-recovery/ba-p/399106)

## Installation and configuration of Active Directory Certificate Services
As usual, I have a Windows Server 2022 Datacenter machine ready in Azure, with the smalldisk image, I joined it to the domain, and so we are ready to install and configure the role!

{{< youtubestartend 4U9W6x399Ms 117 214 >}}

You won't believe it, but we're done already: our CA is up and running, ready to be used.

Now that we're ready to produce certificates en masse, **in the next video, we'll see how to implement LDAPS on Active Directory**.

## Conclusions
As you may have noticed, today's video was very fast-paced and, during this series, there will be longer videos alternating with much faster ones, depending on what we need to implement.

In any case, thank you for following me even in this video and, if you liked it and if you like this type of content, subscribe to my YouTube channel: it costs you nothing but, for me, it's very important and makes all the difference!

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< / rawhtml >}}

Until next time, I'll be waiting for you... LEGENDARY!

Your IT Specialist,  
Riccardo
