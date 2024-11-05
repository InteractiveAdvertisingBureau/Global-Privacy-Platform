<h1 id="gpp-extension-iab-privacy-s-new-jersey-privacy-technical-specification">GPP Extension: IAB Privacy’s New Jersey Privacy Technical Specification</h1>
<h2 id="about-this-document">About this document</h2>
<p>The global standard <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a> defines a way for local standards to &quot;plug-in&quot; into the existing mechanics defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical specification for using the New Jersey section of the GPP specifications in accordance with the IAB Privacy Multi-State Privacy Agreement legal requirements, applicable to both Signatories and non-Signatories of the MSPA.</p>

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
<td>July 2024</td>
<td>1.0</td>
<td>Version 1.0 released</td>
</tr>
</tbody>
</table>
</div>

<h2>New Jersey Section</h2>
<p>The New Jersey Privacy String consists of the following components. Users of the spec should employ the New Jersey Privacy String only if they have determined the New Jersey Act Concerning Online Services, Consumers, and Personal Data, P.L. 2023, c. 266, applies to their processing of a consumer’s personal data.</p>
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
        <td>21</td>
        <td>The New Jersey Section is registered as Section ID 21 under the GPP.</td>
      </tr>
      <tr>
        <td>Client side API prefix</td>
        <td>usnj</td>
        <td>The New Jersey Privacy Section is registered with client side API prefix “usnj” in the GPP Client Side API.</td>
      </tr>
    </tbody>
  </table>
</div>
<h3>Section encoding</h3>
<p>Note on the JS representation of the section: the field name should be in UpperCamelCase, with exactly the same spelling as the names in column "Field name". Follow <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding" target="_blank" rel="noopener">this table</a> to map the GPP field types to JavaScript native data types. Please refer to the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-" target="_blank" rel="noopener">PingReturn's parsedSections object</a> for an example.<p>
<h4>Core Segment</h4>
<p>The core sub-section must always be present. Where terms are capitalized in the ‘description’ field they are defined in the New Jersey Act Concerning Online Services, Consumers, and Personal Data, P.L. 2023, c. 266. It consists of the following fields:</p>
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
          <span style="color:rgb(36, 41, 47);">the Controller does not Process Personal Data</span><p></p><code>1</code> = Yes, notice was provided<p></p><code>2</code> = No, notice was not provided</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">SaleOptOutNotice</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Notice of the Opportunity to Opt Out of the Sale of the Consumer’s Personal Data&nbsp;</span><p></p><code>0</code> = Not Applicable<span style="color:rgb(36, 41, 47);">,
          </span>the
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
        <td>N-Bitfield(2,10)</td>
        <td>Two bits for each Data Activity:<p></p><code>0</code> = Not Applicable, the Controller does not Process the specific category of Sensitive Data<p></p><code>1</code> = No Consent<p></p><code>2</code> = Consent&nbsp;<span style="color:rgb(36, 41, 47);"><p></p>(1). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Racial or Ethnic Origin.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(2). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Religious Beliefs.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(3). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing a Mental or Physical Health Condition, Treatment, or Diagnosis.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(4). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Sex Life or Sexual Orientation.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(5). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Citizenship or Immigration Status.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(6). Consent to Process the Consumer’s Sensitive Data Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(7). Consent to Process the Consumer’s Sensitive Data Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(8). Consent to Process the Consumer’s Sensitive Data Consisting of Precise Geolocation Data.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(9). Consent to Process the Consumer’s Sensitive Data Consisting of Personal Data Revealing Status as Transgender or Nonbinary.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(10). Consent to Process the Consumer’s Sensitive Data Consisting of Financial Information, in Combination with any Required Security Code, Access Code, or Password that Would Permit Access to a Consumer’s Financial Account.</span><p></p>
        </td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">KnownChildSensitiveDataConsents</span>
        </td>
        <td>N-Bitfield(2,5)</td>
        <td>Two bits for each Data Activity:<p></p><code>0</code> = Not Applicable, the Controller does not
          <span style="color:rgb(36, 41, 47);">Process Sensitive Data of a known Child</span><p></p><code>1</code> = No Consent<p></p><code>2</code> = Consent&nbsp;<span style="color:rgb(36, 41, 47);"><p></p>(1). Consent to Process Sensitive Data from a Known Child.</span>
          <span style="color:rgb(36, 41, 47);">(2). Consent to Sell the Personal Data of Consumers At Least 13 Years of Age but Younger Than 16 Years of Age.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(3). Consent to Process the Personal Data of Consumers At Least 13 Years of Age but Younger Than 16 Years of Age for Purposes of Targeted Advertising.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(4). Consent to Sell the Personal Data of Consumers At Least 16 Years of Age but Younger Than 17 Years of Age.</span><p></p>
          <span style="color:rgb(36, 41, 47);">(5). Consent to Process the Personal Data of Consumers At Least 16 Years of Age but Younger Than 17 Years of Age for Purposes of Targeted Advertising.</span><p></p>
        </td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">AdditionalDataProcessingConsent</span>
        </td>
        <td>Int(2)</td>
        <td>Consent to Processing of the Consumer’s Personal Data that Is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s) for which the Consumer’s Personal Data Was Processed<p></p><code>0</code> = Not Applicable, the Controller does not Process Personal Data that is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s)<p></p><code>1</code> = No Consent<p></p><code>2</code> = Consent&nbsp;</td>
      </tr>
      <tr>
        <td>
          <span style="color:rgb(36, 41, 47);">MspaCoveredTransaction</span>
        </td>
        <td>Int(2)</td>
        <td>
          <span style="color:rgb(36, 41, 47);">Publisher or Advertiser, as applicable, is a signatory to the IAB Multi-State Privacy Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a “Covered Transaction” as defined in the MSPA.&nbsp;</span><p></p><code>1</code> = Yes<p></p><code>2</code> = No</td>
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
<h4>GPC Sub-section</h4>
<p>
  <a target="_blank" href="https://globalprivacycontrol.github.io/gpc-spec/">
    <span style="color:rgb(17, 85, 204);">GPC</span>
  </a>
  <span style="color:rgb(36, 41, 47);">
    is signaled in user agent headers
  </span>
  <span style="color:rgb(36, 41, 47);">(Sec-GPC)</span>
  <span style="color:rgb(36, 41, 47);">
    and a simple javascript API
  </span>
  <span style="color:rgb(36, 41, 47);">(globalPrivacyControl)</span>
  <span style="color:rgb(36, 41, 47);">. Entities creating GPP strings should check for whether GPC is set and pass along the value they find (from the headers or javascript API) in this sub-section.</span>
</p>
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
        <td>SubsectionType</td>
        <td>Int(2)</td>
        <td><p></p><code>0</code> = Core<p></p><code>1</code> = GPC</td>
      </tr>
      <tr>
        <td>Gpc</td>
        <td>Boolean</td>
        <td><p></p><code>0</code> = false<p></p><code>1</code> = true</td>
      </tr>
    </tbody>
  </table>
</div>
