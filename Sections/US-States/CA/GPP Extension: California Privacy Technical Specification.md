<h1 id="gpp-extension-california-privacy-technical-specification">GPP Extension: California Privacy Technical Specification</h1>
<h2 id="about-this-document">About this document</h2>
<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a> defines a way for local standards to &quot;plug-in&quot; to the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical specification for using the California section of the GPP specification by those who (i) are Signatories to IAB Privacy, Inc.’s <a href=https://www.iabprivacy.com/>Multi-State Privacy Agreement (MSPA)</a>; and (ii) those who are not signatories of the MSPA.</p>


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



<h2 id="california-privacy-section">California Privacy Section</h2>
<p>The California Privacy Section consists of the components described below. Users should employ the California Privacy String only if they have determined the CPRA applies to their processing of a consumer&#39;s personal information.</p>
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
<td style="text-align:left">GPP SectionID</td>
<td style="text-align:left">8</td>
<td style="text-align:left">The US California Section is registered as Section ID 8 under the GPP.</td>
</tr>
<tr>
<td style="text-align:left">Client side API prefix</td>
<td style="text-align:left">usca</td>
<td style="text-align:left">The California Privacy Section is registered with client side API prefix &quot;usca&quot; in the GPP Client Side API.</td>
</tr>
</tbody>
</table>
<h3 id="section-encoding">Section encoding</h3>
<h4 id="core-section">Core Sub-section</h4>
<p>The core sub-section must always be present. Where terms are capitalized in the ‘description’ field they are defined terms in Cal. Civ. Code 1798.140. It consists of the following fields:
</p>
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
<td style="text-align:left">SaleOptOutNotice</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Notice of the Opportunity to Opt Out of the Sale of the Consumer&#39;s Personal Information<p><code>0</code> Not Applicable. The Business does not Sell Personal Data.<p><code>1</code> Yes, notice was provided<p><code>2</code> No, notice was not provided</td>
</tr>
<tr>
<td style="text-align:left">SharingOptOutNotice</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Notice of the Opportunity to Opt Out of the Sharing of the Consumer&#39;s Personal Information<p><code>0</code> Not Applicable.The Business does not Share Personal Data.<p><code>1</code> Yes, notice was provided<p><code>2</code> No, notice was not provided</td>
</tr>
<tr>
<td style="text-align:left">SensitiveDataLimitUseNotice</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Notice of the Opportunity to Limit Use or Disclosure of the Consumer&#39;s Sensitive Personal Information<p><code>0</code> Not Applicable. The Business does not use or disclose Sensitive Data.<p><code>1</code> Yes, notice was provided<p><code>2</code> No, notice was not provided</td>
</tr>
<tr>
<td style="text-align:left">SaleOptOut</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Opt-Out of the Sale of the Consumer&#39;s Personal Information<p><code>0</code> Not Applicable. SaleOptOutNotice value was not applicable or no notice was provided<p><code>1</code> Opted Out<p><code>2</code> Did Not Opt Out</td>
</tr>
<tr>
<td style="text-align:left">SharingOptOut</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Opt-Out of the Sharing of the Consumer&#39;s Personal Information<p><code>0</code> Not Applicable. SharingOptOutNotice value was not applicable or no notice was provided.<p><code>1</code> Opted Out<p><code>2</code> Did Not Opt Out</td>
</tr>
<tr>
<td style="text-align:left">SensitiveDataProcessing</td>
<td style="text-align:left">N-Bitfield(2,9)</td>
<td style="text-align:left">Two bits for each Data Activity:<p><code>0</code> Not Applicable. SensitiveDataLimitUseNotice value was not applicable or no notice was provided.<p><code>1</code> Opted Out<p><code>2</code> Did Not Opt Out<p> Data Activities: <p>(1) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Which Reveals a Consumer&#39;s Social Security, Driver&#39;s License, State Identification Card, or Passport Number.<p>(2) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Which Reveals a Consumer&#39;s Account Log-In, Financial Account, Debit Card, or Credit Card Number in Combination with Any Required Security or Access Code, Password, or Credentials Allowing Access to an Account.<p>(3) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Which Reveals a Consumer&#39;s Precise Geolocation.<p>(4) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Which Reveals a Consumer&#39;s Racial or Ethnic Origin, Religious or Philosophical Beliefs, or Union Membership.<p>(5) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Which Reveals the contents of a Consumer&#39;s Mail, Email, and Text Messages unless You Are the Intended Recipient of the Communication.<p>(6) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Which Reveals a Consumer&#39;s Genetic Data.<p>(7) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Consisting of Biometric Information tor the Purpose of Uniquely Identifying a Consumer.<p>(8) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Consisting of Personal Information Collected and Analyzed Concerning a Consumer&#39;s Health.<p>(9) Opt-Out of the Use or Disclosure of the Consumer&#39;s Sensitive Personal Information Consisting of Personal Information Collected and Analyzed Concerning a Consumer&#39;s Sex Life or Sexual Orientation.</td>
</tr>
<tr>
<td style="text-align:left">KnownChildSensitiveDataConsents</td>
<td style="text-align:left">N-Bitfield(2,2)</td>
<td style="text-align:left">Two bits for each Data Activity:<p><code>0</code> Not Applicable. The Business does not have actual knowledge that it Processes Personal Information of Consumers Less Than 16 years of Age.<p><code>1</code> No Consent<p><code>2</code> Consent<p>Data Activities:<p>(1) Consent to Sell the Personal Information of Consumers Less Than 16 years of Age<p>(2) Consent to Share the Personal Information of Consumers Less Than 16 years of Age</td>
</tr>
<tr>
<td style="text-align:left">PersonalDataConsents</td>
<td style="text-align:left">Int(2)</td>
<td style="text-align:left">Consent to Collection, Use, Retention, Sale, and/or Sharing of the Consumer&#39;s Personal Data that Is Unrelated to or Incompatible with the Purpose(s) for which the Consumer&#39;s Personal Data Was Collected or Processed<p><code>0</code> Not Applicable. The Business does not use, retain, Sell, or Share the Consumer&#39;s Personal Data for advertising purposes that are unrelated to or incompatible with the purpose(s) for which the Consumer&#39;s Personal Data was collected or processed.<p><code>1</code> No Consent<p><code>2</code> Consent</td>
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


