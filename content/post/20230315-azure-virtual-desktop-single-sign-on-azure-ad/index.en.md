---
date: 2023-03-15T07:00:00-00:00
description: "Finally, the option to enable Single Sign-On to Azure AD has arrived on Azure Virtual Desktop. In this video, we will see how it can be done, even using a FIDO2 security key."
image: "01-azure-virtual-desktop-single-sign-on-azure-ad.png"
categories : ["Security"]
tags: [ "Azure Virtual Desktop", "Azure AD", "Video" ]
title: "Azure Virtual Desktop: Single Sign-On su Azure AD"
url: /en/azure-virtual-desktop-single-sign-on-azure-ad
---
It took me a while to make this video, but finally, here I am: Azure Virtual Desktop Single Sign-On to Azure AD.

{{< youtube O65a5bu-cJs >}}

One of the main "criticisms" always directed at AVD is the double authentication, which many consider a hassle. With Single Sign-On, the process becomes smoother, and the required authentications decrease.

Could I have just shown you the simple SSO?  
Clearly NO, so I even included a FIDO2 security key in it! 🤣

Currently, at the time of writing this post and recording this video, the feature is in preview. I hope it will be released in general availability as soon as possible because I really like it, and it already works well.

During the video, I assume the configurations of Hybrid Azure AD Join and the security key as an authentication method on my user account. If you want me to make a video on these two topics as well, let me know in the comments and subscribe to my YouTube channel so you won't miss any content 😉

Riccardo