<h1 id="gpp-extension-iab-privacy-s-florida-privacy-technical-specification">Florida Privacy Technical Specification</h1>
<h2 id="about-this-document">About this document</h2>
<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a> defines a way for local standards to &quot;plug-in&quot; into the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical specification.</p>

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
<td>August 2026 (<i>Public Comment</i>)</td>
<td>1.0</td>
<td>Updated guidance on usage of MSPA-specific fields in accordance with the Fifth Amended and Restated MSPA</td>
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
<p>The Florida Privacy String consists of the following components. Users of the spec should employ the Florida Privacy String if they have determined the Florida Digital Bill of Rights, Fla. Stat. § 501.701 et seq., may apply to their processing or their partners’ processing of a consumer's personal data.</p>
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
<p>Note on the JS representation of the section: the field name should be in UpperCamelCase, with exactly the same spelling as the names in column "Field name". Follow <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding" target="_blank" rel="noopener">this table</a> to map the GPP field types to JavaScript native data types. Please refer to the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-" target="_blank" rel="noopener">PingReturn's parsedSections object</a> for an example.<p>
<h4>Core Subsection</h4>
<p>The core subsection must always be present. Where terms are capitalized in the ‘description’ column they are defined terms in Fla. Stat. § 501.702. It consists of the following fields:</p>
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
        <td><code>Version</code></td>
        <td>Int(6)</td>
        <td>The version of this section specification used to encode the string. </td>
      </tr>
      <tr>
        <td><code>ProcessingNotice</code></td>
        <td>Int(2)</td>
        <td>Notice of the Processing of Personal Data.
        <p></p><code>0</code> = Not Applicable, The Controller does not Process Personal Data
        <p></p><code>1</code> = Yes, notice was provided
        <p></p><code>2</code> = No, notice was not provided</td>
      </tr>
      <tr>
        <td><code>SaleOptOutNotice</code></td>
        <td>Int(2)</td>
        <td>Notice of the Opportunity to Opt Out of the Sale of the Consumer’s Personal Data
        <p></p><code>0</code> = Not Applicable, The Controller does not Sell Personal Data
        <p></p><code>1</code> = Yes, notice was provided
        <p></p><code>2</code> = No, notice was not provided
        </td>
      </tr>
      <tr>
        <td><code>TargetedAdvertisingOptOutNotice</code></td>
        <td>Int(2)</td>
        <td>Notice of the Opportunity to Opt Out of Processing of the Consumer’s Personal Data for Targeted Advertising
        <p></p><code>0</code> = Not Applicable, the Controller does not Process Personal Data for Targeted Advertising
        <p></p><code>1</code> = Yes, notice was provided
        <p></p><code>2</code> = No, notice was not provided
        </td>
      </tr>
      <tr>
        <td><code>SaleOptOut</code></td>
        <td>Int(2)</td>
        <td>Opt-Out of the Sale of the Consumer’s Personal Data
        <p></p><code>0</code> = Not Applicable, SaleOptOutNotice value was not applicable or no notice was provided
        <p></p><code>1</code> = Opted Out
        <p></p><code>2</code> = Did Not Opt Out</td>
      </tr>
      <tr>
        <td><code>TargetedAdvertisingOptOut</code></td>
        <td>Int(2)</td>
        <td>Opt-Out of Processing the Consumer’s Personal Data for Targeted Advertising
        <p></p><code>0</code> = Not Applicable, TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided
        <p></p><code>1</code> = Opted Out
        <p></p><code>2</code> = Did Not Opt Out</td>
      </tr>
      <tr>
        <td><code>SensitiveDataProcessing</code></td>
        <td>N-Bitfield(2,8)</td>
        <td>Two bits for each Data Activity:
        <p></p><code>0</code> = Not Applicable, the Controller does not Process the specific category of Sensitive Data
        <p></p><code>1</code> = No Consent 
        <p></p><code>2</code> = Consent
        <p></p>(1) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Racial or Ethnic Origin.<p></p>
          (2) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Religious Beliefs.<p></p>
          (3) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing a Mental or Physical Health Diagnosis.<p></p>
          (4) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Sexual Orientation.<p></p>
          (5) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Citizenship or Immigration Status.<p></p>
          (6) Consent to Process the Consumer’s Sensitive Data Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual.<p></p>
          (7) Consent to Process the Consumer’s Sensitive Data Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual.<p></p>
          (8) Consent to Process the Consumer’s Sensitive Data Consisting of Precise Geolocation Data.
        </td>
      </tr>
      <tr>
        <td><code>KnownChildSensitiveDataConsents</code></td>
        <td>N-Bitfield(2,3)</td>
        <td>Two bits for each Data Activity:
        <p></p><code>0</code> = Not Applicable, the Controller does not Process Sensitive Data of a known Child
        <p></p><code>1</code> = No Consent 
        <p></p><code>2</code> = Consent
        ><p></p>(1) Consent to Process Sensitive Data from a Known Child Under the Age of 13.
        <p></p>(2) Consent to Process Sensitive Data of Consumers At Least 13 Years of Age but Younger Than 16 Years of Age.
        <p></p>(3) Consent to Process the Sensitive Data of Consumers At Least 16 Years of Age but Younger Than 18 Years of Age.<p></p>
        </td>
      </tr>
      <tr>
        <td><code>AdditionalDataProcessingConsent</code></td>
        <td>Int(2)</td>
        <td>Consent to Processing of the Consumer’s Personal Data that Is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s) for which the Consumer’s Personal Data Was Processed
        <p></p><code>0</code> = Not Applicable, the Controller does not Process Personal Data that is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s)
        <p></p><code>1</code> = No Consent 
        <p></p><code>2</code> = Consent</td>
      </tr>
      <tr>
        <td><code>MspaCoveredTransaction</code></td>
        <td>Int(2)</td>
        <td><b>Note: As of the Fifth Amended and Restated MSPA, this field should not be used and must always be set to <code>2</code>.</b>
<p>Publisher or Advertiser, as applicable, is a signatory to the IAB Multi-State Privacy Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a “Covered Transaction” as defined in the MSPA.
        <p></p><code>1</code> = Yes
        <p></p><code>2</code> = No</td>
      </tr>
      <tr>
        <td><code>MspaOptOutOptionMode</code></td>
        <td>Int(2)</td>
        <td><b>Note: As of the Fifth Amended and Restated MSPA, this field should not be used and must always be set to <code>0</code>.</b>
<p>Publisher or Advertiser, as applicable, has enabled “Opt-Out Option Mode” for the “Covered Transaction,” as such terms are defined in the MSPA.
        <p></p><code>0</code> = Not Applicable
        <p></p><code>1</code> = Yes
        <p></p><code>2</code> = No</td>
      </tr>
      <tr>
        <td><code>MspaServiceProviderMode</code></td>
        <td>Int(2)</td>
        <td><b>Note: As of the Fifth Amended and Restated MSPA, this field should not be used and must always be set to <code>0</code>.</b>
<p>Publisher or Advertiser, as applicable, has enabled “Service Provider Mode” for the “Covered Transaction,” as such terms are defined in the MSPA.
        <p></p><code>0</code> = Not Applicable
        <p></p><code>1</code> = Yes
        <p></p><code>2</code> = No</td>
      </tr>
    </tbody>
  </table>
</div>
