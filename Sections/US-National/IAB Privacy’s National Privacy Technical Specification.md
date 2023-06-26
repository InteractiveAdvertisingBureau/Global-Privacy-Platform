
<h1 id="gpp-extension-iab-privacy-s-national-privacy-technical-specification">GPP Extension: IAB Privacy’s US National Privacy Technical Specification</h1>

<h2 id="about-this-document">About this document</h2>

<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a> defines a way for local standards to &quot;plug-in&quot; into the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical specification for using the GPP specifications with the IAB Privacy Multi-State Privacy Agreement legal requirements.</p>

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

<h2>US National Privacy Section</h2>
<p style="text-align: justify;">The US National Privacy Section is a string that consists of the components described below. The US National Privacy Section is intended to be used  for MSPA Covered Transactions.  The requirements for using the US National Privacy Section for MSPA Covered Transactions are defined by the MSPA “US National Approach” as a way to comply with the highest common denominator of all different state privacy law requirements in circumstances where the First Party setting the values for the string: (1) does not know the state residency of the Consumer; or (2) otherwise does not wish to use the Consumer’s specific state residency to differentiate how they will treat the Consumer for purposes of compliance with applicable state privacy laws.  Requirements for using the components of the US National Privacy Section relating to sensitive data and childrens’ data are not currently defined by the MSPA, but may be defined by a future amendment or addendum to the MSPA.</p> 

<p>Notwithstanding that the US National Privacy Section is intended to be used in conjunction with the MSPA, those who use it for non-MSPA Covered Transactions are representing to recipients of the string whether they have complied with the specific state law requirements referenced in the description of each string component.</p>

<p>The US National Privacy Section does not reflect any requirements of US federal law (for example, it does not reflect any COPPA consent requirements) and instead is intended only for use as a tool for compliance with applicable US state privacy law requirements.  </p>
<h3>Summary</h3>
<div>
<table>
<tbody>
<tr>
<td><strong>Field Type</strong></td>
<td><strong>Value</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>GPP SectionID</td>
<td>7</td>
<td>The US National Section is registered as Section ID 7 under the GPP.&nbsp;</td>
</tr>
<tr>
<td>Client side API prefix</td>
<td>usnat</td>
<td>The US National Privacy section is registered with client side API prefix &ldquo;usnat&rdquo; in the GPP Client Side API.</td>
</tr>
</tbody>
</table>
</div>

<h3>Section encoding</h3>
<h4>Core Segment</h4>
<p>The core segment must always be present. Where terms are capitalized in the &lsquo;description&rsquo; field they are defined terms in applicable State Privacy Laws and the MSPA. It consists of the following fields:</p>

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
<td>The version of this section specification used to encode the string.</td>
</tr>
<tr>
<td>SharingNotice</td>
<td>Int(2)</td>
<td>Notice of the Sharing of the Consumer&rsquo;s Personal Data with Third Parties.&nbsp;<p><p>References:
<ul>
<li>Virginia Code 59.1-578(C)(4) &ndash; (5)</li>
<li>Colo. Rev. Stat. 6-1-1308(1)(1)(IV) &ndash; (V)</li>
<li>Utah Code 13-61-302(1)(1)(iv) &ndash; (v)</li>
<li>Conn. PA No. 22-15, Sec. 6(3)(4)-(5)</li>
</ul>
<code>0</code>  Not Applicable. The Business does not share Personal Data with Third Parties.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SaleOptOutNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Opt Out of the Sale of the Consumer&rsquo;s Personal Data.<p><p>References:&nbsp;
<ul>
<li>Cal. Civ. Code 1798.100(1)(1), (3), Cal. Civ. Code 1798.135(1), and/or Cal. Civ. Code 1798.135(2), and rules promulgated thereunder.</li>
<li>Virginia Code 59.1-578(D)</li>
<li>Colo. Rev. Stat 6-1-1308(1)(2) and Colo. Rev. Stat. 6-1-1306(1)(1)(III)</li>
<li>Utah Code 13-61-302(1)(2)(i)</li>
<li>Conn. PA No. 22-15, Sec. 6(4) and Conn. PA No. 22-15, Sec. 4(2)</li>
</ul>
<code>0</code>  Not Applicable. The Business does not Sell Personal Data.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SharingOptOutNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Opt Out of the Sharing of the Consumer&rsquo;s Personal Data.<p><p>References:&nbsp;(i) Cal. Civ. Code 1798.100(1)(1), (3), (ii) Cal. Civ. Code 1798.135(1) and/or (iii) Cal. Civ. Code 1798.135(2)&nbsp;<p><code>0</code>  Not Applicable.The Business does not Share Personal Data.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>TargetedAdvertisingOptOutNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Opt Out of Processing of the Consumer&rsquo;s Personal Data for Targeted Advertising<p><p>References:&nbsp;
<ul>
<li>Virginia Code 59.1-578(D)</li>
<li>Colo. Rev. Stat 6-1-1308(1)(2) and Colo. Rev. Stat. 6-1-1306(1)(1)(III)</li>
<li>Utah Code 13-61-302(1)(2)(ii)</li>
<li>Conn. PA No. 22-15, Sec. 6(4) and Conn. PA No. 22-15, Sec. 4(2)</li>
</ul>
<code>0</code>  Not Applicable.The Business does not Process Personal Data for Targeted Advertising.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SensitiveDataProcessingOptOutNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Opt Out of the Processing of the Consumer&rsquo;s Sensitive Data<p><p>References:&nbsp;
<ul>
<li>Utah Code 13-61-302(3)(1)</li>
</ul>
<code>0</code>  Not Applicable. The Business does not Process Sensitive Data.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SensitiveDataLimitUseNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Limit Use or Disclosure of the Consumer&rsquo;s Sensitive Data<p><p>References:&nbsp;
<ul>
<li>Cal. Civ. Code 1798.100(1)(2)-(3), (ii) Cal. Civ. Code 1798.135(1), and/or (iii) Cal. Civ. Code 1798.135(2) and rules promulgated thereunder</li>
</ul>
<code>0</code>  Not Applicable. The Business does not use or disclose Sensitive Data.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SaleOptOut</td>
<td>Int(2)</td>
<td>Opt-Out of the Sale of the Consumer&rsquo;s Personal Data<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.135(1) and/or 1798.135(2)</li>
<li>Virginia Code 59.1-578(D)</li>
<li>Colo. Rev. Stat. 6-1-1306(1)(1)(III) or 6-1-1306(1)(1)(IV)</li>
<li>Utah Code 13-61-302(1)(2)(i)</li>
<li>Conn. PA No. 22-15, Sec. 4(5)(i) or (ii)</li>
</ul>
<code>0</code>  Not Applicable. SaleOptOutNotice value was not applicable or no notice was provided<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td>SharingOptOut</td>
<td>Int(2)</td>
<td>Opt-Out of the Sharing of the Consumer&rsquo;s Personal Data<p><p>References:&nbsp;
<ul>
<li>Cal. Civ. Code 1798.120(1) using a method that adheres to Cal. Civ. Code 1798.135(1) and/or 1798.135(2)</li>
</ul>
<code>0</code>  Not Applicable. SharingOptOutNotice value was not applicable or no notice was provided.<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td>TargetedAdvertisingOptOut</td>
<td>Int(2)</td>
<td>Opt-Out of Processing the Consumer&rsquo;s Personal Data for Targeted Advertising<p><p>References:
<ul>
<li>Virginia Code 59.1-578(D)</li>
<li>Colo. Rev. Stat. 6-1-1306(1)(1)(III) or 6-1-1306(1)(1)(IV)</li>
<li>Utah Code 13-61-302(1)(2)(ii)</li>
<li>Conn. PA No. 22-15, Sec. 4(5)(i) or (ii)</li>
</ul>
<code>0</code>  Not Applicable. TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td>SensitiveDataProcessing</td>
<td>N-Bitfield(2,12)</td>
<td>Two bits for each Data Activity:<code>0</code>  Not Applicable. The Business does not Process the specific category of Sensitive Data.<p><code>1</code> No Consent<p><code>2</code>  Consent&nbsp;<p>Data Activities:
<p>(1) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Racial or Ethnic Origin.&nbsp;<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(2) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Religious or Philosophical Beliefs.&nbsp;<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(3) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Concerning a Consumer&rsquo;s Health (including a Mental or Physical Health Condition or Diagnosis; Medical History; or Medical Treatment or Diagnosis by a Health Care Professional).<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(4) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Sex Life or Sexual Orientation.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(5) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Citizenship or Immigration Status.<p><p>References:
<ul>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(6) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual / Natural Person.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(7) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual / Natural Person.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(8) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Precise Geolocation Data.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
(9) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of a Consumer&rsquo;s Social Security, Driver&rsquo;s License, State Identification Card, or Passport Number.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
</ul>
(10) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of a Consumer&rsquo;s Account Log-In, Financial Account, Debit Card, or Credit Card Number in Combination with Any Required Security or Access Code, Password, or Credentials Allowing Access to an Account.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
</ul>
(11) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Union Membership.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
</ul>
(12) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of the contents of a Consumer&rsquo;s Mail, Email, and Text Messages unless You Are the Intended Recipient of the Communication.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</li>
</ul>
</td>
</tr>
<tr>
<td>KnownChildSensitiveDataConsents</td>
<td>N-Bitfield(2,2)</td>
<td>Two bits for each Data Activity:<code>0</code>  The Business does not have actual knowledge that it Processes Personal Data or Sensitive Data of a Consumer who is under 16 years old.<p><code>1</code> No Consent<p><code>2</code> Consent&nbsp;
  <p>Data Activities:</p>
  <p>(1) Consumer Consent to Process the Consumer’s Personal Data or Sensitive Data for selling, sharing, or targeted advertising for a Consumer  between the age of 13 and 16.
  <p>References:
    <ul>
      <li>Cal. Civ. Code Cal. Civ. Code 1798.120(c)</li>
      <li>Conn. PA 22-15, Sec. 6(a)(4)</li>
    </ul>
  <p></p>(2) Verifiable consent obtained from the Consumer’s parent or lawful guardian to Process the Personal Data or Sensitive Data of a Consumer Younger Than 13 Years of Age.
<p><p>References:
<ul>
<li>Cal. Civ. Code Cal. Civ. Code 1798.120(c)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
<li>Colo. Rev. Stat. 6-1-1308(7)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Conn. PA 22-15, Sec. 6(a)(4)</li>
</ul>
</td>
</tr>
<tr>
<td>PersonalDataConsents</td>
<td>Int(2)</td>
<td>Consent to Collection, Use, Retention, Sale, and/or Sharing of the Consumer&rsquo;s Personal Data that Is Unrelated to or Incompatible with the Purpose(s) for which the Consumer&rsquo;s Personal Data Was Collected or Processed&nbsp;<p><p>References:
<ul>
<li>&nbsp;Cal. Civ. Code 1798.100(c)&nbsp;</li>
</ul>
<code>0</code>  Not Applicable. The Business does not use, retain, Sell, or Share the Consumer&rsquo;s Personal Data for advertising purposes that are unrelated to or incompatible with the purpose(s) for which the Consumer&rsquo;s Personal Data was collected or processed.<p><code>1</code> No Consent<p><code>2</code> Consent&nbsp;</td>
</tr>
<tr>
<td>MspaCoveredTransaction</td>
<td>Int(2)</td>
<td>Publisher or Advertiser, as applicable, is a signatory to the IAB Multistate Service Provider Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a &ldquo;Covered Transaction&rdquo; as defined in the MSPA.&nbsp;<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
<tr>
<td>MspaOptOutOptionMode</td>
<td>Int(2)</td>
<td>Publisher or Advertiser, as applicable, has enabled &ldquo;Opt-Out Option Mode&rdquo; for the &ldquo;Covered Transaction,&rdquo; as such terms are defined in the MSPA.<p><code>0</code>  Not Applicable.<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
<tr>
<td>MspaServiceProviderMode</td>
<td>Int(2)</td>
<td>Publisher or Advertiser, as applicable, has enabled &ldquo;Service Provider Mode&rdquo; for the &ldquo;Covered Transaction,&rdquo; as such terms are defined in the MSPA.<p><code>0</code>  Not Applicable<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
</tbody>
</table>
</div>

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
