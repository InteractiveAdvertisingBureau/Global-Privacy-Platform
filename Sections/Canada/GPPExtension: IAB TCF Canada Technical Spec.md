# GPP Extension: IAB TCF Canada Technical Specification

### About this document

The global standard [GPP](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform) defines a way how local standards can “plug-in” into the existing mechanics defined by GPP and the [GPP client side API](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md) . This document outlines the technical specification for using the IAB Transparency & Consent Framework Canada under these GPP specifications. 

## Summary

<table>
  <tr>
    <td><strong>Type</strong></td>
    <td><strong>Value</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td>GPP Section ID</td>
    <td>5</td>
    <td>The IAB TCF Canada is registered as Section ID 5 under GPP (compare GPP header section, region IDs)</td>
  </tr>
  <tr>
    <td>Client side API prefix</td>
    <td>tcfcav1</td>
    <td>The IAB TCF Canada is registered with client side API prefix “tcfcav1” in the GPP Client Side API.</td>
  </tr>
  </table>
  

## Section encoding

The IAB TCF Canada will be using the following encoding for the GPP section. If already familiar with the IAB TCF Europe encoding, you may view the detailed differences between the two on the [TCF v2 Consent String Specifications](https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#tc-string-format-canada). 

### Core segment

The core segment must always be present. It consists of the following fields:

<table>
  <tr>
    <td><strong>Field Name</strong></td>
    <td><strong>GPP Field Type</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td>Version</td>
    <td>Int(6)</td>
    <td>Version number. This value is 1.</td>
  </tr>
  <tr>
    <td>Created</td>
    <td>Datetime</td>
    <td>Epoch time format when TC String was last updated (must be updated any time a value is changed) . Must be in UTC time and rounded on a full day.</td>
  </tr>
  <tr>
    <td>LastUpdated</td>
    <td>Datetime</td>
    <td>Epoch time format when TC String was last updated (must be updated any time a value is changed). Must be in UTC time and rounded on a full day.</td>
  </tr>
  <tr>
    <td>CmpId</td>
    <td>Int(12)</td>
    <td>Consent Management Platform ID that last updated the TC String. A unique ID will be assigned to each Consent Management Platform. </td>
  </tr>
  <tr>
    <td>CmpVersion</td>
    <td>Int(12)</td>
    <td>Consent Management Platform version of the CMP that last updated this TC String. Each change to a CMP should increment their internally assigned version number as a record of which version the user gave consent and transparency was established. </td>
    </tr>
  <tr>
    <td>ConsentScreen</td>
    <td>Int(6)</td>
    <td>CMP Screen number at which consent was given for a user with the CMP that last updated this TC String . The number is a CMP internal designation and is CmpVersion specific. The number is used for identifying on which screen a user gave consent as a record. </td>
  </tr>
  <tr>
    <td>ConsentLanguage</td>
    <td>String(2)</td>
    <td>Two-letter <a href="https://en.wikipedia.org/wiki/ISO_639-1">ISO 639-1</a> language code in which the CMP UI was presented</td>
  </tr>
  <tr>
    <td>VendorListVersion</td>
    <td>Int(12)</td>
    <td>Version of the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list">GVL</a> used to create this TC String. Number corresponds to <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list">GVL</a> vendorListVersion</td>
   </tr>
  <tr>
    <td>TcfPolicyVersion</td>
    <td>Int(6)</td>
    <td>Version of policy used within <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list">GVL</a>. From the corresponding field in the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list">GVL</a> that was used for obtaining consent. A new policy version invalidates existing strings and requires CMPs to re-establish transparency and consent from users. </td>
  </tr>
  <tr>
    <td>UseNonStandardStacks</td>
    <td>Boolean</td>
    <td>1 CMP used non-IAB standard stacks during consent gathering<br></br>0 IAB standard stacks were used <br></br>Setting this to 1 means that a publisher-run CMP – that is still IAB Europe registered – is using customized Stack descriptions and not the standard stack descriptions defined in the <a href="https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/">Policies</a> (Appendix A section E). A CMP that services multiple publishers sets this value to 0. </td>
  </tr>
  <tr>
    <td>SpecialFeatureExpressConsent</td>
    <td>Bitfield(12)</td>
    <td>One bit for each Special Feature:<br></br>1 Opted in (express consent)<br></br>0 Not opted in (no express consent) <br></br>The TCF <a href="https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/">Policies</a> designates certain Features as “special” which means a CMP must afford the user a means to expressly consent to their use. These “Special Features” are published and numerically identified in the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list">Global Vendor List</a> separately from normal Features. </td>
  </tr>
  <tr>
  <td>PurposesExpressConsent</td>
  <td>Bitfield(24)</td>
  <td>One bit for each Purpose:<br></br>1 Express Consent<br></br>0 No Express Consent <br></br>The user’s consent value for each Purpose established on the legal basis of consent.<br></br>The Purposes are numerically identified and published in the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list">Global Vendor List</a>. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field. Note that purpose 1 bit is not used in TCF Canada.</td>
  </tr>
  <tr>
  <td>PurposesImpliedConsent</td>
  <td>Bitfield(24)</td>
  <td>One bit for each Purpose:<br></br>1 implied consent established<br></br>0 implied consent was NOT established or it was established but user exercised an Objection to the Purpose <br></br>The Purpose’s transparency requirements are met for each Purpose on the legal basis of implied consent and the user has not exercised an Objection to that Purpose.<br></br>By default or if the user has exercised an Objection to a Purpose, the corresponding bit for that Purpose is set to 0. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field. Note that purpose 1 bit is not used in TCF Canada.</td>
  </tr>
  <tr>
  <td>VendorExpressConsent</td>
  <td>OptimizedRange</td>
  <td>List of Vendor IDs that indicate Consent for these vendors. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int. </td>
  </tr>
  <tr>
  <td>VendorImpliedConsent</td>
  <td>OptimizedRange</td>
  <td>List of Vendor IDs for which Implied consent is established and the user did not exercise an Objection.. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int. </td>
  </tr>
  </table>
  

    

>**Note:** Fields marked with * are only included in the string encoded version of the GPP segment but will not be returned by the client side API. Instead the client side API will return an array of int with the corresponding IDs.


## Publisher Purposes Segment

The publisher purposes segment is appended to the core segment by using the “.” (dot) delimiter. The segment is optional. The segment fields are:


<table>
 <tr>
   <td><strong>Field name</strong></td>
   <td><strong>GPP Field Type</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td>SegmentType</td>
    <td>Int(3)</td>
    <td>Always set to 3.</td>
     </tr>
  <tr>
    <td>PubPurposesExpressConsent</td>
    <td>Bitfield(24)</td>
    <td>One bit for each Purpose:<br></br>1 Express Consent<br></br>0 No Express Consent</td>
   </tr>
  <tr>
    <td>PubPurposesImpliedConsent </td>
    <td>Bitfield(24)</td>
    <td>One bit for each Purpose:<br></br>1 implied consent established<br></br>0 implied consent was NOT established or it was established but user exercised an Objection to the Purpose </td>
     </tr>
  <tr>
    <td>NumCustomPurposes</td>
    <td>Int(6)</td>
    <td>The number of Custom Purposes.</td> 
   </tr>
  <tr>
    <td>CustomPurposesExpressConsent</td>
  <td>Bitfield(NumCustomPurposes)</td>
    <td>One bit for each Custom Purpose:<br></br>1 Express Consent<br></br>0 No Express Consent</td>
     </tr>
  <tr>
    <td>CustomPurposesImpliedConsent </td>
    <td>Bitfield(NumCustomPurposes)</td>
    <td>One bit for each Custom Purpose:<br></br>1 implied consent established<br></br>0 implied consent was NOT established or it was established but user exercised an Objection to the Custom Purpose</td>
  </tr>
  </table>


## Client side API

### Key Names

In the mobile or CTV context, the key names to be used in GPP are listed below. 


<table>
  <tr>
    <td><strong>GPP Key Name</strong></td>
    <td><strong>Value(s)</storng></td>
  </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_CmpSdkID</code></td>
    <td><code>Number:</code>The unsigned integer ID of CMP SDK</td>
     </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_CmpSdkVersion</code></td>
    <td><code>Number:</code>The unsigned integer version number of CMP SDK</td>
    </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_PolicyVersion</code></td>
    <td><code>Number:</code>The unsigned integer representing the version of the TCF that these consents adhere to.</td>
     </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_UseNonStandardStacks</code></td>
    <td><code>Number:</code>
      <ul>
        <li><code>1</code>CMP used a non-standard stack</li>
        <li><code>0</code>CMP did not use a non-standard stack</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><code>IABGPP_5_TCString</code></td>
    <td><code>String:</code>Full encoded TC string</td>
    </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_VendorExpressConsents</code></td>
    <td><code>Binary String: </code>The <code>'0'</code> or <code>'1'</code> at position n – where n's indexing begins at <code>0</code> – indicates the consent status for Vendor ID n+1; <code>false</code> and <code>true</code> respectively. eg. <code>'1'</code> at index <code>0</code> is consent <code>true</code> for vendor ID <code>1</code></td>
     </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_VendorImpliedConsents</code></td>
    <td><code>Binary String:</code> The <code>'0'</code> or <code>'1'</code> at position n – where n's indexing begins at <code>0</code> – indicates the legitimate interest status for Vendor ID n+1; <code>false</code> and <code>true</code> respectively. eg. <code>'1'</code> at index 0 is legitimate interest established <code>true</code> for vendor ID <code>1</code></td>
    </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_SpecialFeaturesExpressConsents</code></td>
    <td><code>Binary String:</code>The <code>'0'</code> or <code>'1'</code> at position n – where n's indexing begins at <code>0</code> – indicates the opt-in status for special feature ID n+1; <code>false</code> and <code>true</code> respectively. eg. <code>'1'</code> at index <code>0</code> is opt-in <code>true</code> for special feature ID <code>1</code></td>
     </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_PublisherExpressConsent</code></td>
    <td><code>Binary String:</code>The <code>'0'</code> or <code>'1'</code> at position n – where n's indexing begins at <code>0</code> – indicates the purpose consent status for purpose ID n+1 for the publisher as they correspond to the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md#what-is-the-global-vendor-list">Global Vendor List</a>; <code>false</code> and <code>true</code> respectively. eg. <code>'1'</code> at index <code>0</code> is consent <code>true</code> for purpose ID <code>1</code></td>
  </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_PublisherImpliedConsent</code></td>
    <td><code>Binary String: </code>The <code>'0'</code> or <code>'1'</code> at position n – where n's indexing begins at <code>0</code> – indicates the purpose legitimate interest status for purpose ID n+1 for the publisher as they correspond to the Global Vendor List Purposes; <code>false</code> and <code>true</code> respectively. eg. <code>'1'</code> at index <code>0</code> is legitimate interest established <code>true</code> for purpose ID<code>1</code></td>
     </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_PublisherCustomPurposesExpressConsents</code></td>
    <td><code>Binary String:</code> The <code>'0'</code> or <code>'1'</code> at position n – where n's indexing begins at <code>0</code> – indicates purpose consent status for the publisher's custom purpose ID n+1 for the publisher; <code>false</code> and <code>true</code> respectively. eg. <code>'1'</code> at index <code>0</code> is consent <code>true</code> for custom purpose ID <code>1</code></td>
    </tr>
  <tr>
    <td><code>IABGPP_TCFCA1_PublisherCustomPurposesImpliedConsents</code></td>
    <td><code>Binary String:</code>The <code>'0'</code> or <code>'1'</code> at position n – where n's indexing begins at <code>0</code> – indicates the purpose legitimate interest status for the publisher's custom purpose ID n+1 for the publisher; <code>false</code> and <code>true</code> respectively. eg. <code>'1'</code> at index <code>0</code> is legitimate interest established <code>true</code> for custom purpose ID <code>1</code></td>
     </tr>
  </table>
  
  


## Summary of differences when compared with TCF EU

- References to "consent" should be read as "express consent"
- References to "legitimate interest" should be read as "implied consent"
- References to "special feature opt ins" should be read as "special feature express consent"
- References to a "Right to Object" should be read as a user exercising an "Objection"

