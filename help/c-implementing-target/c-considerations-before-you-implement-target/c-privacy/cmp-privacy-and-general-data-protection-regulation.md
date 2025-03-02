---
keywords: gdpr;eu;european union;privacy;faq;frequently asked questions;california consumer privacy act;ccpa;privacy;data protection;opt-out;opt out;government;regulation
description: Learn about [!DNL Target] and the European Union General Data Protection Regulation (GDPR), the California Consumer Privacy Act (CCPA), and other privacy requirements.
title: How Does [!DNL Target] Handle Privacy and Data Protection Regulations?
feature: Privacy & Security
role: Developer
exl-id: 5013a9d2-a463-4787-90ee-3248d9cb02b2
---
# Privacy and data protection regulations

Information about the European Union's General Data Protection Regulation (GDPR), the California Consumer Privacy Act (CCPA), and other international privacy requirements. Learn how these regulations impact your organization and [!DNL Adobe Target].

## Privacy and General Data Protection Regulation (GDPR) overview {#topic_DE567ECB6C944695AEE5073889F1AEA9}

On May 25, 2018, the European Union's GDPR went into effect. For more information about what this regulation means for you, see [GDPR and Your Business](https://business.adobe.com/privacy/general-data-protection-regulation.html).

When [!DNL Adobe] is providing software and services to an enterprise, [!DNL Adobe] is acting as a Data Processor for any personal data it processes and stores as part of providing these services. As a Data Processor, [!DNL Adobe] processes personal data in accordance with your company's permission and instructions (for example, as set out in your agreement with [!DNL Adobe]).

As the Data Controller, you determine the personal data that [!DNL Adobe] processes and stores on your behalf. If you use [!DNL Adobe Experience Cloud] solutions, [!DNL Adobe] might host personal data for you, depending on the solutions you use and the information you choose to send to your [!DNL Adobe Experience Cloud] account. For a detailed list of examples, see [Adobe Experience Cloud Privacy](https://www.adobe.com/privacy/experience-cloud.html#collect).

[!DNL Adobe Experience Cloud] provides GDPR-ready APIs for Data Controllers that allow them to complete the following tasks:

* Access Data Subject information stored within [!DNL Target]
* Delete Data Subject information stored within [!DNL Target]

For more information, see:

* [Adobe General Data Protection Regulation API website](https://www.adobe.io/apis/experienceplatform/gdpr.html) 
* [GDPR Documentation](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=en)

## California Consumer Privacy Act (CCPA) overview

The California Consumer Privacy Act (CCPA) provides California consumers with new rights regarding their personal information and imposes data protection responsibilities on certain entities that conduct business in California. The CCPA went into effect January 1, 2020.

At a high level, the law affords Californians several key rights, including rights to:

* Request information (data access)
* Opt out of the sale of personal information (a broadly defined right to opt out of sharing of information with third parties)
* Have personal information deleted
* Be informed that personal information is being disclosed or sold

If you were busy getting ready for Europe’s privacy law (GDPR) last year, some of these rights might be familiar and much of the work you have done can be repurposed.

>[!NOTE]
>
>Accessing and deleting data as it applies to the CCPA follows the same process as for the GDPR.

## Adobe [!DNL Target] and [!DNL Adobe Experience Platform] opt-in {#section_6F7B53F5E40C4425934627B653E831B0}

[!DNL Target] provides opt-in functionality support via tags in [!DNL Adobe Experience Platform] to help support your consent management strategy. Opt-in functionality lets customers control how and when the [!DNL Target] tag is fired. There is also an option via [!DNL Adobe Experience Platform] to pre-approve the [!DNL Target] tag. To enable the ability to use Opt-In in the [!DNL Target] at.js library, you should use `targetGlobalSettings` and add the `optinEnabled=true` setting. In [!DNL Adobe ExperiencePlatform], select "enable" from the [!UICONTROL GDPR Opt-In] drop-down list in the extension installation view. See [Implement [!DNL Target] using [!DNL Adobe Experience Platform]](/help/c-implementing-target/c-implementing-target-for-client-side-web/how-to-deployatjs/cmp-implementing-target-using-adobe-launch.md) for more details.

The following code snippet shows you how to enable the `optinEnabled=true` setting:

```
window.targetGlobalSettings = {
  optinEnabled: true
};
```

>[!NOTE]
>
>Opt-in functionality is supported in at.js version 1.7.0 and at.js 2.1.0 or later. Opt-in is not supported in at.js version 2.0.0 and 2.0.1.
>
>Using [!DNL Adobe Experience Platform] to manage opt-in is the recommended approach. Further granular control exists in [!DNL Adobe Experience Platform] to hide selected elements of your page before [!DNL Target] firing that are helpful to use as part of your consent strategy.

There are three scenarios to consider when using Opt-In:

1. **The [!DNL Target] tag is pre-approved via [!DNL Adobe Experience Platform] (or the data subject previously approved [!DNL Target]):** The [!DNL Target] tag is not held for consent and functions as expected.
1. **The [!DNL Target] tag is NOT pre-approved and `bodyHidingEnabled` is FALSE:** The [!DNL Target] tag fires only after consent is collected from the customer. Before consent is collected, default content only is available. After consent is received, [!DNL Target] is called and personalized content is available to the data subject (visitor). Because only default content is available before consent, it is important to use an appropriate strategy, such as a splash page that covers any portion of the page or content that might be personalized. This process ensures that the experience remains consistent for the data subject (visitor).
1. **The [!DNL Target] tag is NOT pre-approved and `bodyHidingEnabled` is TRUE:** The [!DNL Target] tag fires only after consent is collected from the customer. Before consent is collected, default content only is available. However, because `bodyHidingEnabled` is set to true, `bodyHiddenStyle` dictates what content on the page is hidden until the [!DNL Target] tag is fired (or the data subject declines opt-in, in which case default content is displayed). By default, `bodyHiddenStyle` is set to `body { opacity:0;}`, which hides the HTML body tag. Adobe's recommended page configuration is below so that the entire body of the page, other than the consent manager dialog, is hidden by putting the content of the page in one container and the consent manager dialogue in a separate container. This setup configures [!DNL Target] so that it hides the page content container only. See the [Privacy Service overview](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=en).

   The recommended page setup for scenario 3 is:

   ```
   <html> 
   <head> 
   //visitor, at.js 
   </head> 
    
   <body> 
   <div id = "consentManagerDialog"> 
    
   //consent manager html dialog goes here 
   </div> 
    
   <div id="pageContent"> 
   // page content goes here 
   </div> 
    
   </body> 
   </html> 
   
   ```

   Assuming the `bodyHiddenStyle` of:

   ```
   #pageContent { opacity:0;}
   ```

## Privacy and data protection regulations FAQ {#concept_41F88DE95D2943178BEC382736B5C038}

Frequently Asked Questions about the European Union's General Data Protection Regulation (GDPR), the California Consumer Privacy Act (CCPA), and other international privacy requirements specific to [!DNL Target].

### What is the [!DNL Adobe] policy for these regulations? {#section_A6849628D6524C80A6E16946DC5D25A9}

[!DNL Adobe] either already meets or is implementing its obligations as a Data Processor. Adobe has a strong foundation of certified security and privacy controls by design and made product enhancements before the May 2018 deadline. Enterprise customers have the responsibility to implement these enhancements and update any necessary policies and procedures.

### Must my company, the Data Controller, submit a GDPR or CCPA request to each [!DNL Adobe Experience Cloud] solution that it uses? {#section_1DCFA9387D0C4506B14DCE04C49AC22A}

No, [!DNL Adobe] provides a central way to help Data Controllers meet their GDPR and CCPA requirements. Data Controllers do not need to go directly to each solution.

All GDPR and CCPA requests across [!DNL Experience Cloud] solutions, including [!DNL Target], are through a central [!DNL Adobe] API, currently called the GDPR API. The API then completes the request across the Data Controller's [!DNL Experience Cloud] solution suite.

### What information does [!DNL Adobe] enable customers to delete in response to a data subject/user request? {#section_4B51D00924EC4166B2442218B69214F0}

The information related to an individual visitor within [!DNL Target] is contained within the [!DNL Target] Visitor Profile. [!DNL Target] lets customers delete all data associated with an ID in their Visitor Profile. For examples of the profile data [!DNL Target] stores, see [Visitor Profile](/help/c-target/c-audiences/c-target-rules/visitor-profile.md#concept_E972690B9A4C4372A34229FA37EDA38E).

Aggregated or anonymized data (for example, reporting data) that does not identify a particular individual, or data that is unrelated to a specific individual (for example, content data), is outside the scope of a user-deletion request.

[!DNL Target] Visitor Profiles that have been inactive for 90 days are deleted by default, without any action required.

### What IDs are supported to help customers complete a GDPR or CCPA access and deletion request for [!DNL Target]? {#section_F7D0EE4E6A28490FB20056A0D26118BC}

[!DNL Target] supports the following ID types to locate a customer profile:

| User ID | Name Space ID Type | Namespace ID | Definition |
|--- |--- |--- |--- |
|Experience Cloud ID (ECID)|Standard|4|[!UICONTROL Adobe Experience Cloud ID], formerly known as Visitor ID or Experience Cloud ID. You can use the JavaScript API to locate this ID (see details below).|
|TnT ID / Cookie ID(TNTID)|Standard|9|[!DNL Target] identifier set as a cookie in the visitor’s browser. You can use the JavaScript API to locate this ID (see details below).|
|3rd-Party ID / CRM ID (THIRDPARTYID)|[!DNL Target]-Specific|N/A|If you provide [!DNL Target] with your CRM or other unique identifier information for your customers.|

>[!NOTE]
>
>Although [!DNL Target] supports both first-party and third-party cross-domain cookies, first-party [!DNL Target] cookies only are recommended for GDPR and CCPA.

### How does [!DNL Target] handle consent management? {#section_C86BF5EE4FAA47039659850E7594A6BA}

GDPR and CCPA do not change when you must get consent, but how you get it. Each customer's consent strategy depends on its data collection and use practices and its privacy policy. Consent management isn’t supported by and shouldn’t be achieved via [!DNL Target] for GDPR and CCPA.

[!DNL Adobe] does not currently offer a Consent Management Solution, but there are various tools developing in the market to address some of the new requirements. For more information on privacy tools in general, including consent managers, see the [2017 Privacy Tech Vendor Report](https://iapp.org/media/pdf/resource_center/Tech-Vendor-Directory-1.4.1-electronic.pdf) on the *International Association of Privacy Professionals (iaap)* website.

[!DNL Target] does provide opt-in functionality support via [!DNL Adobe Experience Platform] to support your consent management strategy. Opt-in functionality lets customers control how and when the [!DNL Target] tag is fired. There is also an option via [!DNL Adobe Experience Platform] to pre-approve the [!DNL Target] tag. Using [!DNL Adobe Experience Platform] to manage opt-in is the recommended approach. Further granular control exists in [!DNL Adobe Experience Platform] to hide select elements of your page before the [!DNL Target] firing that might be helpful to use as part of your consent strategy.

For more information on GDPR, CCPA, and [!DNL Adobe Experience Platform], see [The Adobe Privacy JavaScript Library and GDPR](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=en). Also, see the *Adobe Target and Adobe Experience Platform opt-in* section above.

### Does `AdobePrivacy.js` submit information to the GDPR API? {#section_1EB8A2BAAD31474C97C1D455F41DA739}

[!DNL AdobePrivacy.js] does *not* submit this information to the API. The customer must do that. This library provides only the IDs that are stored in the browser for that specific visitor.

### What does `removeIdentities` remove? {#section_D3A1591EA1B84C499CE1563DEAF32448}

[!DNL `removeIdentities`] *only* removes those identities from the browser, and that only depends on whether the [!DNL Adobe] solution has implemented it.

For example, [!DNL Target] deletes the cookies storing its IDs, but [!DNL Adobe Audience Manager] (AAM) does not delete the demdex ID that is stored in a third-party cookie.

### What information must be included in a [!DNL Target] GDPR or CCPA request? {#section_D29A4744AE6344E68AD7710B185FD6D0}

In addition to the requirements from Central Privacy Service, a valid GDPR or CCPA message for [!DNL Target] contains:

```
{ 
    "jobId":"12345AD43E", 
    ... 
    "products":["Target",...], 
    "companyContexts":[ 
        { 
            "namespace":"imsOrgID", 
            "value":"123456789@AdobeOrg" 
        }, 
        ... 
    ], 
    "userContexts":[ 
        { 
            "namespace":"ECID", 
            "namespaceId":4, 
            "type":"standard", 
            "value":"53792210477379708453829363835595041181" 
        } 
        And/OR: 
        { 
            "namespace":"TNTID", 
            "namespaceId":9, 
            "type":"standard", 
            "value":"1234567890" 
        } 
        And/OR: 
        { 
            "namespace":"THIRDPARTYID", 
            "type":"target", 
            "value":"thirdPartyIdName" 
        }, 
        ... 
    ] 
}
```

### What types of responses can I expect from [!DNL Target] via the GDPR API? {#section_F67263D2A72B4641A47CE36729CCAE8F}

| Request Status | [!DNL Target] Response Message | Scenario |
|--- |--- |--- |
|Processing|Processing|[!DNL Target] received the GDPR or CCPA request and is processing.|
|Complete|Not applicable - company context not applicable|The IMS ID in the GDPR or CCPA request is not mapped to any [!DNL Target] client.<br>Some companies have multiple IMS IDs. Submit the IMS ID where [!DNL Target] is provisioned.|
|Complete|Not applicable - user context not found|The ID provided in the GDPR or CCPA request for the specific visitor or data subject is not present in the [!DNL Target] profile store.<br>This result also returns if you attempt to submit a namespace ID type that is not supported by [!DNL Target] (see above for supported IDs).|
|Error|Error Message (details depend on the type of error)|Error while fetching or deleting the requested data subject profile.<br>Error while uploading to Azure for access request.|

### What response does [!DNL Target] send to the GDPR API for an access request? {#section_D96D8FBEAF9C4BDAA638215FAFE00763}

Responses to access data requests contain a summary of the [!DNL Target] profile for the visitor in question. This return is sent to the [!DNL Experience Cloud] GDPR API, which in turn sends Data Controllers a response.

A sample [!DNL Target] access API response could look like this:

```
{ 
    "jobId":"12345AD43E", 
    ... 
    "products":["Target",...], 
    "companyContexts":[ 
        { 
            "namespace":"imsOrgID", 
            "value":"123456789@AdobeOrg" 
        }, 
        ... 
    ], 
    "userContexts":[ 
        { 
            ~"namespace":"ECID", 
            "namespaceId":4, 
            "type":"standard", 
            "value":"53792210477379708453829363835595041181" 
        } 
        And/OR: 
        { 
            ~"namespace":"tntId", 
            "namespaceId":9, 
            "type":"standard", 
            "value":"1234567890" 
        } 
        And/OR: 
        { 
            "namespace":"thirdPartyId", 
            "type":"target", 
            "value":"thirdPartyIdName" 
        }, 
        ... 
    ] 
} 

```

| Field | Description |
|--- |--- |
|jobId|Indicates the GDPR or CCPA job ID from the Central GDPR API.|
|imsOrgID|Provides a unique identifier for your company.|
|namespace|Also referred to as data source. See "What IDs are supported to help customers complete a GDPR or CCPA access and deletion request for [!DNL Target]?" in this topic.|
|type|The type of ID for which you requested the GDPR or CCPA data access. [!DNL Target] accepts several ID types, some of which are standard and some of which are specific to [!DNL Target]. See "What IDs are supported to help customers complete a GDPR or CCPA access and deletion request for [!DNL Target]?" in this topic.|
|value|The ID of the namespace/data source. See "What IDs are supported to help customers complete a GDPR or CCPA access and deletion request for [!DNL Target]?" for accepted values.|
|integration code|Integration codes are friendly names for your data sources and help you track your data sources easier than using data source IDs.|

When multiple values are provided to identify profiles, each valid identifier has one profile file. One or more profile files are sent to the central GDPR Azure Blob through the GDPR Central API, in the format of [!DNL Target] Profile JSON response.

A sample [!DNL Target] Profile JSON could look like the following example:

```
{"profileAttributes": 
 
"Sample_Parameter":{"value":"Gold Loyalty Status","modifiedAt":"2018-04-11T21:44:14.000-04:00"}, 
 
"user.ReturnTimeOfDay":{"value":"44.0","modifiedAt":"2018-04-11T21:44:14.000-04:00"}, 
 
"firstSessionStart":{"value":"1523497450602","modifiedAt":"2018-04-11T21:44:10.000-04:00"}, 
 
"user.sessionCountScript":{"value":"1","modifiedAt":"2018-04-11T21:44:14.000-04:00"} 
   } 
} 

```

The following table contains description of the illustrative profile JSON fields:

| Field | Description |
|--- |--- |
|Sample_Parameter|Many pieces of information in the [!DNL Target] profile are uploaded or directly provided by the Data Controller. In this example, a parameter was uploaded into the [!DNL Target] profile using the Profile Update API. For more information, see [Methods to get Data into [!DNL Target]](/help/c-implementing-target/c-considerations-before-you-implement-target/c-methods-to-get-data-into-target/methods-to-get-data-into-target.md).|
|user.ReturnTimeOfDay|This standard field includes the time of day of a user’s most recent return visit.|
|firstSessionStart|This standard field includes the time of day the user’s first session began.|
|user.sessionCountScript|Many pieces of information in the [!DNL Target] profile are uploaded or directly provided by the Data Controller. In this example, a profile script is incrementing the number of sessions this visitor has made to the Data Controller’s site. For more information, see [Profile Script Attributes](/help/c-target/c-visitor-profile/profile-parameters.md).|

>[!NOTE]
>
>This code sample is a shortened version of a [!DNL Target] profile JSON for illustration. Many of the fields of the [!DNL Target] profile are not standard. What is returned depends on what information is in that specific visitor profile.

### Does [!DNL Target] support IP obfuscation? {#section_428907B0CD9842D9B245B38C66A53C6A}

[!DNL Target] supports IP obfuscation if you choose to use it as part of your GDPR or CCPA implementation strategy. For more information, see [Privacy](/help/c-implementing-target/c-considerations-before-you-implement-target/c-privacy/privacy.md#concept_639482A343DB4963A6144378E1D8D7F0).

### Should I do something to prevent my data from being shared or sold to third parties?

[!DNL Target] does not allow customers to share or sell data direct from [!DNL Target] to third parties, so there is no opt-out of sale for [!DNL Target].
