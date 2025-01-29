---
date: 2025-01-29T05:00:00-00:00
description: "Explore how to assign and manage Microsoft Intune policies to optimize the security and efficiency of your devices and users. Mini-guide with practical tips and best practices."
image: "01-include-exclude-user-device-groups-matrix.png"
categories: [ "Modern Work" ]
tags: [ "Microsoft Intune", "Configuration Profiles", "Policies", "Best Practices", "Guide" ]
title: "Quick Tips for Assigning Intune Policies"
url: /en/intune-policy-assignment-support-matrix
---
🚀 IT Specialists! Some best practices when assigning policies on Intune.

And save the attached image with the supportability matrix for inclusions and exclusions, printing it in a long paper format to hang on all walls. 😀

## Support matrix

![Supportability Matrix for Assigning, Including, and Excluding Microsoft Intune Configuration Profiles](01-include-exclude-user-device-groups-matrix.png)

| Scenario | Support |
|----------|---------|
| 1        | ❕ Partially supported  Assigning policies to a dynamic device group while excluding another dynamic device group is supported. But, it's not recommended in scenarios that are sensitive to latency. Any delay in exclude group membership calculation can cause policies to be offered to devices. In this scenario, we recommend using filters instead of dynamic device groups for excluding devices. For example, you have a device policy that's assigned to All devices. Later, you have a requirement that new marketing devices don't receive this policy. So, you create a dynamic device group called Marketing devices based on the enrollmentProfilename property (device.enrollmentProfileName -eq "Marketing_devices"). In the policy, you add the Marketing devices dynamic group as an excluded group. A new marketing device enrolls in Intune for the first time, and a new Microsoft Entra device object is created. The dynamic grouping process puts the device into the Marketing devices group with a possible delayed calculation. At the same time, the device enrolls into Intune, and starts receiving all applicable policies. The Intune policy can be deployed before the device is put in the exclusion group. This behavior results in an unwanted policy (or app) being deployed to the Marketing devices group. As a result, it's not recommended to use dynamic device groups for exclusions in latency sensitive scenarios. Instead, use filters. |
| 2        | ✅ Supported  Assigning a policy to a dynamic device group while excluding a static device group is supported. |
| 3        | ❌ Not supported  Assigning a policy to a dynamic device group while excluding user groups (both dynamic and static) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 4        | ❌ Not supported  Assigning a policy to a dynamic device group and excluding user groups (both dynamic and static) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 5        | ❕ Partially supported  Assigning a policy to a static device group while excluding a dynamic device group is supported. But, it's not recommended in scenarios that are sensitive to latency. Any delay in exclude group membership calculation can cause policies to be offered to devices. In this scenario, we recommend using filters instead of dynamic device groups for excluding devices. |
| 6        | ✅ Supported  Assigning a policy to a static device group and excluding a different static device group is supported. |
| 7        | ❌ Not supported  Assigning a policy to a static device group and excluding user groups (both dynamic and static) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 8        | ❌ Not supported  Assigning a policy to a static device group and excluding user groups (both dynamic and static) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 9        | ❌ Not supported  Assigning a policy to a dynamic user group and excluding device groups (both dynamic and static) isn't supported. |
| 10       | ❌ Not supported  Assigning a policy to a dynamic user group and excluding device groups (both dynamic and static) isn't supported. |
| 11       | ✅ Supported  Assigning a policy to a dynamic user group while excluding other user groups (both dynamic and static) is supported. |
| 12       | ✅ Supported  Assigning a policy to a dynamic user group while excluding other user groups (both dynamic and static) is supported. |
| 13       | ❌ Not supported  Assigning a policy to a static user group while excluding device groups (both dynamic and static) isn't supported. |
| 14       | ❌ Not supported  Assigning a policy to a static user group while excluding device groups (both dynamic and static) isn't supported. |
| 15       | ✅ Supported  Assigning a policy to a static user group while excluding other user groups (both dynamic and static) is supported. |
| 16       | ✅ Supported  Assigning a policy to a static user group while excluding other user groups (both dynamic and static) is supported. |


## Best Practices

📌 **Included or Excluded Groups**: Use these groups as a starting point for assigning policies. The Microsoft Entra group is the limiting group, so use the smallest group scope possible and filters to refine the assignment.

📌 **Static Groups**: Assigned Microsoft Entra groups can be added to Included or Excluded groups. Statically assign pre-registered devices or for ad hoc implementations.

📌 **Dynamic User Groups**: Can be added to Included or Excluded groups.

📌 **Excluded Groups**: Can contain users or devices.

📌 **Dynamic Device Groups**: Can be added to Included groups, but may have latency in population. In latency-sensitive scenarios, use filters to target specific devices and assign policies to user groups.

📌 **Latency-Sensitive Scenarios**: To assign policies to devices as soon as they register, create a filter to target the desired devices and assign the policy with this filter to user groups. Do not assign to device groups.

📌 **Userless Scenarios**: Create a filter to target the desired devices and assign the policy with the filter to the "All devices" group.

📌 **Avoid Dynamic Device Groups in Excluded Groups**: Latency in dynamic group calculation during registration can cause undesirable results, such as unwanted apps and policies being deployed before the excluded group membership is populated.

## Attached documentation
Here is the official document that inspired this post.

📖 [Assign policies in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/device-profile-assign)
