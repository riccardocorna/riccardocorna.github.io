---
date: 2024-01-31T05:00:00-00:00
description: "Let's begin introducing the lab I'm building, based on Microsoft Entra, Active Directory, Microsoft Intune, Microsoft 365, and Microsoft Defender for Endpoint."
image: "01-the-lab-episodio-0-introduzione.jpg"
categories : [ "Security" ]
tags: ["The Lab", "Introduction", "Episode 0"]
title: "The Lab - Episode 0 - Introduction to the Lab"
url: /en/the-lab-episodio-0-introduzione
---

IT Specialists, hello everyone! It's been a while since we last met on video, but despite that, during these months of absence, I've been scheming in the shadows, advancing other projects and initiatives, the results of which you will see on my channels and the Microsoft Security Italian Users Group community. 😉

But enough chit-chat, this is neither the video nor the right occasion to tell you the why, the how, etc. If you are watching this video, it's because you are passionate about everything related to Microsoft Entra, Intune, Active Directory, Microsoft 365, and so, let's put aside the stories and start looking at... THE MEAT!

## Video
Find the entire video below, or you can continue reading the article.

{{< youtube 80OXHAhVQhk >}}

## Introduction

Around the end of 2023, I posted an innocent post where I told you about my plan to rebuild my hybrid lab to test a series of things.

Naively, I asked if you were interested in seeing some videos taken during the lab's construction.

This is where the plot thickens...

I shouldn't have done it! In my head, I thought, "Well, it's a lab, who would be interested?"... really, I considered it a very uninteresting thing. But more than 100 of you expressed explicit interest in this topic, and, I'll tell you more, I believe it's one of the most-viewed posts of 2023!

So... could I disappoint you? Obviously NO, and thus, here's the idea!

Unlike my past videos, not just standalone videos talking about various topics sporadically, but a series, a real path of videos connected by a subtle thread: building an environment together, step by step.

So, let's see what we're going to build!

## How will this lab be set up?

First of all, I decided to build a HYBRID lab, with an on-premises Active Directory. This may seem counterintuitive, but I believe that having a hybrid lab is the most useful choice for both me, testing things, and especially for you IT specialists who follow me!

## Why a hybrid lab?

Why? Because, despite the direction taken by Microsoft and the market inexorably leading us to the cloud, reducing dependence on on-premises infrastructures, etc., before shouting "The cloud, the cloud!" we need to consider some key elements.

Companies and, more generally, entities born in recent years, and all those that will be born from now on (in 2024), are already set up to be "cloud first."

However, the fabric of the information systems of Italian companies, from small/medium enterprises to larger and more structured ones, invested in one or more on-premises infrastructures 10, 15, 20 years ago, in many cases based on Active Directory and other Microsoft or non-Microsoft products.

This means that, as IT specialists, we have an extremely delicate and important task: to guide, help, take all these entities by the hand and lead them towards this crazy cloud world, taking into account the technological legacy they carry and that is still doing its duty.

So, the spirit of this lab is to try together to start thinking about a way to reduce dependence on Active Directory, implementing and testing what we have available today and what we will have available as new tools are released.

## Microsoft Entra Kerberos, the core of the lab

Perfect, let's take the second step, the most interesting one in my opinion: the Active Directory will only be used to synchronize users (via Entra Connect) and to join any servers. That's it.

So, no Windows 10/11 clients will be joined to this on-prem domain. End-user devices will be joined directly to the cloud, on Microsoft Entra.

In other words, end-user devices will be Entra Joined.

Think about it: all users' PCs could potentially be managed wherever they are, and when in the corporate network, they could access on-premises resources or applications seamlessly and as if they were on-premises themselves.

## What you will see and what you won't see

So, after all this philosophical introduction, how do we proceed, and what are the next steps? What will you see, and what won't you see?

We will see together how to build this type of hybrid environment from the perspective of identity and security.

We will see how to install a domain controller and some basic security elements on AD, we will see how to install and configure an Entra Connect.

We will secure identities and resources with MFA and Conditional Access.

We will join Windows devices to Entra, manage them with Intune, secure them with Microsoft Defender for Endpoint.

With these clients, we will try to access on-premises resources even though they are not on the domain.

And then... what will we see?

The answer is "I don't know" because potentially, the things to see are infinite.

But if there's something that intrigues you, if there's any configuration, any feature you're curious to see in action (considering the limitations that a lab environment may have), just leave a comment here, on Linkedin, or on Threads.

## Conclusions

I can't wait to go through this journey together and start building this lab: after this introductory chat, we will see together how to install a Domain Controller by creating a new forest, so don't miss it because we will finally start getting our hands dirty!

As always, thanks for following me this far. If you enjoyed this video and like these topics, subscribe to my YouTube channel and follow me on my blog ITSpecialist.cloud.

{{< rawhtml >}}
  <script src="https://apis.google.com/js/platform.js"></script>
  <div class="g-ytsubscribe" data-channelid="UCDNe_oC28ozt_LJ-8kWQbEA" data-layout="full" data-count="hidden"></div>
{{< /rawhtml >}}

Until next time, I'm waiting for you... LEGENDARY!
