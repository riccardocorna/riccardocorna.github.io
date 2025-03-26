---
date: 2025-02-05T05:00:00-00:00
description: "Discover how to collect detailed hardware data from devices with Intune and the new Enhanced Device Hardware Inventory feature. Get reports in 24 hours!"
image: "01-enhanced-device-hardware-inventory-cover.jpg"
categories : [ "Modern Work" ]
tags: [ "Enhanced Device Hardware Inventory", "Properties Catalog", "Microsoft Intune", "Intune", "Video", "Tutorial", "Cloud Endpoint Diary" ]
title: "Intune Enhanced Device Hardware Inventory"
url: /en/intune-enhanced-device-hardware-inventory
---
IT Specialists! Hello everyone! Some clients have asked me this question more than once:

> *"With Intune, is it possible to collect properties and hardware data from devices? Maybe from multiple devices, all or a group?!"*

Until recently, it was not possible to do this natively with Intune, but from December 2024, you can! How? With a new feature called **Enhanced Device Hardware Inventory**!

## Video
You can find the entire video below, or you can continue reading the article.

{{< youtube z3S3hANsFHE >}}

## Intune Enhanced Device Hardware Inventory

### Introduction
By "hardware data," I mean, for example, the presence or absence of the TPM chip, version, or for laptops, how many charge cycles the battery has gone through. It could be data on the disk, RAM, in short, all hardware properties!

Until recently, it was not possible to do this natively with Intune, but from December 2024, you can!

Without further ado, let's see how to do it with a concrete example.
We collect information on the TPM chip of the machines: whether it is present or not on the PC, version, manufacturer, etc.

### Policy Properties Catalog
We create the policy using the brand new Properties Catalog, set it up, and assign it!

{{< youtubestartend z3S3hANsFHE 71 107 >}}

### Viewing the collected hardware inventory
Perfect, after about 24 hours from the first policy setup, we will see the results in the reports!

{{< youtubestartend z3S3hANsFHE 114 130 >}}

## Attached documentation
Here are the links to the official documentation of this feature.

📃 [Enhanced hardware inventory in Intune](https://techcommunity.microsoft.com/blog/microsoftintuneblog/enhanced-hardware-inventory-in-intune-coming-in-december/4303744)  
📃 [Properties catalog in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/properties-catalog)


## Conclusions
Now it is really much easier to collect hardware information on your machine fleet.
Clearly, there are some requirements that devices must meet in terms of operating systems and type of enrollment/management on Intune: I have left everything you need to delve deeper, below in the description!

Have you already used this feature? Do you think it will be useful? Let's talk about it together in the comments or on my social profiles!

Thanks for watching this video: I look forward to seeing you, as always, on LinkedIn, on the blog, and on this YouTube channel: subscribe!
See you soon... LEGENDS!

Your IT Specialist,  
Riccardo