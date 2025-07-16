<h2>Minnesota Section</h2>
<p>The Minnesota Privacy String consists of the following components. Users should employ the Minnesota Privacy String only if they have determined the Minnesota Consumer Data Privacy Act, Minn. Stat. &sect; 325O.01 et seq (2024), applies to their processing of a consumer&rsquo;s personal data.</p>
<h3><span style="color: rgb(67, 67, 67);">Summary</span></h3>&nbsp;&nbsp;<table style="min-width: 75px;">
    <colgroup>
        <col>
    </colgroup>
    <colgroup>
        <col>
    </colgroup>
    <colgroup>
        <col>
    </colgroup>
    <tbody>
        <tr>
            <td colspan="1" rowspan="1">
                <p><strong>Type</strong></p>
            </td>
            <td colspan="1" rowspan="1">
                <p><strong>Value</strong></p>
            </td>
            <td colspan="1" rowspan="1">
                <p><strong>Description</strong></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>GPP Section ID</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>23</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>The Minnesota Section is registered as Section ID 23 under the GPP.</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>Client side API prefix</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>usmn</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>The Minnesota Privacy Section is registered with client side API prefix &ldquo;usmn&rdquo; in the GPP Client Side API.</p>
            </td>
        </tr>
    </tbody>
</table>
<h3><span style="color: rgb(67, 67, 67);">Section encoding</span></h3>
<p>Note on the JS representation of the section: the field name should be in UpperCamelCase, with exactly the same spelling as the names in column &quot;Field name&quot;. Follow <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding"><span style="color: rgb(17, 85, 204);">this table</span></a> to map the GPP field types to JavaScript native data types. Please refer to the <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-"><span style="color: rgb(17, 85, 204);">PingReturn&apos;s parsedSections object</span></a> for an example.</p>
<h4><span style="color: rgb(102, 102, 102);">Core Subsection</span></h4>
<p>The core sub-section must always be present. Where terms are capitalized in the &lsquo;description&rsquo; field they are defined in Minnesota Consumer Data Privacy Act, Minn. Stat. &sect; 325O.01 et seq (2024). It consists of the following fields:</p>&nbsp;&nbsp;<table style="min-width: 75px;">
    <thead>
        <tr>
            <th colspan="1" rowspan="1">
                <p><strong>Field name</strong></p>
            </th>
            <th colspan="1" rowspan="1">
                <p><strong>GPP Field Type</strong></p>
            </th>
            <th colspan="1" rowspan="1">
                <p><strong>Description</strong></p>
            </th>
        </tr>
    </thead>
    <colgroup>
        <col>
    </colgroup>
    <colgroup>
        <col>
    </colgroup>
    <colgroup>
        <col>
    </colgroup>
    <tbody>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">Version</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(6)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">The version of this section specification used to encode the string.</span></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">ProcessingNotice</span></p>
                <p><br></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">Notice Describing Processing of Personal Data.</span></p>
                <p>0 = Not Applicable, <span style="color: rgb(36, 41, 47);">The Controller does not Process Personal Data</span></p>
                <p>1 = Yes, notice was provided</p>
                <p>2 = No, notice was not provided</p>
                <p><br></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">SaleOptOutNotice</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">Notice of the Opportunity to Opt Out of the Sale of the Consumer&rsquo;s Personal Data</span></p>
                <p><span style="color: rgb(36, 41, 47);">0 = Not Applicable, The Controller does not Sell Personal Data</span></p>
                <p><span style="color: rgb(36, 41, 47);">1 = Yes, notice was provided</span></p>
                <p><span style="color: rgb(36, 41, 47);">2 = No, notice was not provided</span></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">TargetedAdvertisingOptOutNotice</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">Notice of the Opportunity to Opt Out of Processing of the Consumer&rsquo;s Personal Data for Targeted Advertising</span></p>
                <p><span style="color: rgb(36, 41, 47);">0 = Not Applicable, the Controller does not Process Personal Data for Targeted Advertising</span></p>
                <p><span style="color: rgb(36, 41, 47);">1 = Yes, notice was provided</span></p>
                <p><span style="color: rgb(36, 41, 47);">2 = No, notice was not provided</span></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">SaleOptOut</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">Opt-Out of the Sale of the Consumer&rsquo;s Personal Data</span></p>
                <p><span style="color: rgb(36, 41, 47);">0 = Not Applicable, SaleOptOutNotice value was not applicable or no notice was provided</span></p>
                <p><span style="color: rgb(36, 41, 47);">1 = Opted Out</span></p>
                <p><span style="color: rgb(36, 41, 47);">2 = Did Not Opt Out</span></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">TargetedAdvertisingOptOut</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">Opt-Out of Processing the Consumer&rsquo;s Personal Data for Targeted Advertising</span></p>
                <p><span style="color: rgb(36, 41, 47);">0 = Not Applicable, TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided</span></p>
                <p><span style="color: rgb(36, 41, 47);">1 = Opted Out</span></p>
                <p><span style="color: rgb(36, 41, 47);">2 = Did Not Opt Out</span></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">SensitiveDataProcessing</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>N-Bitfield(2,8)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">Two bits for each Category:</span></p>
                <p><span style="color: rgb(36, 41, 47);">0 = Not Applicable, the Controller does not Process the specific category of Sensitive Data</span></p>
                <p><span style="color: rgb(36, 41, 47);">1 = No Consent</span></p>
                <p><span style="color: rgb(36, 41, 47);">2 = Consent</span></p>
                <p><span style="color: rgb(36, 41, 47);">Categories:</span></p>
                <p><span style="color: rgb(36, 41, 47);">(1) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Indicating Racial or Ethnic Origin.</span></p>
                <p><span style="color: rgb(36, 41, 47);">(2) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Indicating Religious Beliefs.</span></p>
                <p><span style="color: rgb(36, 41, 47);">(3) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Indicating a Mental or Physical Health Condition or Diagnosis.</span></p>
                <p><span style="color: rgb(36, 41, 47);">(4) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Indicating Sexual Orientation.</span></p>
                <p><span style="color: rgb(36, 41, 47);">(5) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Personal Data Indicating Citizenship or Immigration Status.</span></p>
                <p><span style="color: rgb(36, 41, 47);">(6) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual.</span></p>
                <p><span style="color: rgb(36, 41, 47);">(7) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual.</span></p>
                <p><span style="color: rgb(36, 41, 47);">(8) Consent to Process the Consumer&rsquo;s Sensitive Data Consisting of Specific Geolocation Data.</span></p>
                <p><br></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">KnownChildSensitiveDataConsents</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(255, 0, 0);">Int(2)</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Consent to process Personal Data from a known Child in accordance with COPPA as required by Minn. Stat. &sect; 325O.07, Subd. 2(d)</p>
                <p><span style="color: rgb(36, 41, 47);">Two bits for each Data Activity:</span></p>
                <p><span style="color: rgb(255, 0, 0);">0 = Not Applicable, the Controller does not Process Sensitive Data of a known Child</span></p>
                <p><span style="color: rgb(255, 0, 0);">1 = No Consent</span></p>
                <p><span style="color: rgb(255, 0, 0);">2 = Consent</span></p>
                <p><br></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">AdditionalDataProcessingConsent</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Consent to Processing of the Consumer&rsquo;s Personal Data that Is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s) for which the Consumer&rsquo;s Personal Data Was Processed</p>
                <p>0 = Not Applicable, the Controller does not Process Personal Data that is Not Reasonably Necessary for nor Compatible with the Disclosed Purpose(s)</p>
                <p>1 = No Consent</p>
                <p>2 = Consent</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">MspaCoveredTransaction</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Publisher or Advertiser, as applicable, is a signatory to the IAB Multi-State Privacy Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a &ldquo;Covered Transaction&rdquo; as defined in the MSPA.</p>
                <p>1 = Yes</p>
                <p>2 = No</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">MspaOptOutOptionMode</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Publisher or Advertiser, as applicable, has enabled &ldquo;Opt-Out Option Mode&rdquo; for the &ldquo;Covered Transaction,&rdquo; as such terms are defined in the MSPA.</p>
                <p>0 = Not Applicable</p>
                <p>1 = Yes</p>
                <p>2 = No</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p><span style="color: rgb(36, 41, 47);">MspaServiceProviderMode</span></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Publisher or Advertiser, as applicable, has enabled &ldquo;Service Provider Mode&rdquo; for the &ldquo;Covered Transaction,&rdquo; as such terms are defined in the MSPA.</p>
                <p>0 = Not Applicable</p>
                <p>1 = Yes</p>
                <p>2 = No</p>
            </td>
        </tr>
    </tbody>
</table>
<h4>GPC Sub-section</h4>
<p><a target="_blank" rel="noopener noreferrer nofollow" href="https://w3c.github.io/gpc/"><span style="color: rgb(17, 85, 204);">GPC</span></a> is signaled in user agent headers (Sec-GPC) and a simple javascript API (globalPrivacyControl). Entities creating GPP strings should check for whether GPC is set and pass along the value they find (from the headers or javascript API) in this sub-section.</p>&nbsp;&nbsp;<table style="min-width: 75px;">
    <colgroup>
        <col>
    </colgroup>
    <colgroup>
        <col>
    </colgroup>
    <colgroup>
        <col>
    </colgroup>
    <tbody>
        <tr>
            <td colspan="1" rowspan="1">
                <p><strong>Field Name</strong></p>
            </td>
            <td colspan="1" rowspan="1">
                <p><strong>GPP Field Type</strong></p>
            </td>
            <td colspan="1" rowspan="1">
                <p><strong>Description</strong></p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>SubsectionType</p>
                <p><br></p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Int(2)</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>0 = Core</p>
                <p>1 = GPC</p>
            </td>
        </tr>
        <tr>
            <td colspan="1" rowspan="1">
                <p>GPCGpc</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>Boolean</p>
            </td>
            <td colspan="1" rowspan="1">
                <p>0 = false</p>
                <p>1 = true</p>
            </td>
        </tr>
    </tbody>
</table>
