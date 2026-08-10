<h1 id="gpp-extension-iab-privacy-s-tennessee-privacy-technical-specification">Tennessee Privacy Technical Specification</h1>
<h2 id="about-this-document">About this document</h2>
<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a> defines a way for local standards to &quot;plug-in&quot; into the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical specification for using the Tennessee section of the GPP specifications.</p>

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
<td>July 2024</td>
<td>1.0</td>
<td>Version 1.0 released</td>
</tr>
</tbody>
</table>
</div>

<h2>Tennessee Section</h2>
<p>The Tennessee Privacy String consists of the following components. Users of the spec should employ the Tennessee Privacy String only if they have determined the Tennessee Information Protection Act, Tenn. Code Ann. 47-18-3301 et seq., applies to their processing of a consumer’s personal information.</p>
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
        <td>22</td>
        <td>The Tennessee Section is registered as Section ID 17 under the GPP.</td>
      </tr>
      <tr>
        <td>Client side API prefix</td>
        <td>ustn</td>
        <td>The Tennessee Privacy Section is registered with client side API prefix “ustn” in the GPP Client Side API.</td>
      </tr>
    </tbody>
  </table>
</div>
<h3>Section encoding</h3>
<p>Note on the JS representation of the section: the field name should be in UpperCamelCase, with exactly the same spelling as the names in column "Field name". Follow <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding" target="_blank" rel="noopener">this table</a> to map the GPP field types to JavaScript native data types. Please refer to the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-" target="_blank" rel="noopener">PingReturn's parsedSections object</a> for an example.<p>
<h4>Core Subsection</h4>
<p>The core subsection must always be present. Where terms are capitalized in the ‘description’ column they are defined in Tenn. Code Ann. 47-18-3301. It consists of the following fields:</p>
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
        <td>The version of this section specification used to encode the string.</td>
      </tr>
      <tr>
        <td><code>ProcessingNotice</code></td>
        <td>Int(2)</td>
        <td>Notice of the Processing of Personal Information.
        <p></p><code>0</code> = Not Applicable, the Controller does not Process Personal Data
        <p></p><code>1</code> = Yes, notice was provided
        <p></p><code>2</code> = No, notice was not provided</td>
      </tr>
      <tr>
        <td><code>SaleOptOutNotice</code></td>
        <td>Int(2)</td>
        <td>Notice of the Opportunity to Opt Out of the Sale of the Consumer’s Personal Information
        <p></p><code>0</code> = Not Applicable, the Controller does not Sell Personal Data
          <p></p><code>1</code> = Yes, notice was provided
          <p></p><code>2</code> = No, notice was not provided
        </td>
      </tr>
      <tr>
        <td><code>TargetedAdvertisingOptOutNotice</code></td>
        <td>Int(2)</td>
        <td>Notice of the Opportunity to Opt Out of Processing of the Consumer’s Personal Information for Targeted Advertising
        <p></p><code>0</code> = Not Applicable, the Controller does not Process Personal Data for Targeted Advertising
          <p></p><code>1</code> = Yes, notice was provided
          <p></p><code>2</code> = No, notice was not provided
        </td>
      </tr>
      <tr>
        <td><code>SaleOptOut</code></td>
        <td>Int(2)</td>
        <td>Opt-Out of the Sale of the Consumer’s Personal Information
        <p></p><code>0</code> = Not Applicable, SaleOptOutNotice value was not applicable or no notice was provided
        <p></p><code>1</code> = Opted Out
        <p></p><code>2</code> = Did Not Opt Out</td>
      </tr>
      <tr>
        <td><code>TargetedAdvertisingOptOut</code></td>
        <td>Int(2)</td>
        <td>Opt-Out of Processing the Consumer’s Personal Information for Targeted Advertising
        <p></p><code>0</code> = Not Applicable, TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided
        <p></p><code>1</code> = Opted Out
        <p></p><code>2</code> = Did Not Opt Out</td>
      </tr>
      <tr>
        <td><code>>SensitiveDataProcessing</code></td>
        <td>N-Bitfield(2,8)</td>
        <td>Two bits for each Data Activity:
        <p></p><code>0</code> = Not Applicable, the Controller does not Process the specific category of Sensitive Data
        <p></p><code>1</code> = No Consent
        <p></p><code>2</code> = Consent
        <p></p>(1) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Information Revealing Racial or Ethnic Origin.><p></p>
          (2) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Information Revealing Religious Beliefs.<p></p>
          (3) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Information Revealing a Mental or Physical Health Diagnosis.<p></p>
          (4) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Information Revealing Sexual Orientation.<p></p>
          (5) Consent to Process the Consumer’s Sensitive Data Consisting of Personal Information Revealing Citizenship or Immigration Status.<p></p>
          (6) Consent to Process the Consumer’s Sensitive Data Consisting of Genetic Data that May Be Processed for the Purpose of Uniquely Identifying an Individual.<p></p>
          (7) Consent to Process the Consumer’s Sensitive Data Consisting of Biometric Data that May Be Processed for the Purpose of Uniquely Identifying an Individual.<p></p>
          (8) Consent to Process the Consumer’s Sensitive Data Consisting of Precise Geolocation Data.<p></p>
        </td>
      </tr>
      <tr>
        <td><code>KnownChildSensitiveDataConsent</code></td>
        <td>Int(2)</td>
        <td>Consent to Process Sensitive Data from a Known Child.
        <p></p><code>0</code> = Not Applicable, the Controller does not Process Sensitive Data of a known Child
        <p></p><code>1</code> = No Consent
        <p></p><code>2</code> = Consent</td>
      </tr>
      <tr>
        <td><code>AdditionalDataProcessingConsent</code></td>
        <td>Int(2)</td>
        <td>Consent to Processing of the Consumer’s Personal Information that Is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s) for which the Consumer’s Personal Information Was Processed
        <p></p><code>0</code> = Not Applicable, the Controller does not Process Personal Data that is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s)
        <p></p><code>1</code> = No Consent
        <p></p><code>2</code> = Consent</td>
         <tr>
        <td><code>MspaCoveredTransaction</code></td>
        <td>Int(2)</td>
        <td><b>Note: As of the Fifth Amended and Restated MSPA, this field should not be used and must always be set to <code>2</code>.</b>
<p>Publisher or Advertiser, as applicable, is a signatory to the IAB Multi-State Privacy Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a “Covered Transaction” as defined in the MSPA.
        <p></p><code>1</code> = Yes
        <p></p><code>2</code> = No</td>
      </tr>
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
<h4>GPC Subsection</h4>
<p><a href="https://w3c.github.io/gpc/" target="_blank" rel="noopener">GPC</a> is signaled in user agent headers<code>(Sec-GPC)</code> and a simple javascript API <code>(globalPrivacyControl)</code>. Entities creating GPP strings should check for whether GPC is set and pass along the value they find (from the headers or javascript API) in this subsection.</p>
<div>
  <table>
    <tbody>
      <tr>
        <td>
          <strong>Field Name</strong>
        </td>
        <td>
          <strong>GPP Field Type</strong>
        </td>
        <td>
          <strong>Description</strong>
        </td>
      </tr>
      <tr>
        <td><code>SubsectionType</code></td>
        <td>Int(2)</td>
        <td><code>1</code> = GPC</td>
      </tr>
      <tr>
        <td><code>Gpc</code></td>
        <td>Boolean</td>
        <td><p></p><code>0</code> = false<p></p><code>1</code> = true</td>
      </tr>
    </tbody>
  </table>
</div>
