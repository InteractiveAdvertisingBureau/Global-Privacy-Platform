Global Privacy Platform (GPP) Implementation Guidelines
=======================================================

This document provides technical implementation guidelines related to the Global Privacy Platform (GPP) specifications. The IAB Tech Lab Global Privacy Working Group developed the guidelines to support industry adoption of the GPP. The intended audience for this document includes product and engineering teams building technology based on the specifications who are looking for implementation guidance.

## Table of Contents

#### [1. Introduction to the Global Privacy Platform](#1-introduction-to-the-global-privacy-platform)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Getting Started](#11-getting-started)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Glossary of Terms](#12-glossary-of-terms)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[1.3 Core GPP Specifications](#13-core-gpp-specifications)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[1.4 Section Specifictions - Understanding Sections and Sub-sections](#14-section-specifications---understanding-sections-and-sub-sections)<br>

#### [2. Publisher/Advertiser (Digital Property Owners) Guidelines](#2-publisheradvertiser-digital-property-owners-guidelines)
&nbsp;&nbsp;&nbsp;&nbsp;[2.1 About Consent Management Platforms (CMPs)](#21-about-consent-management-platforms-cmps)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[2.2 Deciding Which Sections to Support](#22-deciding-which-sections-to-support)<br>

#### [3. CMP Guidelines](#3-cmp-guidelines)
&nbsp;&nbsp;&nbsp;&nbsp;[3.1 CMP IDs](#31-cmp-ids)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.2 Presentation of User Choices](#32-presentation-of-user-choices)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.3 Supported APIs](#33-supported-apis)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.4 Applicable Section(s)](#34-applicable-sections)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.5 Encoding the GPP String](#35-encoding-the-gpp-string)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[3.6 API Lifecycle: Managing “opt in” vs. “opt out” Frameworks](#36-api-lifecycle-managing-opt-in-vs-opt-out-frameworks)<br>

#### [4. Vendor Guidelines](#4-vendor-guidelines)
&nbsp;&nbsp;&nbsp;&nbsp;[4.1 Vendor IDs](#41-vendor-ids)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[4.2 Finding a GPP String](#42-finding-a-gpp-string)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[4.3 Decoding a GPP String](#43-decoding-the-gpp-string)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[4.4 Sending a GPP String](#44-sending-a-gpp-string)<br>

#### [5. FAQs](#5-faqs)
&nbsp;&nbsp;&nbsp;&nbsp;[Where can I find section-specific implementation guidelines?](#where-can-i-find-section-specific-implementation-guidelines)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[What’s the difference between a GPP ID, TCF Vendor ID, and an MSPA Signatory ID?](#whats-the-difference-between-a-gpp-id-tcf-vendor-id-and-an-mspa-signatory-id)<br>
&nbsp;&nbsp;&nbsp;&nbsp;[How can I submit my questions?](#how-can-i-submit-my-questions)<br>

#### [6. Implementation Resources](#6-implementation-resources)

## 1. Introduction to the Global Privacy Platform <a name="1"></a>

The IAB Tech Lab Global Privacy Platform (GPP) was developed to help ecosystem participants support user choice and comply with consumer privacy regulations across diverse regulatory regimes. With increasing numbers of data privacy laws being adopted across the globe, including the GDPR in Europe, PIPEDA in Canada, and multiple US state laws, efforts to maintain compliance were becoming dramatically more complex, cumbersome and fragmented. In response, the Tech Lab’s Global Privacy Working Group developed the GPP, a unified standard for communicating user consent and data preferences efficiently and consistently across diverse legal environments.

The GPP aims to maximize interoperability in this complex environment by simplifying and harmonizing user preference communication, making it easier for all parties in the digital advertising supply chain to comply with regional privacy regulations and easier for users to understand their options and to express and manage preferences. The platform accomplishes this by defining a transport layer which standardizes preference encoding and communication and by providing a common set of well defined signals so all participants have a consistent, partnership agnostic understanding of the user preferences.

The IAB Tech Lab Global Privacy Working Group is responsible for the development of the GPP. As of this writing it has added support for the following privacy strings: the [IAB Europe TCF](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/EEA), the [IAB Canada TCF](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/Canada), the MSPA’s [US National string](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/US-National), and a number of [US state-specific privacy strings](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/US-States). The Global Privacy Platform will continue to be expanded to support additional jurisdictions with data privacy regulations. For the most up-to-date information on supported privacy strings, see [Section Information](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md) in the Global Privacy Platform [github repository](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main).

### 1.1 Getting Started <a name="1.1"></a>

Before adopting and implementing the IAB Global Privacy Platform (GPP) standard, a company should consider the following:

1.  **Regulatory Requirements**: You must start with your compliance team or legal counsel and ensure that the GPP standard aligns with the privacy regulations applicable to your business and to verify the platform supports the jurisdictions your company operates in.
    
2.  **Legal and Compliance Review**: Conduct a thorough legal review to ensure that adopting GPP aligns with your privacy policies and terms of service. This includes verifying that the GPP implementation meets the requirements of all relevant data protection laws.
    
3.  **User Experience**: Determine if implementing GPP will impact the user experience on your platform and if so, how. Consider how consent choices will be presented to users, how users will define and manage their preferences and how changes affecting users will be communicated.
    
4.  **Vendor and Partner Compatibility**: Ensure that your partners, including advertising networks, data processors, and other third-party vendors, are also compatible with GPP. Coordination with these partners is crucial for maintaining compliance across the data supply chain.
    
5.  **Technical Integration**: Assess the technical requirements for integrating GPP with your existing systems. This includes understanding how GPP handles consent strings, how it interfaces with your content management systems (CMS), ad servers, or other third-party services, and whether your infrastructure can support these integrations.
    
6.  **Data Management**: Review GPP user consent data handling and ensure that your data processing practices are compatible with the framework. This includes understanding the logging, storage, retrieval, and updating of consent preferences and ensuring that the process is secure and compliant.
    
7.  **Staff Training**: Prepare your teams by providing training on your regulatory compliance program and how to implement and manage GPP to support it. This includes compliance teams responsible for monitoring and reporting and product and technical teams responsible for implementation and partner integration.
    
8.  **Ongoing Maintenance and Updates**: Determine how your organization will manage the process of keeping your GPP implementation up to date as support for new regulations is added and support for existing ones change. This requires a commitment to keeping abreast of updates to the platform, understanding if and how changes impact your implementation and regularly updating your implementation to ensure continuous compliance.
    
9.  **Cost and Resources**: Consider the cost of implementing and maintaining GPP, including:
    
    1.  Resource allocations for the initial build
        
    2.  Ongoing operational costs for testing, monitoring and updates.
        
    3.  The cost of developing and maintaining integrations with existing and future partners and service providers
        
    4.  Resources required for ongoing monitoring of compliance with new and updated regulations.
        
10.  **Testing and Monitoring**: Plan for system and end-to-end testing during deployment to ensure the GPP implementation works as expected and that you have sufficient monitoring in place. After deployment, establish monitoring processes and regular reviews and testing to ensure continued compliance and proper functioning of your implementation.
    

By considering these factors, a company can effectively implement the Global Privacy Platform standard to aid in complying with global privacy regulations.

### 1.2 Glossary of Terms <a name="1.2"></a>
<table><tbody>
  <tr>
            <td colspan="1" rowspan="1">
                <p><strong>Term</strong>
                </p>
            </td>
            <td colspan="1" rowspan="1">
                <p><strong>Definition</strong>
                </p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Advertiser</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>A company, or advertising agency representing an Advertiser, that (i) owns advertisements for placement in inventory on Publisher’s websites or other media properties, and/or (ii) interacts with consumers on its Digital Properties or through its advertisements.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Consent Management Platform (CMP)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>A company or organization that acts as an intermediary between a Publisher, an end user, and Vendors to (i) provide transparency, (ii) help Vendors and Publishers establish legal bases for processing (where needed), (iii) acquire user consent as needed, as well as manage user opt outs, and (iv) communicate these to the ecosystem.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Digital Property</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>A web page, mobile site, video digital property, video player, application, or retailer page.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Digital Property Owners</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Any party that identifies as a Publisher or Advertiser in the digital supply chain who maintains control of a Digital Property.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>GPP String</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>A string of characters used to represent a user’s choices.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Multi-State Privacy Agreement (MSPA)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>A common contractual framework for Advertisers, Vendors, and Publishers for implementing U.S. state privacy laws that functions as a “springing contract”that creates a contractual relationship amongst signatories as personal information flows between them for purposes of delivering a digital ad.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Section</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>In the context of the GPP String, a Section is the technical encoded representation of the choices/signals for a specific framework. Frameworks usually represent a specific jurisdiction.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Subsection</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>In the context of the GPP String, a Subsection is a logical part of a section used to separate information within this section.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Vendor</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>A company that participates in the delivery of digital advertising or other online activities within a Digital Property, to the extent that company is not acting as a Publisher, Advertiser or CMP.</p>
            </td>
        </tr>
</tbody></table>


### 1.3 Core GPP specifications <a name="1.3"></a>

In the GPP Github repository, there is a Core folder that contains the two specifications that make up the core of the platform: the [GPP API Specification](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md) and the [GPP String Specification](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md).

The GPP API Specification describes the Consent Management Platform (CMP) API, which is the mechanism web pages and apps use to interact with CMPs, including how providers of the API must implement it and what callers of the API can expect.

The GPP String Specification defines what a GPP string looks like and includes the details for the GPP header section. It also provides the primitive data types that may be used in any section specification.

The header section is always required and always comes first. The purpose of the header is to identify which sections are included in a string payload and be a table of contents of where to find each signal in the string payload (broken into discrete sections).

### 1.4 Section Specifications - Understanding sections and sub-sections <a name="1.4"></a>

A section in the GPP represents a unique privacy signal and generally corresponds to a unique jurisdiction. As such, only one section should be sent in a given string, understanding that an individual is typically afforded rights under a single jurisdiction. However, you may encounter multiple sections identified within the Section ID (gpp\_sid).

Today, acceptable use is to allow up to two (2) applicable section IDs to be signaled. See CMP Guidelines, [3.4 Applicable Section(s)](#34-applicable-sections), for more details.

#### 1.4.1 What is the difference between sections and sub-sections? <a name="1.4.1"></a>

Sections indicate a user’s preferences according to the jurisdiction that the section represents. A high level explanation of sections are provided here for reference.

*   The **EEA/UK section** contains data that, when decoded, produces a TC String that is compatible with the TCF specification. See the Transparency and Consent Framework Specification and Implementation Guidelines for more information.
    

Important Note:  
The standalone TC string will continue to be used by many digital property owners until it is deprecated by IAB Europe. Until then, the TC string must be included in your transaction headers, the TCF API must be implemented on your page, and vendors are required to look for and interpret the TC string for all transactions where GDPR is applicable.

*   The **US Privacy section** is deprecated and should not be used. US privacy signals are provided in the MSPA/US National and US State specific sections**.**
    

*   The **MSPA/US National section** provides a way for MSPA signatories and Certified Partners to meet the highest common denominator of state privacy law requirements and are used in place of specific state strings. The signals in the MSPA/US National Section can be evaluated for required compliance in light of the MSPA. See the MSPA text and Implementation Guidelines for more information.
    

*   The **US State Specific sections** provide a way to meet state privacy law requirements. They have been developed to comply with the relevant state privacy laws. The signals in each section, when decoded, can be evaluated for compliance in light of the relevant state laws.
    

Every string consists of at least one section, but each section may contain multiple sub-sections. Sub-sections are used to indicate values representing bespoke requirements under various laws and regulations. For example, while US state privacy laws typically allow for processing unless an opt-out signal has been received, there are different levels of consent required for processing sensitive personal information or children’s data. Sub-sections allow for these nuances to be captured within the consent string.

#### 1.4.2 How new section specifications are added <a name="1.4.2"></a>

The Global Privacy Working Group is responsible for authoring technical specifications for new sections when there is a need to communicate user preferences relevant to specific markets.

Upcoming additions include new sections for U.S. states that have enacted comprehensive data privacy laws, as well as a section designed to help organizations comply with India's Digital Personal Data Protection Act (DPDPA).

## 2. Publisher/Advertiser (Digital Property Owners) Guidelines <a name="2"></a>
This section details the overall guidelines that digital property owners should typically follow when implementing the GPP.

### 2.1 About Consent Management Platforms (CMPs) <a name="2.1"></a>

A Consent Management Platform (CMP) is used to manage transparency and consent preferences signaled by the end user. The CMP captures and manages the transparency and consent information from a user. The CMP also surfaces this information to vendor technologies operating as part of the publisher’s digital property and supply chain. The CMP acts as an intermediary between the publisher, end user, and vendors.

The publisher may implement a CMP in two ways:

1.  **Build**: Develop an in-house CMP
    
2.  **Outsource**: Rely on the service of a commercial CMP
    

Regardless of the choice to build or outsource the CMP, Publishers should be aware of the sections in the GPP that include additional CMP requirements such as registration. Publishers who choose to develop an in-house CMP should also refer to the [CMP Guidelines](#3-cmp-guidelines) section of these guidelines.

### 2.2 Deciding which sections to support <a name="2.2"></a>

Publishers may operate in one or multiple jurisdictions where there is a need to provide their users with transparency and choice. The GPP includes support for multiple jurisdictions including the EU, Canada, and multiple US states. For the most up-to-date list of jurisdictions that the GPP supports, see the [Section Information](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md) portion of the specification.

Publishers should consult their business and legal teams to determine which sections of the GPP they should support. They should also consult their CMPs (if using a commercial CMP) to determine which sections the CMP is ready to support. Last, publishers should work with their vendor partners to understand which sections their partners are ready to support.

## 3. CMP Guidelines <a name="3"></a>

This section details the overall guidelines that consent management platforms should follow when implementing the GPP.

CMPs are responsible for collecting consent from the end user and communicating that consent to vendors.

As a GPP CMP, you will need to:

*   Establish legal bases for processing personal data with your end users, complying with the requirements, technical specifications, and policies of the individual privacy strings (GPP sections) you support.
    
*   Generate an encoded data string, the GPP String, containing the encoded choices or settings for the individual sections for which you have established legal bases.
    
*   Share the GPP String with vendors through the defined GPP API.
    

### 3.1 CMP IDs <a name="3.1"></a>

Certain section frameworks supported in the GPP, such as [IAB Europe’s Transparency and Consent Framework (TCF)](https://iabeurope.eu/transparency-consent-framework/) and [IAB Canada’s Transparency and Consent Framework (TCF)](https://iabcanada.com/tcf-canada/), require a CMP ID. This is an ID assigned by the IAB Europe following registration and certification; if you register as a CMP for multiple of these frameworks, your IAB CMP ID will be the same for all frameworks. Not all individual privacy sections require a CMP ID.

The [PingReturn](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-) object defined in the GPP API contains a `cmpId` field. If you support a section that requires a CMP ID, you should always provide your ID in that field (field may be set to 0 during your stub/loading phase). If you do not have an assigned CMP ID due to not supporting sections that require one, you should set the field to 1.

### 3.2 Presentation of user choices <a name="3.2"></a>

One of the core responsibilities of a CMP is to surface consent choices to the end user within the publisher’s site, mobile, or CTV application.

As the IAB GPP supports many individual section frameworks, you will likely need to develop different user interfaces to establish legal bases under different frameworks. As a CMP, you are responsible for complying with the technical specifications and policies set by each privacy framework that your CMP supports. This may further require IAB certification.

Note that these user interfaces may be surfaced in different ways; some frameworks may require that the user is automatically presented with a blocking interface upon visiting the site or app, whereas others may be triggered by the user clicking a link embedded in the site or app.

### 3.3 Supported APIs <a name="3.3"></a>

As a CMP that supports the GPP, you are not required to implement all supported sections. To indicate to callers which sections of the GPP that you support, use the `supportedAPIs` field in the [PingReturn](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-) object. This can be set statically to the list of all sections (string formatted as \<section prefix>:\<section ID>) that your CMP supports. Use the `applicableSections` field in the `PingReturn` object to dynamically indicate the specific section(s) that apply to a given user.

Note that the `applicableSections` list is separate from the [range-encoded Sections list](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#header-encoding) in the GPP string header itself; the GPP header Sections list should contain only the list of section IDs that correspond to the sections present in the latter part of the GPP string.

### 3.4 Applicable section(s) <a name="3.4"></a>

The GPP string can be thought of as a list of all individual privacy strings collected from the end user. As a CMP, you are responsible for helping vendors interpret this string and determine which section string(s) applies to this request. You will indicate this through the `applicableSections` field in the [PingReturn](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-) object.

This field should be set only to the individual section IDs that you have determined are applicable to this request; it should not be set to the list of all sections that you support as a CMP. If you have determined that no section applies, set \[-1\]. This is typically determined primarily by the end user’s geolocation, although CMPs may use other factors at their discretion in conjunction with your legal and business teams. For example, if you support both the MSPA US National section as well as a state section also supported by MSPA US National, you can determine which section between the two actually applies and should be read by vendors.

Note that you can set up to 2 applicable section IDs in the field. Previously the specification allowed up to 3 to accommodate the now-deprecated US Privacy section, but this is no longer allowed. In the above example where multiple frameworks apply, you may choose to signal both as applicable or select a single section.

### 3.5 Encoding the GPP string <a name="3.5"></a>

The GPP string consists of a tilde-concatenated (~) list of consent sections that you have collected for a given user. It begins with a “header” that provides metadata about the remaining contents of the string, followed by individual section strings.

Instructions for encoding the header section and general encoding formats used by many of the individual sections can be found in the GPP [Consent String Specification](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#creating-a-gpp-string). Note that while the recommended encoding format uses the base64 alphabet, the encoding is only “base64-like” and it uses a different grouping and padding format. More details can be found in the Consent String Specification.

Example headers that demonstrate the expected grouping, padding and encoding patterns can be found in the specification. To manually test the decoding of your encoded strings, you can use the decoder at [iabgpp.com](http://iabgpp.com).

### 3.6 API lifecycle: Managing “opt in” vs. “opt out” frameworks <a name="3.6"></a>

The GPP supports multiple styles of frameworks. Some, like TCF, are considered to be “opt in” where the user must make a selection prior to proceeding in the site or app, whereas others, like MSPA US National, are considered to be “opt out”, where the user triggers the consent layer through an embedded link on the site or app.

See the [PingReturn](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-) section and status codes for more on how to signal various lifecycle events for different framework types. Some key fields are:

*   `signalStatus`: This indicates that the GPP string is ready to be consumed by vendors. Note that for an “opt out”-style framework, this field may immediately be set to `ready`, as long as an initial string for the applicable section has been generated (or if there is no applicable section).
    
*   `cmpDisplayStatus`: This indicates the visibility of the applicable UI. Note that for frameworks that do not have a blocking display layer (e.g. where a user triggers the consent dialog via a “Do not sell or share” link), this value should always be null; callers will rely on the `signalStatus` field to determine if the GPP string is ready for consumption.
    

## 4. Vendor Guidelines <a name="4"></a>

Today’s global environment requires Vendors to uphold their own compliance obligations as well as to support their partners in their compliance efforts. The GPP provides Vendors with a technical mechanism to understand where processing is allowed and where processing may be restricted under applicable privacy laws and regulations.

Vendors use the GPP in order to

*   Understand user consent and data preferences and, the compliance posture of Publishers sharing personal data; and
    
*   Support the Vendor’s compliance posture.
    

Vendor roles include:

*   Supply Side Platforms (SSPs)
    
*   Demand Side Platforms (DSPs)
    
*   Measurement Providers
    
*   Data Management Platforms (DMPs)
    

### 4.1 Vendor IDs <a name="4.1"></a>

Vendor IDs are unique identifiers assigned to companies participating in the [IAB Europe’s Transparency and Consent Framework (TCF)](https://iabeurope.eu/transparency-consent-framework/) for GDPR and ePrivacy compliance, [IAB Canada’s Transparency and Consent Framework (TCF)](https://iabcanada.com/tcf-canada/) for PIPEDA and Quebec’s Law 25 compliance, or [IAB’s Multi-State Privacy Agreement (MSPA)](https://www.iabprivacy.com/#) for compliance with US state privacy regulations.

Each participating vendor is assigned a Vendor ID by the IAB upon registration for TCF Europe, TCF Canada, or when becoming a signatory to the MSPA. Note that not all sections necessarily require registration; however, when registration is required, the Vendor ID is consistent across all frameworks.

#### How Vendor IDs Are Used

*   Vendors can decode the GPP string to determine:
    
    *   Whether they have permission to process user data.
        
    *   What purposes they can process data for (e.g., ad targeting, measurement).
        
*   Vendors that are not included in the GPP string are required to respect the lack of consent and avoid processing personal data.
    

### 4.2 Finding a GPP String <a name="4.2"></a>

GPP strings are created by CMPs and can be found through a CMP API call, through the OpenRTB Regs object (when you don’t have access to the browser), or by reading the URL parameters (where JavaScript cannot be executed).

_CMP API call_

When GPP is received client side (e.g., any code snippet deployed directly on the browser, such as JavaScript), the GPP CMP API should be used to access the encoded string. This information can be collected whether you are in the top parent page (using the \_\_gpp method) or from an iframe (using postMessage method as defined by the CMP API technical specifications). Use a callback function passed to the event listener API (addEventListener) to retrieve the most up to date PingReturn object.

_OpenRTB Regs Object_

If GPP is received server side (e.g., OpenRTB), you should read the encoded string from the Regs object. For other non-standard server side delivery, clarify with your partner(s) on how the encoded string is passed.

If OpenRTB is not supported (for example, for cookie syncs), the GPP string will be found in the URL parameters. Vendors are encouraged to follow the IAB recommendations for macro names. The GPP Consent String Specification allows for URL-based service processes to receive a string through a set of macros designed to pass the encoded string via URL.

### 4.3 Decoding the GPP String <a name="4.3"></a>

The GPP string runs the risk of causing errors due to string length so that Fibonacci encoding is used to shorten the string length. As a result, you will need to either develop your own decoder or use the IAB provided decoder in order to read the values of the string. Refer to the GPP Consent String Specification for more guidance on decoding the GPP string.

_Fibonacci Encoding_

It will be important to read the IAB technical specification for decoding the string. Reference [Section 6. Implementation Resources](#6-implementation-resources) for links to IAB documentation.

### 4.4 Sending a GPP String <a name="4.4"></a>

For any server-side call, if using openRTB, the consent payload should be sent according to the [openRTB specs](https://github.com/InteractiveAdvertisingBureau/openrtb2.x/blob/main/2.6.md#objectregs).

For any client-side call, once the consent payload has been obtained leveraging the CMP JS API, you can validate that it reflects user-intentful consent by checking the status of certain fields. For example:

*   the field cmpStatus is loaded, and
    

*   the field signalStatus is ready
    

The status of these two fields as indicated above show that the CMP has been loaded and that the GPP string is ready to be consumed. After validating the PingReturn payload is suitable for your case, you should pass the GPP string in the ad call using the URL-passing macro solution detailed in documentation for the GPP String.

## 5. FAQs <a name="5"></a>

### Where can I find section-specific implementation guidelines? <a name="FAQ1"></a>

*   [TCF Europe and Canada Section Implementation Guidelines](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md#whatiscmp)
    
*   [MSPA Technical Signaling Implementation Guidelines](https://www.iabprivacy.com/IAB%20MSPA%20Technical%20Signaling%20Implementation%20Guidelines%20v1.3%201.26.24.pdf) - Note that these guidelines are for MSPA signatories
    

### What’s the difference between a GPP ID, TCF Vendor ID, and an MSPA Signatory ID? <a name="FAQ2"></a>

The GPP ID, TCF Vendor ID, and MSPA Signatory ID refer to the same identifier assigned to vendors participating in different frameworks. When a vendor registers for any of these frameworks, they will always have a GPP ID. This ensures that implementers do not need to maintain separate vendor IDs across multiple frameworks.

It's important to note that vendors must register for each specific framework they wish to participate in. Registration in one framework does not automatically mean they are registered in others. Failure to register for all appropriate frameworks will result in vendors not being included in Global Vendor Lists (GVLs) or signatory lists.

### How can I submit my questions? <a name="FAQ3"></a>

You can submit your questions regarding the GPP to [support@iabtechlab.com](mailto:support@iabtechlab.com).

## 6. Implementation Resources <a name="6"></a>

Below are implementation resources developed and maintained by the Global Privacy Working Group

*   [JS Library](https://github.com/IABTechLab/iabgpp-es)
    
*   [Java Library](https://github.com/IABTechLab/iabgpp-java)
    
*   [Encoder/Decoder Tool](https://iabgpp.com/) (GPP String Debugging Tool)
