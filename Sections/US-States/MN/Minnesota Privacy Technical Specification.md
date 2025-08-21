<h1 id="minnesota-privacy-technical-specification">Minnesota Privacy Technical Specification</h1>
<h2>Overview</h2>
<p>The <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">Global Privacy Protocol (GPP)</a> defines a standardized framework that integrates regional privacy specifications with its core mechanics and client-side API. This document outlines the technical specification for implementing the Minnesota section of the GPP.</p>
<h3>Version History</h3>
<div>
<table>
<tbody>
<tr>
    <td><strong>Date</strong></td>
    <td><strong>Version</strong></td>
    <td><strong>Comments</strong></td>
</tr>
<tr>
<td>August 2025</td>
    <td>1.0</td>
    <td>Version 1.0 released</td>
</tr>
</tbody>
</table>
</div>

<h2>Minnesota Section</h2>
<p>The Minnesota Privacy String consists of the following components. Users should employ the Minnesota Privacy String only if they have determined the Minnesota Consumer Data Privacy Act, Minn. Stat. &sect; 325O.01 et seq (2024), applies to their processing of a consumer's personal data.</p>
<h3>Summary</h3>
<div>
    <table>
        <tr>
            <td><strong>Type</strong></td>
            <td><strong>Value</strong></td>
            <td><strong>Description</strong></td>
        </tr>
        <tr>
            <td>GPP Section ID</td>
            <td>23</td>
            <td>The Minnesota Section is registered as Section ID 23 under the GPP.</td>
        </tr>
        <tr>
            <td>Client side API prefix</td>
            <td>usmn</td>
            <td>The Minnesota Privacy Section is registered with client-side API prefix "usmn" in the GPP Client Side API.</td>
        </tr>
</table>
    </div>

<h3>Section encoding</h3>
<p>Note on the JS representation of the section: the field name should be in UpperCamelCase, with exactly the same spelling as the names in column "Field name". Follow <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding">this table</a> to map the GPP field types to JavaScript native data types. Please refer to the <a target="_blank" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-">PingReturn's parsedSections object</a> for an example.</p>

<h4>Core Subsection</h4>
<p>The core subsection must always be present. Where terms are capitalized in the "description" field they are defined in the Minnesota Consumer Data Privacy Act, Minn. Stat. &sect; 325O.01 et seq (2024). It consists of the following fields:</p>
<table>
    <tr>
        <td><strong>Field name</strong></td>
        <td><strong>GPP Field Type</strong></td>
        <td><strong>Description</strong></td>
    </tr>
    <tr>
        <td>Version</td>
        <td>Int(6)</td>
        <td>The version of this section specification used to encode the string.</td>
    </tr>
    <tr>
        <td>ProcessingNotice</td>
        <td>Int(2)</td>
        <td>
           <p>Notice Describing Processing of Personal Data</p>
            <p><code>0</code> = Not Applicable, The Controller does not Process Personal Data</p>
            <p><code>1</code> = Yes, notice was provided</p>
            <p><code>2</code> = No, notice was not provided</p> 
        </td>
    </tr>
    <tr>
        <td>SaleOptOutNotice</td>
        <td>Int(2)</td>
        <td>
            <p>Notice of the Opportunity to Opt Out of the Sale of the Consumer's Personal Data</p>
            <p><code>0</code> = Not Applicable, The Controller does not Sell Personal Data</p>
            <p><code>1</code> = Yes, notice was provided</p>
            <p><code>2</code> = No, notice was not provided</p>   
        </td>
    </tr>
    <tr>
        <td>TargetedAdvertisingOptOutNotice</td>
        <td>Int(2)</td>
        <td>
            <p>Notice of the Opportunity to Opt Out of Processing of the Consumer's Personal Data for Targeted Advertising</p>
            <p><code>0</code> = Not Applicable, the Controller does not Process Personal Data for Targeted Advertising</p>
            <p><code>1</code> = Yes, notice was provided</p>
            <p><code>2</code> = No, notice was not provided</p>
        </td>
    </tr>
    <tr>
        <td>SaleOptOut</td>
        <td>Int(2)</td>
        <td>
            <p>Opt-Out of the Sale of the Consumer's Personal Data</p>
            <p><code>0</code> = Not Applicable, SaleOptOutNotice value was not applicable or no notice was provided</p>
            <p><code>1</code> = Opted Out</p>
            <p><code>2</code> = Did Not Opt Out</p>
        </td>
    </tr>
    <tr>
        <td>TargetedAdvertisingOptOut</td>
        <td>Int(2)</td>
        <td>
            <p>Opt-Out of Processing the Consumer's Personal Data for Targeted Advertising</p>
            <p><code>0</code> = Not Applicable, TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided></p>
            <p><code>1</code> = Opted Out</p>
            <p><code>2</code> = Did Not Opt Out</p>
        </td>
    </tr>
    <tr>
        <td>SensitiveDataProcessing</td>
        <td>N-Bitfield(2,8)</td>
        <td>
            <p>Two bits for each Category:</p>
            <p><code>0</code> = Not Applicable, the Controller does not Process the specific category of Sensitive Data</p>
            <p><code>1</code> = No Consent</p>
            <p><code>2</code> = Consent</p>
            <br>
            <p>Categories:</p>
            <p>(1) Consent to Process the Consumer's Sensitive Data Consisting of Personal Data Indicating Racial or Ethnic Origin.</p>
            <p>(2) Consent to Process the Consumer's Sensitive Data Consisting of Personal Data Indicating Religious Beliefs.</p>
            <p>(3) Consent to Process the Consumer's Sensitive Data Consisting of Personal Data Indicating a Mental or Physical Health Condition or Diagnosis.</p>
            <p>(4) Consent to Process the Consumer's Sensitive Data Consisting of Personal Data Indicating Sexual Orientation.</p>
            <p>(5) Consent to Process the Consumer's Sensitive Data Consisting of Personal Data Indicating Citizenship or Immigration Status.</p>
            <p>(6) Consent to Process the Consumer's Sensitive Data Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual.</p>
            <p>(7) Consent to Process the Consumer's Sensitive Data Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual.</p>
            <p>(8) Consent to Process the Consumer's Sensitive Data Consisting of Specific Geolocation Data.</p>
        </td>
    </tr>
    <tr>
        <td>KnownChildSensitiveDataConsents</td>
        <td>Int(2)</td>
        <td>
            <p>Consent to process Personal Data from a known Child in accordance with COPPA as required by Minn. Stat. &sect; 325O.07, Subd. 2(d)</p>
            <p><code>0</code> = Not Applicable, the Controller does not Process Sensitive Data of a known Child</p>
            <p><code>1</code> = No Consent</p>
            <p><code>2</code> = Consent</p>
        </td>
    </tr>
    <tr>
        <td>AdditionalDataProcessingConsent</td>
        <td>Int(2)</td>
        <td>
            <p>Consent to Processing of the Consumer's Personal Data that Is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s) for which the Consumer's Personal Data Was Processed</p>
            <p><code>0</code> = Not Applicable, the Controller does not Process Personal Data that is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s)</p>
            <p><code>1</code> = No Consent</p>
            <p><code>2</code> = Consent</p>
        </td>
    </tr>
    <tr>
        <td>MspaCoveredTransaction</td>
        <td>Int(2)</td>
        <td>
            <p>Publisher or Advertiser, as applicable, is a signatory to the <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.iabprivacy.com/#">IAB Multi-State Privacy Agreement (MSPA)</a>, as may be amended from time to time, and declares that the transaction is a "Covered Transaction" as defined in the <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.iabprivacy.com/#">MSPA</a>.</p>
            <p><code>1</code> = Yes</p>
            <p><code>2</code> = No</p>
        </td>
    </tr>
    <tr>
        <td>MspaOptOutOptionMode</td>
        <td>Int(2)</td>
        <td>
            <p>Publisher or Advertiser, as applicable, has enabled "Opt-Out Option Mode" for the "Covered Transaction," as such terms are defined in the <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.iabprivacy.com/#">MSPA</a>.</p>
            <p><code>0</code> = Not Applicable</p>
            <p><code>1</code> = Yes</p>
            <p><code>2</code> = No</p>
        </td>
    </tr>
    <tr>
        <td>MspaServiceProviderMode</td>
        <td>Int(2)</td>
        <td>
            <p>Publisher or Advertiser, as applicable, has enabled "Service Provider Mode" for the "Covered Transaction," as such terms are defined in the <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.iabprivacy.com/#">MSPA</a>.</p>
            <p><code>0</code> = Not Applicable</p>
            <p><code>1</code> = Yes</p>
            <p><code>2</code> = No</p>
        </td>
    </tr>
    
</table>

<h4>GPC Subsection</h4>
<p><a target="_blank" rel="noopener noreferrer nofollow" href="https://w3c.github.io/gpc/">GPC</a> is signaled in user agent headers (Sec-GPC) and a simple javascript API (globalPrivacyControl). Entities creating GPP strings should check for whether GPC is set and pass along the value they find (from the headers or javascript API) in this subsection.</p>

<table>
    <tr>
        <td><strong>Field Name</strong></td>
        <td><strong>GPP Field Type</strong></td>
        <td><strong>Description</strong></td>
    </tr>
    <tr>
        <td>SubsectionType</td>
        <td>Int(2)</td>
        <td>
           <p><code>0</code> = Core</p>
            <p><code>1</code> = GPC</p>
        </td>
    </tr>
    <tr>
        <td>Gpc</td>
        <td>Boolean</td>
        <td>
            <p><code>0</code> = false</p>
            <p><code>1</code> = true</p>
        </td>
    </tr>
</table>
