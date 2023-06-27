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
<td>The IAB TCF Canada is registered with client side API prefix &ldquo;tcfcav1&rdquo; in the GPP Client Side API.</td>
</tr>
</tbody>
</table>
</div>
<h2>Section encoding</h2>
<p>The IAB TCF Canada will be using the following encoding for the GPP section. If already familiar with the IAB TCF Europe encoding, you may view the detailed differences between the two on the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/Canada/TCF%20EU%20TCF%20CA%20Comparison.md" target="_blank" rel="noopener">IAB Europe TCF with IAB Canada TCF Signal Definition</a> documentation.&nbsp;</p>
<h3>Core segment</h3>
<p>The core segment must always be present. It consists of the following fields:</p>
<div>
<table>
<thead>
<tr>
<th>
<p><strong>Field name</strong></p>
</th>
<th>
<p><strong>GPP Field Type</strong></p>
</th>
<th>
<p><strong>Description</strong></p>
</th>
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
<td>Two-letter<a href="https://en.wikipedia.org/wiki/ISO_639-1" target="_blank" rel="noopener">ISO 639-1</a> language code in which the CMP UI was presented&nbsp;</td>
</tr>
<tr>
<td>VendorListVersion</td>
<td>Int(12)</td>
<td>Version of the<a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a> used to create this TC String. Number corresponds to<a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a> vendorListVersion</td>
</tr>
<tr>
<td>TcfPolicyVersion</td>
<td>Int(6)</td>
<td>Version of policy used within<a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a>. From the corresponding field in the<a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">GVL</a> that was used for obtaining consent. A new policy version invalidates existing strings and requires CMPs to re-establish transparency and consent from users.&nbsp;</td>
</tr>
<tr>
<td>UseNonStandardStacks</td>
<td>Boolean</td>
<td>1 CMP used non-IAB standard stacks during consent gathering0 IAB standard stacks were used Setting this to 1 means that a publisher-run CMP &ndash; that is still IAB Europe registered &ndash; is using customized Stack descriptions and not the standard stack descriptions defined in the<a href="https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/" target="_blank" rel="noopener">Policies</a> (Appendix A section E). A CMP that services multiple publishers sets this value to 0.&nbsp;</td>
</tr>
<tr>
<td>SpecialFeatureExpressConsent&nbsp;</td>
<td>Bitfield(12)</td>
<td>One bit for each Special Feature:1 Opted in (express consent)0 Not opted in (no express consent) The TCF<a href="https://iabeurope.eu/iab-europe-transparency-consent-framework-policies/" target="_blank" rel="noopener">Policies</a> designates certain Features as &ldquo;special&rdquo; which means a CMP must afford the user a means to expressly consent to their use. These &ldquo;Special Features&rdquo; are published and numerically identified in the<a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">Global Vendor List</a> separately from normal Features.&nbsp;</td>
</tr>
<tr>
<td>PurposesExpressConsent&nbsp;</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:1 Express Consent0 No Express Consent The user&rsquo;s consent value for each Purpose established on the legal basis of consent.The Purposes are numerically identified and published in the<a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list" target="_blank" rel="noopener">Global Vendor List</a>. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field. Note that purpose 1 bit is not used in TCF Canada.</td>
</tr>
<tr>
<td>PurposesImpliedConsent&nbsp;</td>
<td>Bitfield(24)</td>
<td>One bit for each Purpose:1 implied consent established0 implied consent was <strong>NOT</strong> established or it was established but user exercised an Objection to the Purpose The Purpose&rsquo;s transparency requirements are met for each Purpose on the legal basis of implied consent and the user has not exercised an Objection to that Purpose.By default or if the user has exercised an Objection to a Purpose, the corresponding bit for that Purpose is set to 0. From left to right, Purpose 1 maps to the 0th bit, purpose 24 maps to the bit at index 23. Special Purposes are a different ID space and not included in this field. Note that purpose 1 bit is not used in TCF Canada.</td>
</tr>
<tr>
<td>VendorExpressConsent</td>
<td>OptimizedRange</td>
<td>List of Vendor IDs that indicate Consent for these vendors. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int.&nbsp;</td>
</tr>
<tr>
<td>VendorImpliedConsent&nbsp;</td>
<td>OptimizedRange</td>
<td>List of Vendor IDs for which Implied consent is established and the user did not exercise an Objection.. Please note that the field is composed of several fields in order to store the data in GPP string format. The client side API format is array of int.&nbsp;</td>
</tr>
</tbody>
</table>
</div>
<p><strong>Note: </strong>Fields marked with * are only included in the string encoded version of the GPP segment but will not be returned by the client side API. Instead the client side API will return an array of int with the corresponding IDs.</p>
<h3>Publisher Purposes Segment</h3>
<p>The publisher purposes segment is appended to the core segment by using the &ldquo;.&rdquo; (dot) delimiter. The segment is optional. The segment fields are:</p>
<div>
<table>
<thead>
<tr>
<th>
<p><strong>Field name</strong></p>
</th>
<th>
<p><strong>GPP Field Type</strong></p>
</th>
<th>
<p><strong>Description</strong></p>
</th>
</tr>
</thead>
<tbody>
<tr>
<td>SegmentType</td>
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
<p>In the mobile or CTV context, the key names to be used in GPP are listed below.&nbsp;</p>
<div>
<table>
<tbody>
<tr>
<td><strong>GPP Key Name</strong></td>
<td><strong>Value(s)</strong></td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_CmpSdkID</span></td>
<td>Number: The unsigned integer ID of CMP SDK</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_CmpSdkVersion</span></td>
<td>Number: The unsigned integer version number of CMP SDK</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_PolicyVersion</span></td>
<td>Number: The unsigned integer representing the version of the TCF that these consents adhere to.</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_UseNonStandardStacks</span></td>
<td>Number:1 - CMP used a non-standard stack0 - CMP did not use a non-sta<span style="color: #24292f;">ndard stack</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_5_TCString</span></td>
<td>String: Full encoded TC string</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_VendorExpressConsents</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the consent status for Vendor ID n+1; false and true respectively. eg. '1' at index 0 is consent true for vendor ID 1</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_VendorImpliedConsents</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the legitimate interest status for Vendor ID n+1; false and true respectively. eg. '1' at index 0 is legitimate interest established true for vendor ID 1</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_PurposeExpressConsents</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the consent status for purpose ID n+1; false and true respectively. eg. '1' at index 0 is legitimate interest established true for purpose ID 1</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_PurposeImpliedConsents</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the legitimate interest status for purpose ID n+1; false and true respectively. eg. '1' at index 0 is legitimate interest established true for purpose ID 1</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_SpecialFeaturesExpressConsents</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the opt-in status for special feature ID n+1; false and true respectively. eg. '1' at index 0 is opt-in true for special feature ID 1</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_PublisherExpressConsent</span></td>
<td><span style="color: #24292f;">Binary String</span><span style="color: #24292f;">: The </span><span style="color: #24292f;">'0'</span><span style="color: #24292f;"> or </span><span style="color: #24292f;">'1'</span><span style="color: #24292f;"> at position n &ndash; where n's indexing begins at </span><span style="color: #24292f;">0</span><span style="color: #24292f;"> &ndash; indicates the purpose consent status for purpose ID n+1 for the publisher as they correspond to the </span><a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md#what-is-the-global-vendor-list" target="_blank" rel="noopener">Global Vendor List</a><span style="color: #24292f;"> Purposes; </span><span style="color: #24292f;">false</span><span style="color: #24292f;"> and </span><span style="color: #24292f;">true</span><span style="color: #24292f;"> respectively. eg. </span><span style="color: #24292f;">'1'</span><span style="color: #24292f;"> at index </span><span style="color: #24292f;">0</span><span style="color: #24292f;"> is consent </span><span style="color: #24292f;">true</span><span style="color: #24292f;"> for purpose ID </span><span style="color: #24292f;">1</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_PublisherImpliedConsent</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the purpose legitimate interest status for purpose ID n+1 for the publisher as they correspond to the <a href="https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md#what-is-the-global-vendor-list" target="_blank" rel="noopener">Global Vendor List</a> Purposes; false and true respectively. eg. '1' at index 0 is legitimate interest established true for purpose ID 1</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_PublisherCustomPurposesExpressConsents</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the purpose consent status for the publisher's custom purpose ID n+1 for the publisher; false and true respectively. eg. '1' at index 0 is consent true for custom purpose ID 1</td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_TCFCA_PublisherCustomPurposesImpliedConsents</span></td>
<td>Binary String: The '0' or '1' at position n &ndash; where n's indexing begins at 0 &ndash; indicates the purpose legitimate interest status for the publisher's custom purpose ID n+1 for the publisher; false and true respectively. eg. '1' at index 0 is legitimate interest established true for custom purpose ID 1</td>
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
