# Global Privacy Platform String

### Version History


<table>
  <tr>
    <td><strong>Date</strong></td>
	  <td><strong>Version</strong></td>
    <td><strong>Comments</strong></td>
  </tr>
  <tr>
	  <td>Sept 28, 2022</td>    
<td><code>1.0</code></td>
    <td>Published final public version</td>
  </tr>
</table>



## Introduction

This document is one of the IAB Tech Lab Global Privacy Platform Specifications. It defines the technical implementation of the structure and encoding for a Global Privacy Platform String (GPP String). 


# Additional Reading and Referenced Documents

- Consent Manager Provider JS API
- GPP Sections


# Updates to Standards Needed to Support GPP

Updates were made to existing Tech Lab standards to support the Global Privacy Platform. These updates are based on industry consensus, driven by relevant IAB Tech Lab working groups, including the Global Privacy working group and Programmatic Supply Chain working group. They include:


**OpenRTB Community Extensions: ** 

Given limited adoption of the AdCom / OpenRTB 3.0 specification, GPP assumes the use of OpenRTB 2.x. 

- Like other existing privacy signals (TCF and USPrivacy), the GPP string is also able to be transported via OpenRTB. This will begin as an extension within the Regs object. For additional guidance, see the [OpenRTB community extensions Github repo](#https://github.com/InteractiveAdvertisingBureau/openrtb/tree/master/extensions/community_extensions).

## About the Global Privacy Platform

The Global Privacy Platform (GPP) has the objective to enable all parties in the digital advertising chain to comply with regional privacy regulations more easily. It is a transport layer that communicates user consent and preference signaling throughout the digital supply chain that supports existing consent formats and is flexible enough to support new markets with unique needs. IAB Tech Lab stewards the development of these technical specifications.


## About IAB Tech Lab


The IAB Technology Laboratory (Tech Lab) is a non-profit consortium that engages a member community globally to develop foundational technology and standards that enable growth and trust in the digital media ecosystem. Comprised of digital publishers, ad technology firms, agencies, marketers, and other member companies, IAB Tech Lab focuses on improving the digital advertising supply chain, measurement, and consumer experiences, while promoting responsible use of data. Its work includes the OpenRTB real-time bidding protocol, ads.txt anti-fraud specification, Open Measurement SDK for viewability and verification, VAST video specification, and DigiTrust identity service. Established in 2014, the IAB Tech Lab is headquartered in New York City with staff in San Francisco, Seattle, and London.
Learn more at iabtechlab.com.

**Contributors and Technical Governance**

IAB Tech Lab's Global Privacy Working Group members provide contributions to this repository. Participants in the Global Privacy Working group must be members of IAB Tech Lab. Technical Governance for the project is provided by the IAB Tech Lab Privacy & Rearc Commit Group.

**License**

Global Privacy Platform technical specifications governed by the IAB Tech Lab is licensed under a Creative Commons Attribution 3.0 License. To view a copy of this license, visit creativecommons.org/licenses/by/3.0/ or write to Creative Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA.

**Disclaimer**

THE STANDARDS, THE SPECIFICATIONS, THE MEASUREMENT GUIDELINES, AND ANY OTHER MATERIALS OR SERVICES PROVIDED TO OR USED BY YOU HEREUNDER (THE “PRODUCTS AND SERVICES”) ARE PROVIDED “AS IS” AND “AS AVAILABLE,” AND IAB TECHNOLOGY LABORATORY, INC. (“TECH LAB”) MAKES NO WARRANTY WITH RESPECT TO THE SAME AND HEREBY DISCLAIMS ANY AND ALL EXPRESS, IMPLIED, OR STATUTORY WARRANTIES, INCLUDING, WITHOUT LIMITATION, ANY WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AVAILABILITY, ERROR-FREE OR UNINTERRUPTED OPERATION, AND ANY WARRANTIES ARISING FROM A COURSE OF DEALING, COURSE OF PERFORMANCE, OR USAGE OF TRADE. TO THE EXTENT THAT TECH LAB MAY NOT AS A MATTER OF APPLICABLE LAW DISCLAIM ANY IMPLIED WARRANTY, THE SCOPE AND DURATION OF SUCH WARRANTY WILL BE THE MINIMUM PERMITTED UNDER SUCH LAW. THE PRODUCTS AND SERVICES DO NOT CONSTITUTE BUSINESS OR LEGAL ADVICE. TECH LAB DOES NOT WARRANT THAT THE PRODUCTS AND SERVICES PROVIDED TO OR USED BY YOU HEREUNDER SHALL CAUSE YOU AND/OR YOUR PRODUCTS OR SERVICES TO BE IN COMPLIANCE WITH ANY APPLICABLE LAWS, REGULATIONS, OR SELF-REGULATORY FRAMEWORKS, AND YOU ARE SOLELY RESPONSIBLE FOR COMPLIANCE WITH THE SAME.


## About the Global Privacy Platform String

In the GPP, a GPP String is used to encapsulate relevant details about how transparency and consent was established and encoded as it applies for each supported regional or other signal. This document specifies how that string must be formatted and how it must be used.

# What purpose does a GPP String serve?

A GPP String’s primary purpose is to encapsulate and encode all the information disclosed to a user and the expression of their preferences for their personal data processing, for all applicable regions. Using a Consent Management Platform (CMP), the information is captured into an encoded and compact HTTP-transferable string. This string enables communication of transparency and consent information to entities that process a user’s personal data. Vendors decode a GPP String to determine whether they have the necessary legal bases to process a user’s personal data for their purposes. The concise string data format enables a CMP to persist and retrieve a user’s preferences any time they’re needed as well as transfer that information to any vendors who need it.

# What information is stored in a GPP String?

Version 1 of the GPP String contains the following information: 

1. **User disclosures and choices:** Disclosures to and control by the user, with a given granularity dependent on jurisdictional and policy requirements (by-purpose, by-vendor, by-legal-basis, or “omnibus” all or nothing)
2. **General metadata:** context of the choices including timestamps, versions, CMP info, locales, publisher info, regional or jurisdictional applicability
3. **Restrictions:** possible additional legal, publisher, or framework restrictions


Section specifications will clearly define which of the above data are represented, and in what form. Whenever possible, the various technical enumerations that have been developed for TCF v2.0 can be used directly or adapted: 
1. Integer identifiers for version & screens
2. CMP ID’s from TCF v2.0
3. Where applicable to the jurisdiction or region, the vendor ID's and data processing purposes as enumerated in the TCF v2.0 GVL can be reused in whole or adapted. 


See “Discrete Sections” below for more detail.


# Who should create a GPP String?

Digital property owners or CMPs are responsible for generating, persisting, and passing the GPP String. Vendors or any other third-party service providers must neither create nor alter GPP Strings.


# How does a URL-based service process the GPP String when it can’t execute Javascript?


When a creative is rendered, it may contain a number of pixels under <img> tags. For example, `<img src = "http://vendor-a.com/key1-val1&key2=val2">` which fires an HTTP GET request from the browser to Vendor A’s domain.


Since the pixel is in an <img> tag without the ability to execute Javascript, the CMP API cannot be used to obtain the GPP String. All parties in the ad supply chain who transact using URLs must add a pair of macros in their URLs where the GPP String, and applicable section, are inserted. Any caller with access to the applicable GPP String must insert it within a URL containing the macro ${GPP_STRING_XXXXX} where XXXXX is the numeric GPP ID of the vendor receiving the string. The applicable section must also be inserted, where the ${GPP_SID}macro is present.


For example, for Vendor A with ID 123 to receive a GPP String which includes the EU TCF v2 as applicable section, an image URL must include two key-value pairs with the URL parameters and macros gpp=${GPP_STRING_123} and gpp_sid=${GPP_SID}.


The resulting URL is: 
`http://vendor-a.com/key1-val1&key2=val2&gpp=${GPP_STRING_123}&gpp_sid=${GPP_SID}`


If the GPP String is: 
`DBACNYA~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA~1YNN`


Then the caller replaces the macro in the URL with the actual GPP String so that the originally placed pixel containing the macro is modified as follows when making the call to the specified server.
 
 
`http://vendor-a.com/key1=val1&key2=val2&gpp=DBACNYA~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA~1YNN&gpp_sid=2`

GPP Strings must always be propagated as is, and not modified. Additional URLs in the supply chain are addressed the same way with remaining vendors. 

The available URL parameters and macros to relay information down the supply chain are listed in the following section.


**Full GPP String passing**

Services that are called using a URL from the user's browser, like cookie staplers, user id associators, and tracking pixels (the 'callee') are passed as macros within the URL and formatted as:
` &url_parameter=${macro_name}`

The supported URL parameters and the corresponding macros are defined below:

<table>
  <tr>
    <td><strong>URL Parameter</strong></td>
	  <td><strong>Corresponding Macro</strong></td>
    <td><strong>Representation in URL</strong></td>
  </tr>
  <tr>
	  <td>gpp</td>    
<td><code>GPP_STRING_XXXXX (XXXXX is numeric GPP ID - the ID of the vendor on the GPP ID List who is expecting this URL call)</code></td>
    <td>&gpp=${GPP_STRING_123}</td>
    </tr>
  <tr>
	  <td>gpp_sid</td>    
<td><code>GPP_SID</code></td>
    <td>&gpp_sid=${GPP_SID}</td>
   </td>
   </td>
  </tr>
</table>



The service making the call must replace the macros with appropriate values described in the table below. For macro ${GPP_STRING_XXXXX}, the service making the call must also check that the macro name contains a valid GPP ID before replacing the macro. 


The creator of the URL should ensure these parameters are added only once, and are passed to services which are expecting them and can handle them properly.

<table>
  <tr>
    <td><strong>Macro</strong></td>
	  <td><strong>Possible Values</strong></td>
    <td><strong>Purpose</strong></td>
  </tr>
  <tr>
	  <td>${GPP_STRING_XXXXX}</td>    
<td><code>Url-safe base64-encoded GPP string.</code></td>
    <td>Encodes the GPP string, as obtained from the CMP JS API or OpenRTB</td>
    </tr>
  <tr>
	  <td>${GPP_SID}</td>    
<td><code>The section ID(s) in force for the current transaction. In most cases, this field should have a single section ID. In rare occasions where such a single section ID can not be determined, the field may contain up to 2 values, separated by a comma.</code></td>
    <td>As the GPP String may encode user preferences for multiple jurisdictions, this field indicates to the callee which section of the string is considered “in force” by the caller. This should match the value returned by the CMP API (see below).</td>
   </td>
   </td>
  </tr>
</table>


### Fibonacci Encoding to Deal with String Length

There are cases in existing privacy signals where strings are too long for certain applications. Since the GPP expects additional Discrete Sections to be added, it is reasonable to expect that string length will continue be a concern. To optimize this, we look to Fibonacci coding. 

**About Fibonacci Encoding**

In simple terms, Fibonacci numbers are numbers that are the combination of the two Fibonacci numbers that come before. The numbers are [excluding 0, 1,] 1 (0+1), 2 (1+1), 3 (1+2), 5 (2+3), 8 (5+3), 13 (5+8), and so on... The numbers can be converted into bit sequences that are unique and will always end on “11”. E.g. the bit representation of the first Fibonacci numbers are:


<table>
  <tr>
    <td><strong>Number</strong></td>
    <td><strong>Fibonacci representation</strong></td>
    <td><strong>Bit sequence</strong></td>
  </tr>
  <tr>
    <td><code>1</code></td>
    <td>F(2)</td>
    <td>11</td>
  </tr>
  <tr>
    <td><code>2</code></td>
    <td>F(3)</td>
    <td>011</td>
  </tr>
  <tr>
    <td><code>3</code></td>
    <td>F(4)</td>
    <td>0011</td>
  </tr>
  <tr>
    <td><code>4</code></td>
    <td>F(2) + F(4)</td>
    <td>1011</td>
  </tr>
  <tr>
    <td><code>5</code></td>
    <td>F(5)</td>
    <td>00011</td>
   </tr>
  <tr>
    <td><code>6</code></td>
    <td>F(2) + F(5)</td>
    <td>10011</td>
  </tr>
  <tr>
    <td><code>7</code></td>
    <td>F(3) + F(5)</td>
    <td>01011</td>
     </td>
     </td>
  </tr>
</table>




The advantage of this is, that a sequence of numbers can be encoded into a sequence of bits without the need to know the length of the bit sequences in advance. This, therefore, saves a lot of bits (size), in the case of TCF it especially saves size when encoding numbers that are around 100 to 4000.


**Encoding and Decoding**

The encoding and decoding is simple and can be done in basically all development languages.

(From [Wikipedia](#https://en.wikipedia.org/wiki/Fibonacci_coding))

To encode an integer *N*:

1. Find the largest Fibonacci number equal to or less than *N*; subtract this number from *N*, keeping track of the remainder.
2. If the number subtracted was the *i*-th Fibonacci number *F(i)*, put a 1 in place *i*−2 in the code word (counting the left-most digit as place 0).
3. Repeat the previous steps, substituting the remainder for *N*, until a remainder of 0 is reached.
4. Place an additional 1 after the rightmost digit in the code word.

To decode a code word, remove the final "1", assign the remaining values 1,2,3,5,8,13... (the Fibonacci numbers) to the bits in the code word, and sum the values of the "1" bits. 


## Creating a GPP String

The following details provide information on creating, storing, and managing a GPP String. The basic steps for creating a GPP String are as follows: 

1. **Create discrete sections.** For each section: 
 - For sections that use the recommended base64-websafe encoding, create a bit representation of the Section’s header (if it exists) and each sub-section. Then, convert them to base64-websafe without padding (i.e. removing “=” at the end) and concatenate the header and all sub-sections using the “.” (dot) character.
 - For sections that use different encoding, ensure that the data is websafe and does not include the “~” (tilde) character.
2. **Create header section.** Create a bit representation of the GPP header section. Include all IDs for discrete sections in a sorted order. Then, convert it to base64-websafe without padding.
3. **Concatenate all sections.** Concatenate the GPP-header as the first item to the encoded versions of the discrete sections using “~” (tilde) as the delimiter.


# How should the GPP String be stored?

The storage mechanism used for GPP Strings is up to a CMP, including any non-cookie storage mechanism.

# GPP String Format

The GPP string is comprised of distinct sections joined together on a “~” (tilde) character.

The string must contain a header and applicable discrete section(s): 
[Header]~[Discrete Section]


**Header**

The header is always required and comes first. The purpose of the Header is to identify which transparency and control signals are included in a string payload and be a table of contents of where to find each signal in the string payload (broken into discrete sections). It is basically an ordered list of discrete sections that equate to different regions and counties and their jurisdictions. It lets readers understand what is present in the string and in what order. (See [Discrete Sections](#https://docs.google.com/document/d/1cl9vdDN3kVO0AZFOL7gBCGcyUh5obbjcbXmn3IlLsM4/edit?pli=1#heading=h.28tuopy3glus) below)

The header contains only a GPP version, the section ID(s) and index of the place of the associated section in the string. The header delegates regional policy versions and technical encoding versions to each substring section so that each may develop independently of each other and the header design. (See [Discrete Sections](#https://docs.google.com/document/d/1cl9vdDN3kVO0AZFOL7gBCGcyUh5obbjcbXmn3IlLsM4/edit?pli=1#heading=h.28tuopy3glus) below)


**Section IDs**

Below is an example of how Section IDs are enumerated. For the full list of Section IDs, see [Section information](#https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20information). 


<table>
  <tr>
    <td><strong>Section ID</strong></td>
	  <td><strong>Description</strong></td>
  </tr>
  <tr>
	  <td>1</td>    
<td><code>EU TCF v1 section (deprecated)</code></td>
  </tr>
  <tr>
	  <td>2</td>    
<td><code>EU TCF v2 section (see note below)</code></td>
     </tr>
  <tr>
	  <td>3</td>    
<td><code>GPP Header section (see note below)</code></td>
   </tr>
  <tr>
	  <td>4</td>    
<td><code>GPP signal integrity section</code></td>
    </tr>
  <tr>
	  <td>5</td>    
<td><code>Canadian TCF section</code></td>
     </tr>
  <tr>
	  <td>6</td>    
<td><code>USPrivacy String section</code></td>
   </tr>
  <tr>
	  <td>...</td>    
<td><code>...</code></td>
  </td>
  </td>
  </tr>
  </table>
	


**Note:** In order to make it simple to distinguish a GPP string from the existing IAB Europe TCF  v2 TC String the first space in the header should be the version. This would allow current implementations to more easily understand and adapt to a GPP string. If the reader of a string finds “C” as the first character this indicates the string is IAB Europe’s TCF v2.0 ("2" in bits corresponds to letter "C" in base64). If the reader of a string finds a “D” as the first character this indicates the string is GPP ("3" in bits corresponds to letter "D" in base64). 


**Header Encoding**

The Header consists of the following encoded fields and uses Fibonacci encoding. For more information about Fibonacci Encoding, see the “About Fibonacci Encoding” section.



<table>
  <tr>
    <td><strong>Position</strong></td>
    <td><strong>Type</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td><code>Type</code></td>
    <td>Int(6)</td>
    <td>Fixed to 3 as “GPP Header field”</td>
  </tr>
  <tr>
    <td><code>Version</code></td>
    <td>Int(6)</td>
    <td>Version of the GPP spec (currently 1)</td>
  </tr>
  <tr>
    <td><code>Sections</code></td>
    <td>Range(Int)</td>
    <td>List of Section IDs that are contained in the GPP string. Each ID represents a discrete Section that will be concatenated to the Header Section. The IDs must be represented in the order the related Sections appear in the string. This is required to make real time string processing less resource intensive.</td>
     </td>
     </td>
  </tr>
 </table>


**Header Examples**

<table>
  <tr>
    <td><strong>Header Example 1</strong></td>
  </tr>
  <tr>
    <td><code>Conditions:</code></td>
  </tr>
  <tr>
    <td><code>Version</code></td>
    <td>Int(6)</td>
    <td>Version of the GPP spec (currently 1)</td>
  </tr>
  <tr>
    <td><code>Sections</code></td>
    <td>Range(Int)</td>
    <td>List of Section IDs that are contained in the GPP string. Each ID represents a discrete Section that will be concatenated to the Header Section. The IDs must be represented in the order the related Sections appear in the string. This is required to make real time string processing less resource intensive.</td>
     </td>
     </td>
  </tr>
 </table>
Header Examples
The following examples provide a sample Header Section that represents the stated conditions.
Header Example 1
Conditions: 
Version 1 of the GPP string is being used
Includes the section for EU TCF v2
Header Bit Representation: 
Type = 000011
Version = 000001
Section Range
Amount = 000000000001
Item 1 Single = 0
Item 1 start ID = 011

Based on the Section ID table above, the Section ID for EU TCF v2 is 2.
Full header bit string: 
000011 000001 000000000001 0 011
Encoded header: 
DBABMA


Header Example 2
Conditions: 
Version 1 of the GPP string is being used
Includes the sections for EU TCF v2 and US Privacy
Header Bit Representation: 
Type = 000011
Version = 000001
Section Range
Amount = 000000000010
Item 1 Single = 0
Item 1 start ID = 011
Item 2 Single = 0
Item 2 offset to last ID = 1011

Based on the Section ID table above, the Section ID for EU TCF is 2 and the Section ID for US Privacy is 6.
Full header bit string: 
000011 000001 000000000010 0 011 0 1011
Encoded header: 
DBACNYA


Header Example 3
Conditions: 
Version 1 of the GPP string is being used
Includes the sections for Canadian TCF and US Privacy
Bit Representation: 
Type = 000011
Version = 000001
Section Range
Amount = 000000000001
Item 1 Single = 1
Item 1 start ID = 00011
Item 1 offset to last ID = 11

Based on the Section ID table above, the Section ID for Canadian TCF is 5 and the Section ID for US Privacy is 6. See Range (Fibonacci) in the Data Types table for more detail on these fields.
Full bit string: 
000011 000001 000000000001 1 00011 11
Encoded: 
DBABjw

Discrete Sections
Discrete sections are used to support multiple signals from one architecture while maintaining the ability to modify each section as needed. 

Each string segment is scoped to the same body that updates the spec. This allows for regional sovereignty policies to make changes that might include more delimited information. For example, if TCF needs a version 3 and eliminates the concept of “out of band” vendors—which would result in the removal of DisclosedVendors and AllowedVendors—that should not require a version bump to the GPP string specification. 
 
Delimiters
In order to be backward compatible with IAB Europe’s TC String and US Privacy String formats, the delimiter used to separate segments is “~” (tilde).

Note: URL-safe characters are important to meet the integration needs of those not reading privacy signals server side or via the client-side APIs. URL-safe characters are:

A-Z, a-z, 0-9
- (minus)
. (dot)
_ (underscore)
~ (tilde)

“.” and “-” and “_” are in use which leaves “~” as the only possible delimiter unless we re-use “.”.


Section Encoding
A discrete section is encoded according to that specific section’s needs. This means today’s implementations that read and adapt to TCF v2.0 signals or US Privacy signals don't need to change their logic for a given discrete section of the string, as long as the implementation is aware of where the discrete section is.

New sections should follow the guidelines below. Guidelines like these help developers quickly adopt new sections and allow for parsing new sections without the need to reinvent new data types.

The possible data types are: 

Data Type
Encoding
Description
Boolean
1 bit
0=true, 1=false
Integer (fixed length of x)
x bit
A fixed amount of bit representing an integer. Usual lengths are 3, 6 or 12 bit. 
Example: int(6) “000101” represents the number 5
Integer (Fibonacci)
Variable length
Integer encoded using Fibonacci encoding

See “About Fibonacci Encoding” for more detail
String (fixed length of x) (including country codes)
x*6 bit
A fixed amount of bit representing a string. The character’s ASCII integer ID is subtracted by 65 and encoded into an int(6).


Example: int(6) “101010” represents integer 47 + 65 = char “h”
Datetime
36 bit
A datetime is encoded as a 36 bit integer representing the 1/10th seconds since January 01 1970 00:00:00 UTC.


Example JavaScript representation: Math.round((new Date()).getTime()/100)
Bitfield (fixed length of x)
x bit
A fixed amount of bit. Usually each bit represents a boolean for an ID within a group where the first bit corresponds to true/false for ID 1, the second bit corresponds to true/false for ID 2 and so on.
Range (Int)
variable
A range field always consists of the following fields:
int(12) - representing the amount of items to follow
(per item) Boolean - representing whether the item is a single ID (0/false) or a group of IDs (1/true)
(per item) int(16) - representing a) the single ID or b) the start ID in case of a group
(per item + only if group)  int(16) - representing the end ID of the group

Example:
int(12) = 2 // 2 items
Bool = 0 // item 1 is type single ID
int(16) = 3 // ID of item 1
Bool = 1 // item 2 is type group
int(16) = 5 // item 2 start ID
int(16) = 8 // item 2 end ID

Range = [3,5,6,7,8]
Bits = 000000000010 0 0000000000000011 1 0000000000000101 0000000000001000

Note: items may not be in sorted order.
Range (Fibonacci)
variable
A range field always consists of the following fields:
int(12) - representing the amount of items to follow
(per item) Boolean - representing whether the item is a single ID (0/false) or a group of IDs (1/true)
(per item) int(Fibonacci) - representing a) the single ID or b) the offset to the last end ID in case of a group
(per item + only if group)  int(Fibonacci) - length of the group

Example:
int(12) = 2 // 2 items
Bool = 0 // item 1 is type single ID
int(Fibonacci) = 3 // ID of item 1
Bool = 1 // item 2 is type group
int(Fibonacci) = 2 // offset to last ID (3+2 = 5 is first ID)
int(Fibonacci) = 3 // length of group (5+3 =>8 is last ID)

Range = [3,5,6,7,8]
Bits = 000000000010 0 0011 1 011 0011

Note: items MUST be in sorted order.


When defining a new Section, regional policy writers should consider the above format to describe their segment.

Example Section 
Example Field name
Example Type
Example Description
Version
int(6)
Version of Specification XYZ
LastUpdated
datetime
Datetime of last update
OptOutPurposes
Bitfield(6)
Purposes the user opted out for, each bit representing the purpose ID
...
...
...



Note: It is recommended to use Field names in CamelCase and without any special characters or space. This allows the use of the same field names within other APIs (e.g. GPP JS API or GPP Mobile API)


Sub-Sections / Segments
If a section uses sub-sections to separate information or to be more flexible, it can use the delimiter “.” (dot) to separate the sub-sections from each other. 
Other Signals
Header Reference
Other Signals are referenced in the Header when available. Each signal will have its own ID as indicated in the Header documentation of this specification. When Other Signals are present they will be indicated in the encoding format specified in the Header documentation of this specification. Note, in some cases the signal may be present in the user agent (ex. Global Privacy Control), but the CMP or other entity creating the privacy signal may not have fetched the signal.
Currently Supported Signals, Values, and References
In order to be included as a supported GPP signal, Other Signals must meet the following criteria:
Be open designs
Be widely understood and adopted
Have a clear interface for machines
Global Privacy Control 
Global Privacy Control or GPC defines itself as “a signal, transmitted over HTTP and through the DOM, that conveys a person's request to websites and services to not sell or share their personal information with third parties.” It is a result of the California Consumer Privacy Act (CCPA) and has subsequently grown in popularity as other US States debate and enact privacy laws and even US Federal lawmakers weigh privacy legislation options. It is also supported by a number of different market participants including some IAB Tech Lab members.

GPC is signaled in user agent headers (Sec-GPC) and a simple javascript API (globalPrivacyControl). CMPs or other entities creating GPP strings may check for whether GPC is set and pass along the value they find in a GPC section of the GPP string. Potential values are boolean (0/1 for header and true/false for javascript API). True is an opt out of sale under CCPA (“Do not sell my personal information”).
Where can I find specific section details?
You can find all section specific details in the discrete section’s documentation.
GPP String Examples
Using the same cases as in the Header Examples above, the following examples provide a sample GPP string that represents the stated conditions.

GPP String Example 1
Conditions: 
Version 1 of the GPP string is being used
Includes the section for EU TCF v2
Encoded header: 
DBABMA
Full GPP String: 
DBABMA~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA


GPP String Example 2
Conditions: 
Version 1 of the GPP string is being used
Includes the sections for EU TCF v2 and US Privacy
Encoded header: 
DBACNYA
Full GPP String:
DBACNYA~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA~1YNN


GPP String Example 3
Conditions: 
Version 1 of the GPP string is being used
The GPP string includes the sections for Canadian TCF and US Privacy
Encoded header: 
DBABjw
Full GPP String:
DBABjw~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA~1YNN

Signal Integrity
As part of the first version of GPP, signal integrity will be accomplished in concert with the Accountability Platform. The Global Privacy Working Group is committed to introducing signal integrity technology for GPP in future versions. 
GPP Identifier 
Callers needing to consume privacy signals with business entity level disclosures across multiple markets need the ability to do so with the assurance that business entities do not have duplicate or overlapping IDs. There are already existing vendor lists (see note with non-exhaustive list below) on which the same business entity may appear. Frameworks that are supported by the GPP must retrieve their IDs from the IAB Tech Lab Transparency Center. This will ensure the creation of concurrent non-overlapping vendor IDs. 

Registration to participate in a specific framework is governed by the local jurisdiction Policy and T&Cs, who would also be responsible for enforcement and compliance. 

I’m a vendor, how do I get a GPP identifier?
Vendors should decide which framework signals they plan to participate in to determine which list registrations may be required. If approved, a GPP Identifier will be assigned. 

Vendors looking to register for the European GVL or Canadian GVL should do so on this registration portal. Additional details on the Global Vendor List can be found in the Consent string and vendor list format specification.

Vendors looking to sign the LSPA may do so at the Transparency Center. Additional details about the LSPA can be found here. 
I’m a vendor and I already have an GVL ID, is there anything that I need to do?
If you are a vendor with a GVL ID for a specific framework, you already have a GPP ID. However, you may still need to complete registration to participate in a specific framework.



 

