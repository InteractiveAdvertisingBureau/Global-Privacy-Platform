# IAB TCF Europe Technical Specification

## About this document

The global standard [GPP](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform) defines a way how local standards can “plug-in” into the existing mechanics defined by GPP and the [GPP client side API](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md). This document outlines the technical specification for using the IAB Europe Transparency & Consent Framework under these GPP specifications. 

## Summary

<table>
  <tr>
    <td><strong>Type</strong></td>
    <td><strong>Value</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td>GPP Section ID</td>
    <td>2</td>
    <td>The IAB TCF Europe is registered as Section ID 2 under the GPP.</td>
  </tr>
  <tr>
    <td>Client side API prefix</td>
    <td>tcfeuv2</td>
    <td>The IAB TCF Europe is registered with client side API prefix <code>"tcfeuv2"</code> in the GPP Client Side API.</td>
  </tr>
  </table>
  


## Section encoding

The GPP section for the IAB Europe TCF (Section ID 2) will use the following encoding.
Note that the resulting TC String produced is expected to be exactly the same as the TC String produced when using the [TCF specification](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md). The GPP introduces new data types that are For full details about the TC String, please refer to the [Consent string and vendor list format v2](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md).


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
    <td>Version number. This value is 2.</td>
  </tr>
  <tr>
    <td>Created</td>
    <td>Datetime</td>
    <td>Epoch time format when TC String was last updated (must be updated any time a value is changed). Must be in UTC time and rounded on a full day.</td>
  </tr>
  <tr>
    <td>LastUpdated</td>
    <td>Datetime</td>
    <td>Epoch time format when TC String was last updated (must be updated any time a value is changed). Must be in UTC time and rounded on a full day.</td>
  </tr>
  <tr>
    <td>CmpId</td>
    <td>Int(12)</td>
    <td>Consent Management Platform ID that last updated the TC String. A unique ID will be assigned to each Consent Management Platform.</td>
  </tr>
  <tr>
    <td>CmpVersion</td>
    <td>Int(12)</td>
    <td>Consent Management Platform version of the CMP that last updated this TC String. Each change to a CMP should increment their internally assigned version number as a record of which version the user gave consent to and transparency was established.</td>
  </tr>
  <tr>
    <td>ConsentScreen</td>
    <td>Int(6)</td>
    <td>CMP Screen number at which consent was given for a user with the CMP that last updated this TC String. The number is a CMP internal designation and is CmpVersion specific. The number is used for identifying on which screen a user gave consent as a record.</td>
  </tr>
  <tr>
    <td>ConsentLanguage</td>
    <td>String(2)</td>
    <td>Two-letter ISO 639-1 language code in which the CMP UI was presented</td>
  </tr>
  <tr>
    <td>VendorListVersion</td>
    <td>Int(12)</td>
    <td>Version of the GVL used to create this TC String. Number corresponds to GVL vendorListVersion</td>
  </tr>
  <tr>
    <td>TcfPolicyVersion</td>
    <td>Int(6)</td>
    <td>Version of policy used within GVL. From the corresponding field in the GVL that was used for obtaining consent. A new policy version invalidates existing strings and requires CMPs to re-establish transparency and consent from users.</td>
  </tr>
  <tr>
    <td>IsServiceSpecific</td>
    <td>Boolean</td>
    <td>1 true<br><br>0 false<br><br>This field must always have the value of 1. When a Vendor encounters a TC String with IsServiceSpecific=0 then it is considered invalid.</td>
  </tr>
  <tr>
  <td>UseNonStandardStacks</td>
  <td>Boolean</td>
  <td>1 CMP used non-IAB standard stacks during consent gathering<br><br>0 IAB standard stacks were used<br><br> Setting this to 1 means that a publisher-run CMP – that is still IAB Europe registered – is using customized Stack descriptions and not the standard stack descriptions defined in the <a href="https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/">Policies</a> (Appendix A section E). A CMP that services multiple publishers sets this value to 0.</td>
  </tr>
  <tr>
    <td>SpecialFeatureOptIns</td>
    <td>Bitfield(12)</td>
    <td>One bit for each Special Feature:
    <ul>
      <li>1 Opten in</li>
      <li>0 Not opted in</li>
    </ul>
   The TCF <a href="https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/">Policies </a> designates certain Features as “special” which means a CMP must afford the user a means to expressly consent to their use. These “Special Features” are published and numerically identified in the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list">Global Vendor List </a> separately from normal Features.</td>
   </tr>
   <tr>
  <td>PurposeConsent</td>
  <td>Bitfield(24)</td>
  <td>One bit for each Purpose:
    <ul>
      <li>1 Consent</li>
      <li>0 Consent</li>
    </ul>
    The user’s consent value for each Purpose established on the legal basis of consent.<br><br>  <br><br>The Purposes are numerically identified and published in the Global Vendor List. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field.</td>
  </tr>
  <tr>
  <td>PurposesLITransparency</td>
  <td>Bitfield(24)</td>
  <td>One bit for each Purpose:
    <ul>
      <li>1 legitimate interest estalished</li>
      <li>0 legitimate interest was NOT established or it was established but user exercised their “Right to Object” to the Purpose</li>
    </ul>
      The Purpose’s transparency requirements are met for each Purpose on the legal basis of legitimate interest and the user has not exercised their “Right to Object” to that Purpose.<br><br>By default or if the user has exercised their “Right to Object” to a Purpose, the corresponding bit for that Purpose is set to 0. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field.</td>
    </tr>
    <tr>
  <td>PurposeOneTreatment</td>
  <td>Boolean</td>
  <td>1 Purpose 1 was NOT disclosed at all.<br><br>0 Purpose 1 was disclosed commonly as consent as expected by the Policies.<br><br>CMPs can use the PublisherCC field to indicate the legal jurisdiction the publisher is under to help vendors determine whether the vendor needs consent for Purpose 1.</td>
  </tr>
  <tr>
  <td>PublisherCC</td>
  <td>String (2)</td>
  <td>The country code of the country that determines legislation of reference. Commonly, this corresponds to the country in which the publisher’s business entity is established.
    Each letter is encoded as 6 bits, <code>a=0..z=25</code>. <a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2"> ISO 3166-1 alpha-2 code </a> </td>
  </tr>
  <tr>
  <td>VendorConsent</td>
  <td>OptimizedIntRange</td>
  <td>List of Vendor IDs that indicate Consent for these vendors. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int.<br></br>Equivalent of the fields listed under the Vendor Consent Section as defined in the <a href="https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md">TCF v2 specification:</a> <br></br>MaxVendorId, <br></br>IsRangeEncoding, <br></br>BitField, NumEntries, IsARange, StartOrOnlyVendorId, EndVendorId</td>
  </tr>
  <tr>
  <td>VendorLegitimateInterest</td>
  <td>OptimizedIntRange</td>
  <td>List of Vendor IDs for which Legitimate Interest is established and the user did not exercise their “Right to Object”. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int.<br></br>Equivalent of the fields listed under the Vendor Legitimate Interest Section as defined in the <a href="https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md">TCF v2 specification:</a><br></br>MaxVendorId, <br></br>IsRangeEncoding, <br></br>BitField, NumEntries, IsARange, StartOrOnlyVendorId, EndVendorId </td>
  </tr>
  <tr>
  <td>PublisherRestrictions</td>
  <td>TCFPublisherRestriction</td>
  <td>List of restrictions to apply.</td>
  </tr>
  </table>
  
  


> **Note:** Fields marked with * are only included in the string encoded version of the GPP segment but will not be returned by the client side API. Instead, the client side API will return an array of int with the corresponding IDs.


## Disclosed Vendors Segment

The disclosed vendors segment is appended to the core segment by using the “.” (dot) delimiter. This is an optional TC String segment. The segment fields are:

<table>
<tr>
<td><strong>Field Name</strong></td>
<td><strong>GPP Field Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>SegmentType</td>
<td>Int(3)</td>
<td>Always set to 1.</td>
</tr>
<tr>
<td>DisclosedVendors</td>
<td>OptimizedIntRange</td>
  <td>List of Vendor IDs that were disclosed in a CMP UI to the user. <br></br>Equivalent of the fields listed under Disclosed Vendors as defined in the <a href="https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md">TCF v2 specification:</a><br></br>MaxVendorId, <br></br>IsRangeEncoding, <br></br>BitField, NumEntries, IsARange, StartOrOnlyVendorId, EndVendorId</td>
</tr>
</table>



## Publisher Purposes Segment

The publisher purposes segment is appended to the core segment by using the “.” (dot) delimiter. The segment is optional. The segment fields are:


<table>
<tr>
<td><strong>Field Name</strong></td>
<td><strong>GPP Field Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>SegmentType</td>
<td>Int(3)</td>
<td>Always set to 3.</td>
</tr>
<tr>
<td>PubPurposesConsent</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:<br></br>1 Consent<br></br>0 No Consent</td>
</tr>
<tr>
<td>PubPurposesLITransparency</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:<br></br>1 legitimate interest established<br></br>0 legitimate interest was NOT established or it was established but user exercised their “Right to Object” to the Purpose</td>
</tr>
<tr>
<td>NumCustomPurposes</td>
<td>Int(6)</td>
<td>The number of Custom Purposes.</td>
</tr>
<tr>
<td>CustomPurposesConsent</td>
<td>Bitfield(NumCustomPurposes)</td>
<td>One bit for each Purpose:<br></br>1 Consent<br></br>0 No Consent</td>
</tr>
<tr>
<td>CustomPurposesLITransparency</td>
<td>Bitfield(NumCustomPurposes)</td>
<td>One bit for each Purpose:<br></br>1 legitimate interest established<br></br>0 implied consent was NOT established or it was established but user exercised their “Right to Object” to the Custom Purpose</td>
</tr>
</table>



# Client side API

The client side API does not expose the following custom GPP commands:

## getTCData


<table>
<tr>
<td>Command:</td>
<td>tcfcav2.getTCData</td>
</tr>
<tr>
<td>Callback:</td>
<td>function(tcData: object, success: boolean)</td>
</tr>
<tr>
<td>Parameter:</td>
<td>not used</td>
</tr>
<tr>
<td>Description</td>
<td>Please note that this command is only used for downward compatibility. Developers should use the generic GPP command getSection or getField instead.<br></br>When called, the callback function will be called with the javascript representation of the parsed Core Segment (see above) and Publisher segment as tcData.</td>
</tr>
</table>



## Key Names

In the mobile or CTV context, the key names to be used in GPP are listed below. For complete details on the expected values for each key listed below, see the [IAB TCF EU v2 specification.](https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md#what-is-the-cmp-in-app-internal-structure-for-the-defined-api)


<table>
<tr>
<td><strong>TCF Key Name</strong></td>
<td><strong>GPP Key Name</strong></td>
</tr>
<tr>
<td>IABTCF_CmpSdkID</td>
<td>IABGPP_TCFEU2_CmpSdkID</td>
</tr>
<tr>
<td>IABTCF_CmpSdkVersion</td>
<td>IABGPP_TCFEU2_CmpSdkVersion</td>
</tr>
<tr>
<td>IABTCF_PolicyVersion</td>
<td>IABGPP_TCFEU2_PolicyVersion</td>
</tr>
<tr>
<td>IABTCF_gdprApplies</td>
<td>IABGPP_TCFEU2_gdprApplies</td>
</tr>
<tr>
<td>IABTCF_PublisherCC</td>
<td>IABGPP_TCFEU2_PublisherCC</td>
</tr>
<tr>
<td>IABTCF_PurposeOneTreatment</td>
<td>IABGPP_TCFEU2_PurposeOneTreatment</td>
</tr>
<tr>
<td>IABTCF_UseNonStandardStacks</td>
<td>IABGPP_TCFEU2_UseNonStandardStacks</td>
</tr>
<tr>
<td>IABTCF_TCString</td>
<td>IABGPP_2_TCString</td>
</tr>
<tr>
<td>IABTCF_VendorConsents</td>
<td>IABGPP_TCFEU2_VendorConsents</td>
</tr>
<tr>
<td>IABTCF_VendorLegitimateInterests</td>
<td>IABGPP_TCFEU2_VendorLegitimateInterests</td>
</tr>
<tr>
<td>IABTCF_PurposeConsents</td>
<td>IABGPP_TCFEU2_PurposeConsents</td>
</tr>
<tr>
<td>IABTCF_PurposeLegitimateInterests</td>
<td>IABGPP_TCFEU2_PurposeLegitimateInterests</td>
</tr>
<tr>
<td>IABTCF_SpecialFeaturesOptIns</td>
<td>IABGPP_TCFEU2_SpecialFeaturesOptIns</td>
</tr>
<tr>
<td>IABTCF_PublisherRestrictions{ID}</td>
<td>IABGPP_TCFEU2_PublisherRestrictions{ID}</td>
</tr>
<tr>
<td>IABTCF_PublisherConsent</td>
<td>IABGPP_TCFEU2_PublisherConsent</td>
</tr>
<tr>
<td>IABTCF_PublisherLegitimateInterests</td>
<td>IABGPP_TCFEU2_PublisherLegitimateInterests</td>
</tr>
<tr>
<td>IABTCF_PublisherCustomPurposesConsents</td>
<td>IABGPP_TCFEU2_PublisherCustomPurposesConsents</td>
</tr>
<tr>
<td>IABTCF_PublisherCustomPurposesLegitimateInterests</td>
<td>IABGPP_TCFEU2_PublisherCustomPurposesLegitimateInterests</td>
</tr>
</table>
