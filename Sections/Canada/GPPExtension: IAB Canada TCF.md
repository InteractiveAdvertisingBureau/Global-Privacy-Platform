<h1>IAB Canada TCF Technical Specification</h1>
<h2>About this document</h2>
<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform" target="_blank" rel="noopener">GPP</a> defines a way how local standards can &ldquo;plug-in&rdquo; into the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md" target="_blank" rel="noopener">GPP client side API </a>. This document outlines the technical specification for using the IAB Transparency &amp; Consent Framework Canada under these GPP specifications.&nbsp;</p>
<h2>Summary</h2>
<div>
<table>
<tbody>
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
<td>The IAB TCF Canada is registered with client side API prefix "tcfcav1" in the GPP Client Side API.</td>
</tr>
</tbody>
</table>
</div>
<h2>Section encoding</h2>
<p>The IAB TCF Canada will be using the following encoding for the GPP section. If already familiar with the IAB TCF Europe encoding, you may view the detailed differences between the two on the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/Canada/TCF%20EU%20TCF%20CA%20Comparison.md" target="_blank" rel="noopener">IAB Europe TCF with IAB Canada TCF Signal Definition</a> documentation.</p>
<p>Note: in the JS representation of the section, the field name should be in UpperCamelCase, just like the column "Field name". Follow [this table](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding) to map the GPP field types to JavaScript native data types.<p>
<h3>Core sub-section</h3>
<p>The core sub-section must always be present. It consists of the following fields:</p>
<div>
<table>
<thead>
<tr>
<th>Field name</th>
<th>GPP Field Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
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
<td>Consent Management Platform ID that last updated the TC String. A unique ID will be assigned to each Consent Management Platform.&nbsp;</td>
</tr>
<tr>
<td>CmpVersion</td>
<td>Int(12)</td>
<td>Consent Management Platform version of the CMP that last updated this TC String. Each change to a CMP should increment their internally assigned version number as a record of which version the user gave consent and transparency was established.&nbsp;</td>
</tr>
<tr>
<td>ConsentScreen</td>
<td>Int(6)</td>
<td>CMP Screen number at which consent was given for a user with the CMP that last updated this TC String . The number is a CMP internal designation and is CmpVersion specific. The number is used for identifying on which screen a user gave consent as a record.&nbsp;</td>
</tr>
<tr>
<td>ConsentLanguage</td>
<td>String(2)</td>
<td>Two-letter <a href="https://en.wikipedia.org/wiki/ISO_639-1" target="_blank" rel="noopener">ISO 639-1</a> language code in which the CMP UI was presented&nbsp;</td>
</tr>
<tr>
<td>VendorListVersion</td>
<td>Int(12)</td>
<td>Version of the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a> used to create this TC String. Number corresponds to <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a> vendorListVersion</td>
</tr>
<tr>
<td>TcfPolicyVersion</td>
<td>Int(6)</td>
<td>Version of policy used within <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a>. From the corresponding field in the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a> that was used for obtaining consent. A new policy version invalidates existing strings and requires CMPs to re-establish transparency and consent from users.&nbsp;</td>
</tr>
<tr>
<td>UseNonStandardStacks</td>
<td>Boolean</td>
<td><code>1</code> CMP used non-IAB standard stacks during consent gathering
  <p><code>0</code> IAB standard stacks were used</p> 
    <p>Setting this to 1 means that a publisher-run CMP - that is still IAB Canada registered - is using customized Stack descriptions and not the standard stack descriptions defined in the <a href="https://iabcanada.com/tcf-policies/" target="_blank" rel="noopener">Policies</a> (Appendix A section E). A CMP that services multiple publishers sets this value to 0.</p></td>
</tr>
<tr>
<td>SpecialFeatureExpressConsent</td>
<td>Bitfield(12)</td>
<td>One bit for each Special Feature:
  <p><code>1</code> Opted in (express consent)</p>
  <p><code>0</code> Not opted in (no express consent)</p> 
  <p>The TCF <a href="https://iabcanada.com/tcf-policies/" target="_blank" rel="noopener">Policies</a> designates certain Features as "special" which means a CMP must afford the user a means to expressly consent to their use. These "Special Features" are published and numerically identified in the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">Global Vendor List</a> separately from normal Features.</p></td>
</tr>
<tr>
<td>PurposesExpressConsent</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:
  <p><code>1</code> Express Consent</p>
  <p><code>0</code> No Express Consent</p> 
  <p>The user's consent value for each Purpose established on the legal basis of consent.The Purposes are numerically identified and published in the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">Global Vendor List</a>. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field. Note that purpose 1 bit is not used in TCF Canada.</p></td>
</tr>
<tr>
<td>PurposesImpliedConsent</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:
<p><code>1</code> implied consent established</p>
<p><code>0</code> implied consent was <strong>NOT</strong> established or it was established but user exercised an Objection to the Purpose</p> 
<p>The Purpose's transparency requirements are met for each Purpose on the legal basis of implied consent and the user has not exercised an Objection to that Purpose.</p> 
<p>By default or if the user has exercised an Objection to a Purpose, the corresponding bit for that Purpose is set to 0. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field. Note that purpose 1 bit is not used in TCF Canada.</p></td>
</tr>
<tr>
<td>VendorExpressConsent</td>
<td>OptimizedRange</td>
<td>List of Vendor IDs that indicate Consent for these vendors. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int.</td>
</tr>
<tr>
<td>VendorImpliedConsent</td>
<td>OptimizedRange</td>
<td>List of Vendor IDs for which Implied consent is established and the user did not exercise an Objection.. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int.</td>
</tr>
<tr>
<td>PubRestrictions</td>
<td>N-ArrayOfRanges (6,2)</td>
<td><p></p><b>Key:</b> The Vendor’s declared Purpose ID that the Publisher has indicated they are overriding.</p>
    <p><b>Types:</b></p>
    <p><code>0</code> Purpose Flatly Not Allowed by Publisher (regardless of Vendor declarations)</p>
    <p><code>1</code> Require Express Consent (if Vendor has declared the Purpose IDs legal basis as Implied Consent and flexible)</p>
    <p><code>2</code> Require Implied Consent (if Vendor has declared the Purpose IDs legal basis as Express Consent and flexible)</p>
    <p><code>3</code> UNDEFINED (not used)</li></p>
  <p><b>ids</b> - A single or range of Vendor ID(s) who the publisher has designated as restricted under the purpose id.</p>
</tr>  
</tbody>
</table>
</div>
<h3>Disclosed Vendors Sub-section</h3>
    <p>The disclosed vendors sub-section is appended to the core sub-section by using the “.” (dot) delimiter. This is an optional string sub-section. It may be used by a CMP while storing strings, but must not be included in the string when returned by the CMP API. The sub-section fields are:</p> 
<div>
  <table>
    <thead><tr><th>Field name</th>
      <th>GPP Field Type</th>
      <th>Description</th>
    </tr></thead>
    <tbody>
      <tr>
        <td>SubsectionType</td>
        <td>Int(3)</td>
        <td>Always set to 1</td>
      </tr>
      <tr>
        <td>DisclosedVendors</td>
        <td>OptimizedRange</td>
        <td>List of Vendor IDs that were disclosed in a CMP UI to the user</td>
      </tr>
    </tbody></table></div>
<h3>Publisher Purposes Sub-section</h3>
<p>The publisher purposes sub-section is appended to the core sub-section by using the &ldquo;.&rdquo; (dot) delimiter. The sub-section is optional. The sub-section fields are:</p>
<div>
<table>
<thead>
<tr>
<th>Field name</th>
<th>GPP Field Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>SubsectionType</td>
<td>Int(3)</td>
<td>Always set to 3.</td>
</tr>
<tr>
<td>PubPurposesExpressConsent&nbsp;</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:1 Express Consent0 No Express Consent</td>
</tr>
<tr>
<td>PubPurposesImpliedConsent&nbsp;</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:1 implied consent established0 implied consent was <strong>NOT</strong> established or it was established but user exercised an Objection to the Purpose&nbsp;</td>
</tr>
<tr>
<td>NumCustomPurposes</td>
<td>Int(6)</td>
<td>The number of Custom Purposes.</td>
</tr>
<tr>
<td>CustomPurposesExpressConsent&nbsp;</td>
<td>Bitfield(NumCustomPurposes)</td>
<td>One bit for each Custom Purpose:1 Express Consent0 No Express Consent</td>
</tr>
<tr>
<td>CustomPurposesImpliedConsent&nbsp;</td>
<td>Bitfield(NumCustomPurposes)</td>
<td>One bit for each Custom Purpose:1 implied consent established0 implied consent was <strong>NOT</strong> established or it was established but user exercised an Objection to the Custom Purpose</td>
</tr>
</tbody>
</table>
</div>
<h2>Client side API</h2>
<h3>Key Names</h3>
<p>In the mobile or CTV context, the key names must follow the the naming conventions defined in the In-App Key Names portion of the GPP API Specification. The in-app values should also follow what is defined in the In-App Key Names portion of the specification and be transformed accordingly (for example, a field that has a data type of OptimizedRange will be converted to a string with an underscore used to separate each value).</p>
<p>Below are some examples of the key names for TCF Canada. </p>
<div>
<table>
<tbody>
<tr>
<td><strong>GPP Key Name</strong></td>
<td><strong>Value(s)</strong></td>
</tr>
<tr>
<td><code>IABGPP_TCFCAV1_CmpId</code></td>
<td><b>Number:</b> The unsigned integer ID of CMP SDK</td>
</tr>
<tr>
<td><code>IABGPP_TCFCAV1_CmpVersion</code></td>
<td><b>Number:</b> The unsigned integer version number of CMP SDK</td>
</tr>
<tr>
<td><code>IABGPP_TCFCAV1_TcfPolicyVersion</code></td>
<td><b>Number:</b> The unsigned integer representing the version of the TCF that these consents adhere to.</td>
</tr>
<tr>
<td><code">IABGPP_TCFCAV1_UseNonStandardStacks</code></td>
<td><b>Number:</b> 1 - CMP used a non-standard stack; 0 - CMP did not use a non-standard stack</td>
</tr>
<tr>
<td><code>IABGPP_5_TCString</code></td>
<td><b>String:</b> Full encoded TC string</td>
</tr>
<tr>
<td><code>IABGPP_TCFCAV1_VendorExpressConsents</code></td>
<td><b>String:</b> Per the field description above, this is an array of integers that represent the list of Vendor IDs that indicate consent for these vendors. Since the data type for this field is OptimizedRange, the value for this should be a string (e.g. “1_4_99”). See In-App Key Names section of the GPP API Specification for more details.</td>
</tr>
<tr>
<td><code>IABGPP_TCFCAV1_PubRestrictions</code></td>
<td><b>String:</b> Per the field description above, this is a sequence of id:type pairs representing the Vendor IDs who the publisher has designated as restricted under the purpose id and the type of restriction.

<p>Since the data type for this field is N-ArrayofRanges, the value for this should be a string (e.g. "3:0_5:1_6:1_7:2_12:0"). See In-App Key Names section of the GPP API Specification for more details.</p></td>
</tr>
<td><code>IABGPP_TCFCAV1_PublisherExpressConsent</code></td>
<td><b>Binary String:</b> The'0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the purpose consent status for purpose ID n+1 for the publisher as they correspond to the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md#what-is-the-global-vendor-list" target="_blank" rel="noopener">Global Vendor List</a> Purposes; false and true respectively. eg. '1' at index 0 is consent true for purpose ID 1</td>
</tr>
</tbody>
</table>
</div>
<h2>Summary of differences when compared with TCF EU</h2>
<ul>
<li>References to "consent" should be read as "express consent"</li>
<li>References to "legitimate interest" should be read as "implied consent"</li>
<li>References to "special feature opt ins" should be read as "special feature express consent"</li>
<li>References to a "Right to Object" should be read as a user exercising an "Objection"</li>
</ul>
