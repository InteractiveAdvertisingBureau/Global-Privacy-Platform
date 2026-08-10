
<h1 id="gpp-extension-iab-privacy-s-mspa-us-national-privacy-technical-specification">GPP Extension: IAB Privacy’s MSPA US National Section Technical Specification</h1>

<h2 id="about-this-document">About this document</h2>

<p>The <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a>  standard is designed to be extensible so that support for new regulations can be added without the need to update existing capabilities defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical requirements for using the GPP specification with the IAB Privacy Multi-State Privacy Agreement (MSPA) legal requirements.</p>

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
<td>August 2026 <i>(Public Comment)</i></td>
<td>3.0</td>
<td>Updated to support the Fifth Amended and Restated MSPA</td>
</tr>
<tr>
<td>October 2024</td>
<td>2.0</td>
<td>Version 2.0 – Added support for DE, IN, IA, KY, MD, MI, MT, NH, NE, NJ, OR, RI, TN, TX in accordance with the Second Amended and Restated MSPA.</td>
</tr>
<tr>
<td>December 2022</td>
<td>1.0</td>
<td>Version 1.0 released</td>
</tr>
</tbody>
</table>
</div>

<h2>Multi-State Privacy Agreement (MSPA) US National Section</h2>
<p>The MSPA US National Section string includes the components described below.</p>

<p>
Implementers must support the MSPA US National Privacy Section to adhere to the “US National Approach” for their Processing of a Consumer’s Personal Information, as defined in Section 1.80 of the MSPA. The MSPA US National Section must only be used by MSPA Signatories and Certified Partners in connection with a Covered Transaction pursuant to the MSPA. Click <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.iabprivacy.com/">here</a> to access IABPrivacy.com which includes links to the text of the MSPA and the Signatory and Certified Partner Identification List.</p>

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
<td>The MSPA US National Section is assigned <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md">GPP Section ID</a> 7.</td>
</tr>
<tr>
<td>Client-side API prefix</td>
<td>usnat</td>
<td>The MSPA US National Section is assigned the client side API prefix “usnat” in the GPP Client Side API.</td>
</tr>
</tbody>
</table>
</div>

<h3>Section encoding</h3>
<p>Note that JS is case sensitive, so field name references should be UpperCamelCase with exactly the same spelling as the strings in the "Field Name" column. <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#section-encoding">This table</a> explains how to map the GPP field types to JavaScript native data types. Please refer to the <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-">PingReturn's parsedSections object</a> for an example of how to reference fields.<p>

<h4>Section Header</h4>
<p>The section header is required and must always be present, it includes the following fields</p>
<div>
<table>
<tbody>
<tr>
<td><strong>Field Name</strong></td>
<td><strong>Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>SectionId</code></td>
<td>Int(6)</td>
<td>Section ID from the <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md">Section IDs list.</a></td>
</tr>
<tr>
<td><code>Version</code></td>
<td>Int(6)</td>
<td>The version of this section specification used to encode the string.</td>
</tr>
</tr>
<tr>
<td><code>SubSections</code></td>
<td>Range (Fibonacci)</td>
<td>List of subsection ids that are contained in this section. The IDs must be represented in the order the related subsections appear in the string. The Core subsection is required and always included first, so its ID (zero) is not included in the subsection IDs list.</td>
</tr>
</tbody>
</table>
</div>

<h4>Subsection IDs</h4>
<p>The currently defined MSPA US National subsections are:</p>
<div>
<table>
<tbody>
<tr>
<td><strong>Subsection ID</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>0</code></td>
<td>Core</td>
</tr>
<tr>
<td><code>1</code></td>
<td>GPC</td>
</tr>
</tbody>
</table>
</div>


<h4>Core Subsection</h4>
<p>The Core subsection must always be present. Where terms are capitalized in the "Description" column they refer to defined terms in Applicable State Privacy Laws and the MSPA. The Core subsection consists of the following fields:</p>

<div>
<table>
<thead>
<tr>
<th>
<p><strong>Field Name</strong></p>
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
<td><code>MspaVersion</code></td>
<td>Int(6)</td>
<td>Version of the MSPA</td>
</tr>
<tr>
<td><code>MspaNotice</code></td>
<td>Int(2)</td>
<td>First Party provided notice pursuant to Section 4.3 of the MSPA
<p><code>1</code> No, notice was not provided because the First Party does not Sell or Share Personal Information</p>
<p><code>2</code> Yes, notice was provided</p> 
</td>
</tr>
<tr>
<td><code>MspaOptOut</code></td>
<td>Int(2)</td>
<td>Consumer submitted a request to Opt Out pursuant to the Choice Mechanisms provided under Section 4.4 of the MSPA.
<p><code>0</code> Not applicable because the First Party does not Sell or Share Personal Information or Process Personal Information for Targeted Advertising.</p>
<p><code>1</code> Consumer Opted Out</p> 
<p><code>2</code> Consumer Did Not Opt Out </p> 
</td>
</tr>
<tr>
<td><code>MspaId</code></td>
<td>Int(14)</td>
<td>The MSPA identifier from the First Party where the string originates.
</td>
</tr>
</tbody>
</table>
</div>

<h4 id="gpc-subsection">GPC Subsection</h4>
<p><a href="https://w3c.github.io/gpc/" target="_blank" rel="noopener">GPC</a> is signaled in user agent headers<code>(Sec-GPC)</code> and a simple javascript API <code>(globalPrivacyControl)</code>. Entities creating GPP strings must check for whether GPC is set and pass along the signal they find (from the headers or javascript API) in this subsection. The GPC subsection must always be present.</p>

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
<td style="text-align:left"><code>SubsectionType</code></td>
<td style="text-align:left">Int(2)</td>
<td><code>1</code> GPC</td>
</tr>
<tr>
<td style="text-align:left"><code>Gpc</td>
<td style="text-align:left">Boolean</td>
<td style="text-align:left"><p><code>0</code> false<p><code>1</code> true</td>
</tr>
</tbody>
</table>
