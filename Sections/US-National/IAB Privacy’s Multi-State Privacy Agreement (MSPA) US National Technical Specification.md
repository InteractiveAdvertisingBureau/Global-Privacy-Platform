
<h1 id="gpp-extension-iab-privacy-s-mspa-us-national-privacy-technical-specification">GPP Extension: IAB Privacy’s MSPA US National Section Technical Specification</h1>

<h2 id="about-this-document">About this document</h2>

<p>The <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform">GPP</a>  standard is designed to be extensible so that support for new regulations can be added without the need to update existing capabilities defined by GPP and the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md">GPP client side API</a>. This document outlines the technical requirements for using the GPP specification with the IAB Privacy Multi-State Privacy Agreement (MSPA) legal requirements.</p>

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
<tr>
<td>August 2024</td>
<td>2.0</td>
<td>Version 2.0 – Added support for DE, IN, IA, KY, MD, MI, MT, NH, NE, NJ, OR, RI, TN, TX in accordance with the Second Amended and Restated MSPA.</td>
</tr>
</tbody>
</table>
</div>

<h2>Multi-State Privacy Agreement (MSPA) US National Section</h2>
<p>The MSPA US National Section string includes the components described below.&nbsp;</p>
<p>
    <br>Implementers should employ the MSPA US National Privacy Section to adhere to the “National Approach” for their Processing of a Consumer’s Personal Information, as defined in Section 1.81 of the MSPA.&nbsp; The MSPA US National Privacy Section should be used by MSPA Signatories and Certified Partners in connection with a Covered Transaction pursuant to the MSPA.&nbsp; Click <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.iabprivacy.com/"><span style="color: rgb(17, 85, 204)">here</span></a> to access the text of the MSPA and to review the Signatory and Certified Partner Identification List.</p>

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
<td>The MSPA US National Section is assigned GPP Section ID 7.&nbsp;</td>
</tr>
<tr>
<td>Client side API prefix</td>
<td>usnat</td>
<td>The MSPA US National Section is assigned the client side API prefix “usnat” in the GPP Client Side API.</td>
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
<td>Notice Describing Your Processing of Personal Information pursuant to the National Approach as defined in Section 1.81(a) of the MSPA, which incorporates the statutory provisions and regulations set forth below:<p><p>
<ul>
<li>Virginia Code 59.1-578(C)(4) &ndash; (5)</li>
<li>Colo. Rev. Stat. 6-1-1308(1)(1)(IV) &ndash; (V)</li>
<li>Utah Code 13-61-302(1)(1)(iv) &ndash; (v)</li>
<li>Conn. PA No. 22-15, Sec. 6(3)(4)-(5)</li>
<li>Cal. Civ. Code 1798.100(a), Cal. Civ. Code 1798.130(a)(5), and 11 CCR 7011 - 7013</li>
<li>Colo. Rev. Stat. 6-1-1308(1)(a) and 4 CCR 904-3-3 and 6.03.</li>
<li>Conn. Gen. Stat. § 42-520(c)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(c)</li>
<li>Ind. Code Ann. §§ 24-15-4-3</li>
<li>Iowa Code § 715D.4(5)</li>
<li>Kentucky Act, Sec. 4(3)</li>
<li>Maryland Act 14-4607(D)</li>
<li>Minn. Stat. § 325O.07, Subd. 1(a)</li>
<li>Montana Act, Sec. 7(5)</li>
<li>N.H. Rev. Stat. 507-H:6(III)</li>
<li>Nebraska Act, Sec. 13</li>
<li>New Jersey Act, Sec. 3(a)</li>
<li>Oregon Act, Sec. 5(4)</li>
<li>Rhode Island Act 6-48.1-3(a)</li>
<li>Tenn. Code Ann. 47-18-3305(c)</li>
<li>Tex. Bus. & Com. Code §§ 541.102(a)</li>
<li>Utah Code 13-61-302(1)(a)</li>
<li>Virginia Code 59.1-578(C)</li>
</ul>
<code>0</code>  Not Applicable. The Business does not share Process Personal Informatin.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SaleOptOutNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Opt Out of the Sale of the Consumer’s Personal Information pursuant to the National Approach as defined in Section 1.81(b) of the MSPA, which incorporates the statutory provisions and regulations set forth below:<p><p>
<ul>
<li>Cal. Civ. Code 1798.100(a)(1), (3), Cal. Civ. Code 1798.135(a), Cal. Civ. Code 1798.135(b), and 11 CCR 7013.</li>
<li>Colo. Rev. Stat 6-1-1308(1)(b), Colo. Rev. Stat. 6-1-1306(1)(a)(III), and 4 CCR 904-3-4.03.</li>
<li>Conn. Gen. Stat. § 42-520(d) and Conn. Gen. Stat. § 42-518(b)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(d)</li>
<li>Ind. Code Ann. § 24-15-4-4</li>
<li>Iowa Code § 715D.4(6)</li>
<li>Kentucky Act, Sec. 4(4)</li>
<li>Maryland Act 14-4607(E)</li>
<li>Minn. Stat. § 325O.07, Subd. 1(b)</li>
<li>Montana Act, Sec. 7(4)</li>
<li>N.H. Rev. Stat. 507-H:6(IV)</li>
<li>Nebraska Act, Sec. 14</li>
<li>New Jersey Act, Sec. 3(b)</li>
<li>Oregon Act, Sec. 5(4)(c)</li>
<li>Rhode Island Act 6-48.1-3(b)</li>
<li>Tenn. Code Ann. 47-18-3305(d)</li>
<li>Tex. Bus. & Com. Code § 541.103</li>
<li>Utah Code 13-61-302(1)(b)(i)</li>
<li>Virginia Code 59.1-578(D)</li>
</ul>
<code>0</code>  Not Applicable. The Business does not Sell Personal Information.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SharingOptOutNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Opt Out of the Sharing of the Consumer’s Personal Information pursuant to the National Approach as defined in Section 1.81(b) of the MSPA, which incorporates the statutory provisions and regulations set forth below:<p><p>&nbsp;(i) Cal. Civ. Code 1798.100(a)(1), (3), Cal. Civ. Code 1798.135(a), Cal. Civ. Code 1798.135(b), and 11 CCR 7013<p><code>0</code>  Not Applicable. The Business does not Share Personal Information.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>TargetedAdvertisingOptOutNotice</td>
<td>Int(2)</td>
<td>Notice of the Opportunity to Opt Out of Processing of the Consumer’s Personal Information for Targeted Advertising pursuant to the National Approach as defined in Section 1.81(b) of the MSPA, which incorporates the statutory provisions and regulations set forth below:<p><p>
<ul>
<li>Colo. Rev. Stat 6-1-1308(1)(b), Colo. Rev. Stat. 6-1-1306(1)(a)(III), and 4 CCR 904-3-4.03.</li>
<li>Conn. Gen. Stat. § 42-520(d) and Conn. Gen. Stat. § 42-518(b)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(d)</li>
<li>Ind. Code Ann. § 24-15-4-4</li>
<li>Iowa Code § 715D.4(6)</li>
<li>Kentucky Act, Sec. 4(4)</li>
<li>Maryland Act 14–4605(B)(7)(I)</li>
<li>Minn. Stat. § 325O.07, Subd. 1(b)</li>
<li>Montana Act, Sec. 7(4)</li>
<li>N.H. Rev. Stat. 507-H:6(IV)</li>
<li>Nebraska Act, Sec. 14</li>
<li>New Jersey Act, Sec. 3(b)</li>
<li>Oregon Act, Sec. 5(4)(h)</li>
<li>Rhode Island Act 6-48.1-3(b)</li>
<li>Tenn. Code Ann. 47-18-3305(d)</li>
<li>Tex. Bus. & Com. Code § 541.103</li>
<li>Utah Code 13-61-302(1)(b)(ii)</li>
<li>Virginia Code 59.1-578(D)</li>
</ul>
<code>0</code>  Not Applicable. The Business does not Process Personal Information for Targeted Advertising.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SensitiveDataProcessingOptOutNotice</td>
<td>Int(2)</td>
<td>Notice to the Consumer of the Consumer’s right to opt out of the Processing of the Consumer’s Sensitive Personal Information that adheres to the requirements of an optional addendum to the MSPA that IAB may, in the future, promulgate to govern the Processing of Sensitive Personal Information by Signatories and Certified Partners for Digital Advertising Activities pursuant to Section 1.28 of the MSPA, which will incorporate the statutory provisions and regulations set forth below:<p><p>
<ul>
    <li>Utah Code 13-61-302(3)(a)</li>
    <li>Iowa Code §&nbsp; 715D.4(2)</li>
</ul>
<p>Note: A Business adhering to the National Approach must obtain consent from Consumers before processing their sensitive data or sensitive personal information. However, Utah Code 13-61-302(3)(a) and Iowa Code §&nbsp; 715D.4(2) requires a controller to provide a consumer with clear notice of the right to opt out of the controller’s processing of the consumer’s sensitive data prior to any such processing. To adhere to these requirements, Businesses following the National Approach should consider incorporating clear notice of the right to opt out as part the process they use to prompt the user to provide consent, for example, by informing Consumers that if they provide consent, they retain the right to opt out (i.e., withdraw consent) of the Business’s processing of their sensitive data at any time. </p>
<code>0</code>  Not Applicable. The Business does not Process Sensitive Data.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SensitiveDataLimitUseNotice</td>
<td>Int(2)</td>
<td>Link to the Consumer that enables the Consumer, or a person authorized by the Consumer, to limit the Business’s use or disclosure of the Consumer’s Sensitive Personal Information and that adheres to the requirements of an optional addendum to the MSPA that IAB may, in the future, promulgate to govern the Processing of Sensitive Personal Information by Signatories and Certified Partners for Digital Advertising Activities as provided in Section 1.28 of the MSPA, which will incorporate the statutory provisions and regulations set forth below:<p><p>
<ul>
    <li>
        <p><span >Cal. Civ. Code 1798.100(a)(2)-(3), Cal. Civ. Code 1798.135(a); Cal. Civ. Code 1798.135(b), and 11 CCR 7014</span>
        </p>
    </li>
</ul>
<code>0</code>  Not Applicable. The Business does not use or disclose Sensitive Data.<p><code>1</code>  Yes, notice was provided<p><code>2</code>  No, notice was not provided</td>
</tr>
<tr>
<td>SaleOptOut</td>
<td>Int(2)</td>
<td>Consumer submitted a request to opt out of the Sale of Personal Information, pursuant to the National Approach as defined in Section 1.81(c) of the MSPA, which incorporates Cal. Civ. Code 1798.120(a) and 11 CCR 7026, Virginia Code 59.1-577(A)(5)(i), Colo. Rev. Stat. 6-1-1306(1)(a)(I)(B), Utah Code 13-61-201(4)(b), Conn. Gen. Stat. § 42-518(a), Iowa Code § 715D.3(1)(d), Ind. Code Ann. § 24-15-3-1(b)(5), Tenn. Code Ann. 47-18-3304(a)(2)(E)(i), Tex. Bus. &amp; Com. Code § 541.051(b)(5)(B), Montana Act, Sec. 5(1)(e)(ii), Oregon Act, Sec. 3(1)(d)(B), Del. Code Ann. tit. 6, § 12D-104(a)(6)(b), New Jersey Act, Sec. 7(a)(5), N.H. Rev. Stat. 507-H:4(I)(e), Nebraska Act, Sec. 7(e)(ii), Kentucky Act, Sec. 3(2)(e), Minn. Stat. § 325O.05, Subd. 1(f), Maryland Act 14–4605(B)(7)(II), or Rhode Island Act 6-48.1-5(e)(4) using a Choice Mechanism (Sale) pursuant to the National Approach as defined in Section 1.81(b) of the MSPA, which incorporates the statutory provisions and regulations set forth below:<p></p>
<ul>
 <li>Cal. Civ. Code 1798.135(a) or 1798.135(b) and 11 CCR 7025 or 7026</li>
<li>Colo. Rev. Stat. 6-1-1306(1)(a)(III) or 6-1-1306(1)(a)(IV), and 4 CCR 904-3-4.03 and 5.03.</li>
<li>Conn. Gen. Stat. § 42-520(1)(A)(e)(i) or (ii)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(e)</li>
<li>Ind. Code Ann. § 24-15-3-1(a)</li>
<li>Iowa Code § 715D.4(7)</li>
<li>Kentucky Act, Sec. 4(5)</li>
<li>Maryland Act 14–4605(C) or 14-46-6(A)(2)</li>
<li>​​Minn. Stat. §§ 325O.07, Subd. 4(b) or 325O.05, Subd. 3(a)</li>
<li>Montana Act, Sec. 6(3)(a) or (b)</li>
<li>N.H. Rev. Stat. 507-H:6(V)(a)(1)(A) or N.H. Rev. Stat. 507-H:6(V)(a)(1)(B)</li>
<li>Nebraska Act, Sec. 11(1) or 11(5)</li>
<li>New Jersey Act, Sec. 3(b) or 8(b)</li>
<li>Oregon Act, Sec. 5(5)</li>
<li>Rhode Island Act 6-48.1-5(f)</li>
<li>Tenn. Code Ann. 47-18-3304(a)</li>
<li>Tex. Bus. & Com. Code § 541.055</li>
<li>Utah Code 13-61-302(1)(b)(i)</li>
<li>Virginia Code 59.1-578(D)</li>
</ul>
<code>0</code>  Not Applicable. SaleOptOutNotice value was not applicable or no notice was provided<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td>SharingOptOut</td>
<td>Int(2)</td>
<td>Consumer submitted a request to opt-out of the Sharing of the Consumer’s Personal Information pursuant to the National Approach as defined in Section 1.81(c) of the MSPA, which incorporates Cal. Civ. Code 1798.120(a) and 11 CCR 7026, using a Choice Mechanism (Share) pursuant to the National Approach as defined in Section 1.81(b) of the MSPA, which incorporates the statutory provisions and regulations set forth below:<p><p>
<ul>
<li>Cal. Civ. Code 1798.135(a) or 1798.135(b) and 11 CCR 7025 or 7026</li>
</ul>
<code>0</code>  Not Applicable. SharingOptOutNotice value was not applicable or no notice was provided.<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td>TargetedAdvertisingOptOut</td>
<td>Int(2)</td>
<td>Consumer submitted a request to opt out of the Processing of Personal Information for Targeted Advertising, pursuant to the National Approach as defined in Section 1.81(c) of the MSPA, which incorporates Virginia Code 59.1-577(A)(5)(i), Colo. Rev. Stat. 6-1-1306(1)(a)(I)(A), Utah Code 13-61-201(4)(a), Conn. Gen. Stat. § 42-518(a), Iowa Code § 715D.4(6), Ind. Code Ann. § 24-15-3-1(b)(5), Tenn. Code Ann. 47-18-3304(a)(2)(E)(ii), Tex. Bus. &amp; Com. Code § 541.055(b)(5)(A), Montana Act, Sec. 5(1)(e)(i), Oregon Act, Sec. 3(1)(d)(A), Del. Code Ann. tit. 6, § 12D-104(a)(6)(a),&nbsp; New Jersey Act, Sec. 7(a)(5), N.H. Rev. Stat. 507-H:4(I)(e), Nebraska Act, Sec. 7(e)(i), Kentucky Act, Sec. 3(2)(e), Minn. Stat. § 325O.05, Subd. 1(f), Maryland Act 14–4605(B)(7)(I), or Rhode Island Act 6-48.1-5(e)(4) using a Choice Mechanism (Targeted Advertising) pursuant to the National Approach as defined in Section 1.81(b) of the MSPA, which incorporates the statutory provisions and regulations set forth below:<p><p>
<ul>
<li>Colo. Rev. Stat. 6-1-1306(1)(a)(III) or 6-1-1306(1)(a)(IV), and 4 CCR 904-3-4.03 or 5.03.</li>
<li>Conn. Gen. Stat. § 42-520(1)(A)(e)(i) or (ii)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(e)</li>
<li>Ind. Code Ann. § 24-15-3-1(a)</li>
<li>Iowa Code § 715D.4(7)</li>
<li>Kentucky Act, Sec. 5(5)</li>
<li>Maryland Act 14–4605(C) or 14-46-6(A)(2)</li>
<li>Minn. Stat. §§ 325O.07, Subd. 1(b) or 325O.05, Subd. 3(a)</li>
<li>Montana Act, Sec. 6(3)(a) or (b)</li>
<li>N.H. Rev. Stat. 507-H:6(V)(a)(1)(A) or N.H. Rev. Stat. 507-H:6(V)(a)(1)(B)</li>
<li>Nebraska Act, Sec. 11(1) or 11(5)</li>
<li>New Jersey Act, Section 3(b) or 8(b)</li>
<li>Oregon Act, Sec. 5(5)</li>
<li>Rhode Island Act 6-48.1-5(f)</li>
<li>Tenn. Code Ann. 47-18-3304(a)</li>
<li>Tex. Bus. & Com. Code § 541.055</li>
<li>Utah Code 13-61-302(1)(b)(ii)</li>
<li>Virginia Code 59.1-578(D)</li>
</ul>
<code>0</code>  Not Applicable. TargetedAdvertisingOptOutNotice value was not applicable or no notice was provided<p><code>1</code>  Opted Out<p><code>2</code>  Did Not Opt Out</td>
</tr>
<tr>
<td>SensitiveDataProcessing</td>
<td>N-Bitfield(2,16)</td>
<td><p>For the specific category of Sensitive Personal Information that is identified in the String Component, have you obtained Consent from the Consumer to Process his or her Sensitive Personal Information in a way that adheres to requirements of an optional addendum to the MSPA that IAB may, in the future, promulgate to govern the Processing of Sensitive Personal Information by Signatories and Certified Partners for Digital Advertising Activities as provided in Section 1.28 of the MSPA, which will incorporate the statutory provisions and regulations set forth below?&nbsp;</p>
<p>Two bits for each Data Activity:</p><code>0</code>  Not Applicable. The Business does not Process the specific category of Sensitive Data.<p><code>1</code> No Consent<p><code>2</code>  Consent&nbsp;<p>
<p>(1) Consent to Process the Consumer’s Sensitive Personal Information Consisting of Personal Information Revealing Racial or Ethnic Origin.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-6.10.</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(2) Consent to Process the Consumer’s Sensitive Personal Information Consisting of Personal Information Revealing Religious or Philosophical Beliefs.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-6.10.</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(3) Consent to Process the Consumer’s Personal Information Consisting of Personal Information Concerning a Consumer’s Health (including a Mental or Physical Health Condition or Diagnosis; Medical History; pregnancy; or Medical Treatment or Diagnosis by a Health Care Professional).<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-6.10.</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(4) Consent to Process the Consumer’s Personal Information Consisting of Personal Information Revealing Sex Life, Sexual Orientation, or Sexuality.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-6.10</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(5) onsent to Process the Consumer’s Personal Information Consisting of Personal Information Revealing Citizenship or Immigration Status.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-6.10</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(6) Consent to Process the Consumer’s Personal Information Consisting of Genetic Data for the Purpose of Uniquely Identifying an Individual / Natural Person.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-6.10</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(7) Consent to Process the Consumer’s Personal Information Consisting of Biometric Data for the Purpose of Uniquely Identifying an Individual / Natural Person.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-6.10</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(8) onsent to Process the Consumer’s Personal Information Consisting of Precise Geolocation Data.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. & Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(9) Consent to Process the Consumer’s Personal Information Consisting of a Consumer’s Social Security, Driver’s License, State Identification Card, or Passport Number.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
</ul>
(10) Consent to Process the Consumer’s Personal Information Consisting of a Consumer’s Account Log-In, Financial Account, Debit Card, or Credit Card Number in Combination with Any Required Security or Access Code, Password, or Credentials Allowing Access to an Account.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
</ul>
(11) Consent to Process the Consumer’s Personal Information Consisting of Union Membership.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
</ul>
(12) Consent to Process the Consumer’s Personal Information Consisting of the contents of a Consumer’s Mail, Email, and Text Messages unless You Are the Intended Recipient of the Communication.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.121(a) and 11 CCR 7027</li>
</ul>
(13) Consent to Process Consumer Health Data about the Consumer.<p></p>References:
<ul>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>  
</ul>
(14) Consent to Process Data Concerning the Consumer’s Status as a Victim of Crime.<p></p>References:
<ul>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
</ul>
(15) Consent to Process the Consumer’s Sensitive Personal Information Consisting of Personal Information Revealing National Origin.<p></p>References:
<ul>
<li>Oregon Act, Sec. 5(2)(b)</li>
</ul>
(16) Consent to Process the Consumer’s Sensitive Personal Information Consisting of Personal Information Revealing Status as Transgender or Nonbinary.<p></p>References:
<ul>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>  
</ul>
</td>
</tr>
<tr>
<td>KnownChildSensitiveDataConsents</td>
<td>N-Bitfield(2,3)</td>
<td>Consent from the Consumer to Process his or her Personal Information or Sensitive Personal Information in a way that adheres to requirements of an optional addendum to the MSPA that IAB may, in the future, promulgate to govern the Processing of Minor Information by Signatories and Certified Partners for Digital Advertising Activities as provided in Section 1.28 of the MSPA, which will incorporate the statutory provisions and regulations set forth below.<p></p>
<p>Two bits for each Data Activity:</p>
<code>0</code>  Not Applicable. The Business does not have actual knowledge that it Processes Personal Data or Sensitive Data of a Consumer who is a known child.<p><code>1</code> No Consent<p><code>2</code> Consent&nbsp;
<p>(1) Consent to Process the Consumer’s Personal Information or Sensitive Personal Information for Consumers from Age 13 to 16.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.120(c) and 11 CCR 7070-7071</li>
<li>Conn. Gen. Stat. § 42-520(a)(7)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(7)</li>
<li>Montana Act, Sec. 7(2)(d)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(g)</li>
<li>New Jersey Act, Sec. 9(a)(7)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
</ul>
(2)Consent to Process the Consumer’s Personal Information or Sensitive Personal Information for Consumers Younger Than 13 Years of Age.<p><p>References:
<ul>
<li>Cal. Civ. Code 1798.120(c) and 11 CCR 7070-7071</li>
<li>Colo. Rev. Stat. 6-1-1308(7) and 4 CCR 904-3-7.06</li>
<li>Conn. Gen. Stat. § 42-520(a)(4)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>Ind. Code Ann. § 24-15-4-1(5)</li>
<li>Iowa Code § 715D.4(2)</li>
<li>Kentucky Act, Sec. 4(1)(e)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(d)</li>
<li>Montana Act, Sec. 7(2)(b)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(d)</li>
<li>Nebraska Act, Sec. 12(2)(d)</li>
<li>New Jersey Act, Sec. 9(a)(4)</li>
<li>Oregon Act, Sec. 5(2)(b)</li>
<li>Rhode Island Act 6-48.1-4(c)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(6)</li>
<li>Tex. Bus. &amp; Com. Code § 541.101(b)(4)</li>
<li>Utah Code 13-61-302(3)(a)</li>
<li>Virginia Code 59.1-578(A)(5)</li>
</ul>
(3) Consent to Process the Consumer’s Personal Information or Sensitive Personal Information for Consumers from Age 16 to 17.<p><p>References:
<ul>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(4)</li>
<li>New Jersey Act, Sec. 9(a)(7)</li>
</ul>
</td>
</tr>
<tr>
<td>PersonalDataConsents</td>
<td>Int(2)</td>
<td>onsumer Consented to the Processing of the Consumer’s Personal Information for Digital Advertising Activities that would, but for providing Consent, not otherwise meet the Secondary Use Limitations.&nbsp; The Secondary Use Limitations, as set forth in the National Approach, incorporate the statutory provisions and regulations set forth below:<p><p>References:
<ul><li>Cal. Civ. Code 1798.100(c) and 11 CCR 7002</li>
<li>Colo. Rev. Stat. 6-1-1308(4) and 4 CCR 904-3-6.08</li>
<li>Conn. Gen. Stat. § 42-520(a)(2)</li>
<li>Del. Code Ann. tit. 6, § 12D-106(a)(2)</li>
<li>Ind. Code Ann. § 24-15-4-1(2)</li>
<li>Kentucky Act, Sec. 4(1)(b)</li>
<li>Minn. Stat. § 325O.07, Subd. 2(b)</li>
<li>Montana Act, Sec. 7(2)(a)</li>
<li>N.H. Rev. Stat. 507-H:6(I)(b)</li>
<li>Nebraska Act, Sec. 12(2)(a)</li>
<li>New Jersey Act, Sec. 9(a)(2)</li>
<li>Oregon Act, Sec. 5(1)(a) and 5(2)(a)</li>
<li>Tenn. Code Ann. 47-18-3305(a)(2)</li>
<li>Tex. Bus. &amp; Com. Code § 541.101(b)(1)</li>
<li>Virginia Code 59.1-578(A)(2)</li>
</ul>
<code>0</code>  Not Applicable. The Business does not Process the Consumer’s Personal Data for advertising purposes that are not reasonably necessary for nor compatible with the disclosed purpose for which the Consumer’s Personal Data was processed.<p><code>1</code> No Consent<p><code>2</code> Consent&nbsp;</td>
</tr>
<tr>
<td>MspaCoveredTransaction</td>
<td>Int(2)</td>
<td>Publisher or Advertiser, as applicable, is a signatory to the IAB Multistate Service Provider Agreement (MSPA), as may be amended from time to time, and declares that the transaction is a “Covered Transaction” as defined in the MSPA.<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
<tr>
<td>MspaOptOutOptionMode</td>
<td>Int(2)</td>
<td>Publisher or Advertiser, as applicable, has enabled “Opt-Out Option Mode” for the “Covered Transaction,” as such terms are defined in the MSPA.<p><code>0</code>  Not Applicable.<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
<tr>
<td>MspaServiceProviderMode</td>
<td>Int(2)</td>
<td>Publisher or Advertiser, as applicable, has enabled “Service Provider Mode” for the “Covered Transaction,” as such terms are defined in the MSPA.<p><code>0</code>  Not Applicable<p><code>1</code>  Yes<p><code>2</code>  No</td>
</tr>
</tbody>
</table>
</div>

<h4 id="gpc-subsection">GPC Sub-section</h4>
<p><a href="https://globalprivacycontrol.github.io/gpc-spec/" target="_blank" rel="noopener">GPC</a> is signaled in user agent headers<code>(Sec-GPC)</code> and a simple javascript API <code>(globalPrivacyControl)</code>. Entities creating GPC Subsections should check whether GPC is set and pass along the value from the headers or javascript API in this subsection. Refer to the </span><a target="_blank" rel="noopener noreferrer nofollow" href="https://privacycg.github.io/gpc-spec/"><span style="color: rgb(17, 85, 204)">GPC specifications</span></a><span style="color: rgb(36, 41, 47)"> for details on GPC including how to handle conflicts or inconsistencies.</span>
</p>

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
