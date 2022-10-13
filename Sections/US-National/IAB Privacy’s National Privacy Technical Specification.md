<h1 id="gpp-extension-iab-privacy-s-national-privacy-technical-specification">GPP Extension: IAB Privacy’s National Privacy Technical Specification</h1>

<h2 id="about-this-document">About this document</h2>

<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a> defines a way for local standards to &quot;plug-in&quot; into the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20specification">GPP client side API</a>. This document outlines the technical specification for using the GPP specifications with the IAB Privacy Multi-State Privacy Agreement legal requirements.</p>

<h2>National Privacy Section</h2>
<p style="text-align: justify;">The National Privacy Section is a string that consists of the following components. Users should employ the National Privacy Section only if they will adhere to the National Approach for their processing of a consumer&rsquo;s personal data.</p>
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
<td>uspnat</td>
<td>The National Privacy section is registered with client side API prefix &ldquo;uspnat&rdquo; in the GPP Client Side API.</td>
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
<td><span style="color: #24292f;">Version</span></td>
<td>Int(6)</td>
<td><span style="color: #24292f;">The version of this section specification used to encode the string.</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">SharingNotice</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Notice of the Sharing of the Consumer&rsquo;s Personal Data with Third Parties.&nbsp;</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Virginia Code 59.1-578(C)(4) &ndash; (5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(1)(1)(IV) &ndash; (V)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(1)(1)(iv) &ndash; (v)</span></li>
<li><span style="color: #24292f;">Conn. PA No. 22-15, Sec. 6(3)(4)-(5)</span></li>
</ul>
<code>0</code>  Not Applicable<span style="color: #24292f;">. The Business does not share Personal Data with Third Parties.</span><span style="color: #24292f;"><p><code>1</code>  Yes, notice was provided</span><span style="color: #24292f;"><p><code>2</code>  No, notice was not provided</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">SaleOptOutNotice</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Notice of the Opportunity to Opt Out of the Sale of the Consumer&rsquo;s Personal Data.</span><span style="color: #24292f;"><p><p>References:&nbsp;</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(1)(1), (3), Cal. Civ. Code 1798.135(1), and/or Cal. Civ. Code 1798.135(2), and rules promulgated thereunder.</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(D)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat 6-1-1308(1)(2) and Colo. Rev. Stat. 6-1-1306(1)(1)(III)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(1)(2)(i)</span></li>
<li><span style="color: #24292f;">Conn. PA No. 22-15, Sec. 6(4) and Conn. PA No. 22-15, Sec. 4(2)</span></li>
</ul>
<code>0</code>  Not Applicable<span style="color: #24292f;">. </span>The <span style="color: #24292f;">Business does not Sell Personal Data.</span><span style="color: #24292f;"><p><code>1</code>  Yes, notice was provided</span><span style="color: #24292f;"><p><code>2</code>  No, notice was not provided</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">SharingOptOutNotice</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Notice of the Opportunity to Opt Out of the Sharing of the Consumer&rsquo;s Personal Data.</span><span style="color: #24292f;"><p><p>References:&nbsp;</span><span style="color: #24292f;">(i) Cal. Civ. Code 1798.100(1)(1), (3), (ii) Cal. Civ. Code 1798.135(1) and/or (iii) Cal. Civ. Code 1798.135(2)&nbsp;</span><code>0</code>  Not Applicable<span style="color: #24292f;">.</span>T<span style="color: #24292f;">he Business does not Share Personal Data.</span><span style="color: #24292f;"><p><code>1</code>  Yes, notice was provided</span><span style="color: #24292f;"><p><code>2</code>  No, notice was not provided</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">TargetedAdvertisingOptOutNotice</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Notice of the Opportunity to Opt Out of Processing of the Consumer&rsquo;s Personal Data for Targeted Advertising</span><span style="color: #24292f;"><p><p>References:&nbsp;</span>
<ul>
<li><span style="color: #24292f;">Virginia Code 59.1-578(D)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat 6-1-1308(1)(2) and Colo. Rev. Stat. 6-1-1306(1)(1)(III)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(1)(2)(ii)</span></li>
<li><span style="color: #24292f;">Conn. PA No. 22-15, Sec. 6(4) and Conn. PA No. 22-15, Sec. 4(2)</span></li>
</ul>
<code>0</code>  Not Applicable<span style="color: #24292f;">.The Business does not Process Personal Data for Targeted Advertising.</span><span style="color: #24292f;"><p><code>1</code>  Yes, notice was provided</span><span style="color: #24292f;"><p><code>2</code>  No, notice was not provided</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">SensitiveDataProcessingOptOutNotice</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Notice of the Opportunity to Opt Out of the Processing of the Consumer&rsquo;s Sensitive Data</span><span style="color: #24292f;"><p><p>References:&nbsp;</span>
<ul>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(1)</span></li>
</ul>
<code>0</code>  Not Applicable<span style="color: #24292f;">.</span> The<span style="color: #24292f;"> Business does not Process Sensitive Data.</span><span style="color: #24292f;"><p><code>1</code>  Yes, notice was provided</span><span style="color: #24292f;"><p><code>2</code>  No, notice was not provided</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">SensitiveDataLimitUseNotice</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Notice of the Opportunity to Limit Use or Disclosure of the Consumer&rsquo;s Sensitive Data</span><span style="color: #24292f;"><p><p>References:&nbsp;</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(1)(2)-(3), (ii) Cal. Civ. Code 1798.135(1), and/or (iii) Cal. Civ. Code 1798.135(2) and rules promulgated thereunder</span></li>
</ul>
<code>0</code>  Not Applicable<span style="color: #24292f;">.</span> The<span style="color: #24292f;"> Business does not use or disclose Sensitive Data.</span><span style="color: #24292f;"><p><code>1</code>  Yes, notice was provided</span><span style="color: #24292f;"><p><code>2</code>  No, notice was not provided</span></td>
</tr>
<tr>
<td><span style="color: #24292f;">SaleOptOut</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Opt-Out of the Sale of the Consumer&rsquo;s Personal Data</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.135(1) and/or 1798.135(2)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(D)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1306(1)(1)(III) or 6-1-1306(1)(1)(IV)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(1)(2)(i)</span></li>
<li><span style="color: #24292f;">Conn. PA No. 22-15, Sec. 4(5)(i) or (ii)</span></li>
</ul>
<code>0</code>  Not Applicable. SaleOptOutNotice value was not applicable or no notice was provided<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td><span style="color: #24292f;">SharingOptOut</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Opt-Out of the Sharing of the Consumer&rsquo;s Personal Data</span><span style="color: #24292f;"><p><p>References:&nbsp;</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.120(1) using a method that adheres to Cal. Civ. Code 1798.135(1) and/or 1798.135(2)</span></li>
</ul>
<code>0</code>  Not Applicable. SharingOptOutNotice value was not applicable or no notice was provided.<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td><span style="color: #24292f;">TargetedAdvertisingOptOut</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Opt-Out of Processing the Consumer&rsquo;s Personal Data for Targeted Advertising</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Virginia Code 59.1-578(D)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1306(1)(1)(III) or 6-1-1306(1)(1)(IV)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(1)(2)(ii)</span></li>
<li><span style="color: #24292f;">Conn. PA No. 22-15, Sec. 4(5)(i) or (ii)</span></li>
</ul>
<code>0</code>  Not Applicable. TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td><span style="color: #24292f;">SensitiveDataProcessing</span></td>
<td>N-Bitfield(2,12)</td>
<td>Two bits for each Data Activity:<code>0</code>  Not Applicable. The Business does not Process the specific category of Sensitive Data.<p><code>1</code>  Consent<p><code>2</code>  No Consent&nbsp;<span style="color: #24292f;">(1). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Racial or Ethnic Origin.&nbsp;</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(2). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Religious or Philosophical Beliefs.&nbsp;</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(3). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Concerning a Consumer&rsquo;s Health (including a Mental or Physical Health Condition or Diagnosis; Medical History; or Medical Treatment or Diagnosis by a Health Care Professional).</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(4). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Sex Life or Sexual Orientation.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(5). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Revealing Citizenship or Immigration Status.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(6). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual / Natural Person.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(7). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual / Natural Person.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. </span>Code<span style="color: #24292f;"> 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(8). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Precise Geolocation Data.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(9). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of a Consumer&rsquo;s Social Security, Driver&rsquo;s License, State Identification Card, or Passport Number.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
</ul>
<span style="color: #24292f;">(10). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of a Consumer&rsquo;s Account Log-In, Financial Account, Debit Card, or Credit Card Number in Combination with Any Required Security or Access Code, Password, or Credentials Allowing Access to an Account.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
</ul>
(11). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Union Membership.<span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
</ul>
<span style="color: #24292f;">(12). Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of the contents of a Consumer&rsquo;s Mail, Email, and Text Messages unless You Are the Intended Recipient of the Communication.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code 1798.100(a)(2), 1798.121(a), and 1798.135(a)</span></li>
</ul>
</td>
</tr>
<tr>
<td><span style="color: #24292f;">KnownChildSensitiveDataConsents</span></td>
<td>N-Bitfield(2,2)</td>
<td>Two bits for each Data Activity:<code>0</code>  Not Applicable. The Business does not have <span style="color: #24292f;">actual knowledge that it Processes Personal Data or Sensitive Data of a Consumer who is a known child.</span><p><code>1</code>  Consent<p><code>2</code>  No Consent&nbsp;<span style="color: #24292f;">(1). Consent to Process the Consumer&rsquo;s Personal Data or Sensitive Data for Consumers from Age 13 to 16.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code Cal. Civ. Code 1798.120(c)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
<span style="color: #24292f;">(2). Consent to Process the Consumer&rsquo;s Personal Data or Sensitive Data for Consumers Younger Than 13 Years of Age.</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">Cal. Civ. Code Cal. Civ. Code 1798.120(c)</span></li>
<li><span style="color: #24292f;">Virginia Code 59.1-578(A)(5)</span></li>
<li><span style="color: #24292f;">Colo. Rev. Stat. 6-1-1308(7)</span></li>
<li><span style="color: #24292f;">Utah Code 13-61-302(3)(a)</span></li>
<li><span style="color: #24292f;">Conn. PA 22-15, Sec. 6(a)(4)</span></li>
</ul>
</td>
</tr>
<tr>
<td><span style="color: #24292f;">PersonalDataConsents</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Consent to Collection, Use, Retention, Sale, and/or Sharing of the Consumer&rsquo;s Personal Data that Is Unrelated to or Incompatible with the Purpose(s) for which the Consumer&rsquo;s Personal Data Was Collected or Processed&nbsp;</span><span style="color: #24292f;"><p><p>References:</span>
<ul>
<li><span style="color: #24292f;">&nbsp;Cal. Civ. Code 1798.100(c)&nbsp;</span></li>
</ul>
<code>0</code>  Not Applicable. <span style="color: #24292f;">The Business does not use, retain, Sell, or Share the Consumer&rsquo;s Personal Data for advertising purposes that are unrelated to or incompatible with the purpose(s) for which the Consumer&rsquo;s Personal Data was collected or processed.</span><p><code>1</code>  Consent<p><code>2</code>  No Consent&nbsp;</td>
</tr>
<tr>
<td><span style="color: #24292f;">MspaCoveredTransaction</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Publisher or Advertiser, as applicable, is a signatory to the IAB Multistate Service Provider Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a &ldquo;Covered Transaction&rdquo; as defined in the MSPA.&nbsp;</span><code>0</code>  Not Applicable<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
<tr>
<td><span style="color: #24292f;">MspaOptOutOptionMode</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Publisher or Advertiser, as applicable, has enabled &ldquo;Opt-Out Option Mode&rdquo; for the &ldquo;Covered Transaction,&rdquo; as such terms are defined in the MSPA.</span><code>0</code>  Not Applicable.<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
<tr>
<td><span style="color: #24292f;">MspaServiceProviderMode</span></td>
<td>Int(2)</td>
<td><span style="color: #24292f;">Publisher or Advertiser, as applicable, has enabled &ldquo;Service Provider Mode&rdquo; for the &ldquo;Covered Transaction,&rdquo; as such terms are defined in the MSPA.</span><code>0</code>  Not Applicable<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
</tbody>
</table>
</div>
<h4>GPC Segment</h4>
<div>
<table>
<tbody>
<tr>
<td><strong>Field Name</strong></td>
<td><strong>GPP Field Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td>Gpc</td>
<td>Boolean</td>
<td><code>0</code>  false<p><code>1</code>  true</td>
</tr>
</tbody>
</table>
</div>
<h3>Client side API</h3>
<h4>Key Names</h4>
<p>In the mobile or CTV context, the key names to be used in GPP are listed below.</p>
<div>
<table>
<tbody>
<tr>
<td><strong>GPP Key Name</strong></td>
<td><strong>Value(s)</strong></td>
</tr>
<tr>
<td><span style="color: #24292f;">IABGPP_7_String</span></td>
<td>String: Full encoded USPNAT string</td>
</tr>
</tbody>
</table>
</div>
