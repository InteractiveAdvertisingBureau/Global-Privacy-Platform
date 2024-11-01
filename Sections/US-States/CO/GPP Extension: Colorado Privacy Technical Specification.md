<h1 id="gpp-extension-colorado-privacy-technical-specification">GPP Extension: Colorado Privacy Technical Specification</h1>
<h2 id="about-this-document">About this document</h2>
<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a> defines a way for local standards to &quot;plug-in&quot; to the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical specification for using the Colorado section of the GPP specification by those who (i) are Signatories to IAB Privacy, Inc.’s <a href=https://www.iabprivacy.com/>Multi-State Privacy Agreement (MSPA)</a>; and (ii) those who are not signatories of the MSPA.</p>

<h3>Version History&nbsp;</h3>
<div>
<table>
<tbody>
<tr>
<td><strong>Date</strong></td>
<td><strong>Version</strong></td>
<td><strong>Comments</strong></td>
</tr>
<tr>
<td>December 2022</td>
<td>1.0</td>
<td>Version 1.0 released</td>
</tr>
</tbody>
</table>
</div>


<h2 id="colorado-privacy-section">Colorado Privacy Section</h2>
<p>The Colorado Privacy Section consists of the components described below. Users should employ the Colorado Privacy Section only if they have determined the CPA applies to their processing of a consumer&#39;s personal data.</p>
<h3 id="summary">Summary</h3>
<table>
<thead>
<tr>
<th style="text-align:left"><strong>Type</strong></th>
<th style="text-align:left"><strong>Value</strong></th>
<th style="text-align:left"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">GPP Section ID</td>
<td style="text-align:left">10</td>
<td style="text-align:left">The Colorado Section is registered as Section ID 10 under the GPP.</td>
</tr>
<tr>
<td style="text-align:left">Client side API prefix</td>
<td style="text-align:left">usco</td>
<td style="text-align:left">The Colorado Privacy Section is registered with client side API prefix &quot;usco&quot; in the GPP Client Side API.</td>
</tr>
</tbody>
</table>
<h3 id="section-encoding">Section encoding</h3>
<p>Note: in the JS representation of the section, the field name should be in UpperCamelCase, just like the column "Field name". Follow [this table](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding) to map the GPP field types to JavaScript native data types.<p>
<h4 id="core-segment">Core Segment</h4>
<p>The core segment must always be present. Where terms are capitalized in the ‘description’ field they are defined terms in Colo. Rev. Stat. 6-1-1303. It consists of the following fields:</p>
<table>
<thead>
<tr>
<th style="text-align:left"><strong>Field name</strong></th>
<th style="text-align:left"><strong>GPP Field Type</strong></th>
<th style="text-align:left"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">Version</td>
<td style="text-align:left">Int(6)</td>
<td style="text-align:left">The version of this section specification used to encode the string.</td>
</tr>
<tr>
<td style="text-align:left">SharingNotice</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Notice of the Sharing of Personal Data with Third Parties.<p><code>0</code> Not Applicable. The Controller does not share Personal Data with Third Parties.<p><code>1</code> Yes, notice was provided<p><code>2</code> No, notice was not provided</td>
</tr>
<tr>
<td style="text-align:left">SaleOptOutNotice</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Notice of the Opportunity to Opt Out of the Sale of the Consumer&#39;s Personal Data<p><code>0</code> Not Applicable. The Controller does not Sell Personal Data.<p><code>1</code> Yes, notice was provided<p><code>2</code> No, notice was not provided</td>
</tr>
<tr>
<td style="text-align:left">TargetedAdvertisingOptOutNotice</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Notice of the Opportunity to Opt Out of Processing of the Consumer&#39;s Personal Data for Targeted Advertising<p><code>0</code> Not Applicable.The Controller does not Process Personal Data for Targeted Advertising.<p><code>1</code> Yes, notice was provided<p><code>2</code> No, notice was not provided</td>
</tr>
<tr>
<td style="text-align:left">SaleOptOut</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Opt-Out of the Sale of the Consumer&#39;s Personal Data<p><code>0</code> Not Applicable. SaleOptOutNotice value was not applicable or no notice was provided<p><code>1</code> Opted Out<p><code>2</code> Did Not Opt Out</td>
</tr>
<tr>
<td style="text-align:left">TargetedAdvertisingOptOut</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Opt-Out of Processing the Consumer&#39;s Personal Data for Targeted Advertising<p><code>0</code> Not Applicable. TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided<p><code>1</code> Opted Out<p><code>2</code> Did Not Opt Out</td>
</tr>
<tr>
<td style="text-align:left">SensitiveDataProcessing</td>
<td style="text-align:left">N-Bitfield(2,7)</td>
<td style="text-align:left">Two bits for each Data Activity:<p><code>0</code> Not Applicable. The Controller does not Process the specific category of Sensitive Data.<p><code>1</code> No Consent<p><code>2</code> Consent<p>(1) Consent to Process the Consumer&#39;s Sensitive Data Consisting of Personal Data Revealing Racial or Ethnic Origin.<p>(2) Consent to Process the Consumer&#39;s Sensitive Data Consisting of Personal Data Revealing Religious Beliefs.<p>(3) Consent to Process the Consumer&#39;s Sensitive Data Consisting of Personal Data Revealing a Mental or Physical Health Condition or Diagnosis.<p>(4) Consent to Process the Consumer&#39;s Sensitive Data Consisting of Personal Data Revealing Sex Life or Sexual Orientation.<p>(5) Consent to Process the Consumer&#39;s Sensitive Data Consisting of Personal Data Revealing Citizenship or Citizenship Status.<p>(6) Consent to Process the Consumer&#39;s Sensitive Data Consisting of Genetic Data that May Be Processed for the Purpose of Uniquely Identifying an Individual.<p>(7) Consent to Process the Consumer&#39;s Sensitive Data Consisting of Biometric Data that May Be Processed for the Purpose of Uniquely Identifying an Individual.</td>
</tr>
<tr>
<td style="text-align:left">KnownChildSensitiveDataConsents</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Consent to Process Sensitive Data from a Known Child.<p><code>0</code> Not Applicable. The Controller does not Process Sensitive Data of a known Child.<p><code>1</code> No Consent<p><code>2</code> Consent</td>
</tr>
<tr>
<td style="text-align:left">MspaCoveredTransaction</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Publisher or Advertiser, as applicable, is a signatory to the IAB Multistate Service Provider Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a &quot;Covered Transaction&quot; as defined in the MSPA.<p><code>1</code> Yes<p><code>2</code> No</td>
</tr>
<tr>
<td style="text-align:left">MspaOptOutOptionMode</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Publisher or Advertiser, as applicable, has enabled &quot;Opt-Out Option Mode&quot; for the &quot;Covered Transaction,&quot; as such terms are defined in the MSPA.<p><code>0</code> Not Applicable<p><code>1</code> Yes<p><code>2</code> No</td>
</tr>
<tr>
<td style="text-align:left">MspaServiceProviderMode</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Publisher or Advertiser, as applicable, has enabled &quot;Service Provider Mode&quot; for the &quot;Covered Transaction,&quot; as such terms are defined in the MSPA.<p><code>0</code> Not Applicable<p><code>1</code> Yes<p><code>2</code> No</td>
</tr>
</tbody>
</table>

<h4 id="gpc-subsection">GPC Sub-section</h4>
<p><a href="https://globalprivacycontrol.github.io/gpc-spec/" target="_blank" rel="noopener">GPC</a> is signaled in user agent headers<code>(Sec-GPC)</code> and a simple javascript API <code>(globalPrivacyControl)</code>. Entities creating GPP strings should check for whether GPC is set and pass along the value they find (from the headers or javascript API) in this sub-section.</p>

<table>
<thead>
<tr>
<th style="text-align:left"><strong>Field Name</strong></th>
<th style="text-align:left"><strong>GPP Field Type</strong></th>
<th style="text-align:left"><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">SubsectionType</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left"><p><code>0</code> Core<p><code>1</code> GPC</td>
</tr>
<tr>
<td style="text-align:left">Gpc</td>
<td style="text-align:left">Boolean</td>
<td style="text-align:left"><p><code>0</code> false<p><code>1</code> true</td>
</tr>
</tbody>
</table>
