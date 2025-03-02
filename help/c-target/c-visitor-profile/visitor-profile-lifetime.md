---
keywords: Overview and Reference
description: Learn more about when a visitor profile expires in [!DNL Adobe Target].
title: What Is the Visitor Profile Lifetime and Can I Extend It?
feature: Audiences
exl-id: 70cb5e3b-ed6d-450d-8c6e-f1bfe8d26e54
---
# Visitor profile lifetime

By default, a visitor profile in [!DNL Adobe Target] expires after 14 days of inactivity for that visitor. This profile lifetime can be extended.

[Contact Client Care or your Adobe consultant](/help/cmp-resources-and-contact-information.md#reference_ACA3391A00EF467B87930A450050077C) to extend the profile lifetime at no additional cost. The lifetime can be set to as many as 90 days.

You do not need to download a new [!DNL Platform Web SDK] file or at.js file if your profile is extended beyond the default.

The expiration date is not reset for existing profiles. If a previous visitor does not return for 15 days, that profile expires. If a previous visitor returns before the original two-week profile expires, the profile is reset to the extended lifetime. All new visitor profiles are set to the extended profile lifetime.

In the following scenario, assume that one or both sites are implemented with the [!DNL Platform Web SDK]. If both sites are under one client code and a visitor visits both sites, the profile is set to the lifetime of profiles on whichever site was visited last. For example, assume Site 1 has an 84-day profile lifetime. Site 2 has a 14-day lifetime. If the visitor visits Site 1 and then Site 2, that visitor's profile expires in 14 days of inactivity. If the visitor visits Site 1 after visiting Site 2, the profile will expire in 84 days of inactivity.
