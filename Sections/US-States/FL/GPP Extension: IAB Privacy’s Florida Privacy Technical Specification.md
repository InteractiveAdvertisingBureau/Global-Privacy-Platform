<h1 id="gpp-extension-iab-privacy-s-florida-privacy-technical-specification">GPP Extension: IAB Privacy’s Florida Privacy Technical Specification</h1>
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
<td>May 2024</td>
<td>1.0</td>
<td>Version 1.0 released</td>
</tr>
</tbody>
</table>
</div>

<h2>Florida Section</h2>
<p>The Florida Privacy String consists of the following components. Users should employ the Florida Privacy String only if they have determined the Florida Digital Bill of Rights, Fla. Stat. § 501.701 et seq., applies to their processing of a consumer’s personal data.</p>
<h3>Summary</h3>
<div>
  <table>
    <tbody>
      <tr>
        <td>
          <strong>Type</strong>
        </td>
        <td>
          <strong>Value</strong>
        </td>
        <td>
          <strong>Description</strong>
        </td>
      </tr>
      <tr>
        <td>GPP Section ID</td>
        <td>13</td>
        <td>The Florida Section is registered as Section ID 13 under the GPP.</td>
      </tr>
      <tr>
        <td>Client side API prefix</td>
        <td>usfl</td>
        <td>The Florida Privacy Section is registered with client side API prefix “usfl” in the GPP Client Side API.</td>
      </tr>
    </tbody>
  </table>
</div>
<h3>Section encoding</h3>
<h4>Core Segment</h4>
<p>The core sub-section must always be present. Where terms are capitalized in the ‘description’ field they are defined terms in Fla. Stat. § 501.702. It consists of the following fields:</p>
<div>
  <table>
    <thead>
      <tr>
        <th>
          <p>Field name</p>
        </th>
        <th>
          <p>GPP Field Type</p>
        </th>
        <th>
          <p>Description</p>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">Version</span>
        </td>
        <td>Int(6)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">The version of this section specification used to encode the string.</span>
        </td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">ProcessingNotice</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Notice of the Processing of Personal Data.</span><p></p><code>0</code> = Not Applicable,
          <span style="color:rgb(36, 41, 47);">The Controller does not Process Personal Data</span><p></p><code>1</code> = Yes, notice was provided<p></p><code>2</code> = No, notice was not provided</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">SaleOptOutNotice</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Notice of the Opportunity to Opt Out of the Sale of the Consumer’s Personal Data&nbsp;</span><p></p><code>0</code> = Not Applicable<span style="color:rgb(36, 41, 47);">,
          </span>The
          <span style="color:rgb(36, 41, 47);">Controller does not Sell Personal Data</span>
          <span style="color:rgb(36, 41, 47);"><p></p><code>1</code> = Yes, notice was provided</span>
          <span style="color:rgb(36, 41, 47);"><p></p><code>2</code> = No, notice was not provided</span>
        </td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">TargetedAdvertisingOptOutNotice</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Notice of the Opportunity to Opt Out of Processing of the Consumer’s Personal Data for Targeted Advertising</span><p></p><code>0</code> = Not Applicable<span style="color:rgb(36, 41, 47);">, the Controller does not Process Personal Data for Targeted Advertising</span>
          <span style="color:rgb(36, 41, 47);"><p></p><code>1</code> = Yes, notice was provided</span>
          <span style="color:rgb(36, 41, 47);"><p></p><code>2</code> = No, notice was not provided</span>
        </td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">SaleOptOut</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Opt-Out of the Sale of the Consumer’s Personal Data</span><p></p><code>0</code> = Not Applicable, SaleOptOutNotice value was not applicable or no notice was provided<p></p><code>1</code> = Opted Out<p></p><code>2</code> = Did Not Opt Out</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">TargetedAdvertisingOptOut</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Opt-Out of Processing the Consumer’s Personal Data for Targeted Advertising</span><p></p><code>0</code> = Not Applicable, TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided<p></p><code>1</code> = Opted Out<p></p><code>2</code> = Did Not Opt Out</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">SensitiveDataProcessing</span>
        </td>
        <td>Bitfield(16)</td>
        <td>Two bits for each Data Activity:<p></p><code>0</code> = Not Applicable, the Controller does not Process the specific category of Sensitive Data<p></p><code>1</code> = Consent <p></p><code>2</code> = No Consent&nbsp;<span style="color:rgb(36, 41, 47);"><p></p>(1). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Racial or Ethnic Origin.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(2). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Religious Beliefs.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(3). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing a Mental or Physical Health Diagnosis.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(4). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Sexual Orientation.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(5). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Citizenship or Immigration Status.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(6). Consent to Process the Consumer’s Sensitive Data Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(7). Consent to Process the Consumer’s Sensitive Data Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(8). Consent to Process the Consumer’s Sensitive Data Consisting of Precise Geolocation Data.</span>
        </td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">KnownChildSensitiveDataConsents</span>
        </td>
        <td>Bitfield(6)</td>
        <td>Two bits for each Data Activity:<p></p><code>0</code> = Not Applicable, the Controller does not
          <span style="color:rgb(36, 41, 47);">Process Sensitive Data of a known Child</span><p></p><code>1</code> = Consent <p></p><code>2</code> = No Consent&nbsp;<span style="color:rgb(36, 41, 47);"><p></p>(1). Consent to Process Sensitive Data from a Known Child Under the Age of 13.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(2). Consent to Process Sensitive Data of Consumers At Least 13 Years of Age but Younger Than 16 Years of Age.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(3). Consent to Process the Sensitive Data of Consumers At Least 16 Years of Age but Younger Than 18 Years of Age.</span><p></p>
        </td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">AdditionalDataProcessingConsent</span>
        </td>
        <td>Int(2)</td>
        <td>Consent to Processing of the Consumer’s Personal Data that Is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s) for which the Consumer’s Personal Data Was Processed<p></p><code>0</code> = Not Applicable, the Controller does not Process Personal Data that is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s)<p></p><code>1</code> = Consent <p></p><code>2</code> = No Consent&nbsp;</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">MspaCoveredTransaction</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Publisher or Advertiser, as applicable, is a signatory to the IAB Multistate Service Provider Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a “Covered Transaction” as defined in the MSPA.&nbsp;</span><p></p><code>0</code> = Not Applicable<p></p><code>1</code> = Yes<p></p><code>2</code> = No</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">MspaOptOutOptionMode</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Publisher or Advertiser, as applicable, has enabled “Opt-Out Option Mode” for the “Covered Transaction,” as such terms are defined in the MSPA.</span><p></p><code>0</code> = Not Applicable<p></p><code>1</code> = Yes<p></p><code>2</code> = No</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">MspaServiceProviderMode</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Publisher or Advertiser, as applicable, has enabled “Service Provider Mode” for the “Covered Transaction,” as such terms are defined in the MSPA.</span><p></p><code>0</code> = Not Applicable<p></p><code>1</code> = Yes<p></p><code>2</code> = No</td>
      </tr>
    </tbody>
  </table>
</div>
