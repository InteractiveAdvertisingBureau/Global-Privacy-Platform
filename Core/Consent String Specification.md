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
	<tr>
	  <td>Nov 3, 2023</td>    
<td><code>1.0</code></td>
    <td>Added clarifications to encoding mechanism, fixed encoded header examples</td>
  </tr>
</table>



## Introduction

This document is one of the IAB Tech Lab Global Privacy Platform Specifications. It defines the technical implementation of the structure and encoding for a Global Privacy Platform String (GPP String). 


### Additional Reading and Referenced Documents

- [Consent Management Platform JS API](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md)
- [GPP Sections](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections)


### Updates to Standards Needed to Support GPP

Updates were made to existing IAB Tech Lab standards to support the Global Privacy Platform. These updates are based on industry consensus, driven by relevant IAB Tech Lab working groups, including the Global Privacy Working Group and Programmatic Supply Chain Working Group. They include:


**OpenRTB Attributes:** 

GPP assumes the use of OpenRTB 2.x. 

- Like other existing privacy signals (TCF and USPrivacy), the GPP string is also able to be transported via OpenRTB. This will be included in the Regs object in the November 2022 release. See this [document](https://github.com/InteractiveAdvertisingBureau/openrtb/tree/master/extensions/community_extensions) for approved design prior to release.

### About the Global Privacy Platform

The Global Privacy Platform (GPP) enables advertisers, publishers and technology vendors in the digital advertising industry to adapt to regulatory demands across markets. It is a single protocol designed to streamline transmitting privacy, consent, and consumer choice signals from sites and apps to ad tech providers. IAB Tech Lab stewards the development of these technical specifications.


### About IAB Tech Lab


The IAB Technology Laboratory (Tech Lab) is a non-profit consortium that engages a member community globally to develop foundational technology and standards that enable growth and trust in the digital media ecosystem. Comprised of digital publishers, ad technology firms, agencies, marketers, and other member companies, IAB Tech Lab focuses on improving the digital advertising supply chain, measurement, and consumer experiences, while promoting responsible use of data. Its work includes the OpenRTB real-time bidding protocol, ads.txt anti-fraud specification, Open Measurement SDK for viewability and verification, VAST video specification, and DigiTrust identity service. Established in 2014, the IAB Tech Lab is headquartered in New York City with staff in San Francisco, Seattle, and London.
Learn more at [iabtechlab.com](iabtechlab.com).

**Contributors and Technical Governance**

IAB Tech Lab's Global Privacy Working Group members provide contributions to this repository. Participants in the Global Privacy Working group must be members of IAB Tech Lab. Technical Governance for the project is provided by the IAB Tech Lab Privacy & Rearc Commit Group.

**License**

Global Privacy Platform technical specifications governed by the IAB Tech Lab is licensed under a Creative Commons Attribution 3.0 License. To view a copy of this license, visit [creativecommons.org/licenses/by/3.0/](creativecommons.org/licenses/by/3.0/) or write to Creative Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA.

**Disclaimer**

THE STANDARDS, THE SPECIFICATIONS, THE MEASUREMENT GUIDELINES, AND ANY OTHER MATERIALS OR SERVICES PROVIDED TO OR USED BY YOU HEREUNDER (THE “PRODUCTS AND SERVICES”) ARE PROVIDED “AS IS” AND “AS AVAILABLE,” AND IAB TECHNOLOGY LABORATORY, INC. (“TECH LAB”) MAKES NO WARRANTY WITH RESPECT TO THE SAME AND HEREBY DISCLAIMS ANY AND ALL EXPRESS, IMPLIED, OR STATUTORY WARRANTIES, INCLUDING, WITHOUT LIMITATION, ANY WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AVAILABILITY, ERROR-FREE OR UNINTERRUPTED OPERATION, AND ANY WARRANTIES ARISING FROM A COURSE OF DEALING, COURSE OF PERFORMANCE, OR USAGE OF TRADE. TO THE EXTENT THAT TECH LAB MAY NOT AS A MATTER OF APPLICABLE LAW DISCLAIM ANY IMPLIED WARRANTY, THE SCOPE AND DURATION OF SUCH WARRANTY WILL BE THE MINIMUM PERMITTED UNDER SUCH LAW. THE PRODUCTS AND SERVICES DO NOT CONSTITUTE BUSINESS OR LEGAL ADVICE. TECH LAB DOES NOT WARRANT THAT THE PRODUCTS AND SERVICES PROVIDED TO OR USED BY YOU HEREUNDER SHALL CAUSE YOU AND/OR YOUR PRODUCTS OR SERVICES TO BE IN COMPLIANCE WITH ANY APPLICABLE LAWS, REGULATIONS, OR SELF-REGULATORY FRAMEWORKS, AND YOU ARE SOLELY RESPONSIBLE FOR COMPLIANCE WITH THE SAME.


## About the Global Privacy Platform String

In the GPP, a GPP String is used to encapsulate relevant details about transparency and consumer choice and encoded as it applies for each [supported regional or other signal](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections). This document specifies how that string must be formatted and how it must be used.

### What purpose does a GPP String serve?

A GPP String’s primary purpose is to encapsulate and encode all the information disclosed to a user and the expression of their choices, for all applicable regions. Using a Consent Management Platform (CMP), the information is captured into an encoded and compact HTTP-transferable string. This string enables communication of the consumer's choices from sites and apps to ad tech providers. Ad tech providers decode a GPP String to determine whether they have the necessary requirements to process a user’s personal data for their purposes. 

### What information is stored in a GPP String?

Version 1 of the GPP String contains the following information: 

1. **User disclosures and choices:** Disclosures to and control by the user, with a given granularity dependent on jurisdictional and policy requirements (by-purpose, by-vendor, by-legal-basis, or “omnibus” all or nothing)
2. **General metadata:** context of the choices including timestamps, versions, CMP info, locales, publisher info, regional or jurisdictional applicability
3. **Restrictions:** possible additional legal, publisher, or framework restrictions


Section specifications will clearly define which of the above data are represented, and in what form.  


See [“Discrete Sections”](#discretesections) below for more detail.


### Who should create a GPP String?

Digital property owners or CMPs are responsible for generating, persisting, and passing the GPP String. Vendors or any other third-party service providers must neither create nor alter GPP Strings.



### Fibonacci Encoding to Deal with String Length <a name="fibonacci"></a>

There are cases in existing privacy signals where strings are too long for certain applications. Since the GPP expects additional discrete sections to be added, it is reasonable to expect that string length will continue to be a concern. To optimize this, we look to Fibonacci coding. 

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

(From [Wikipedia](https://en.wikipedia.org/wiki/Fibonacci_coding))

To encode an integer *N*:

1. Find the largest Fibonacci number equal to or less than *N*; subtract this number from *N*, keeping track of the remainder.
2. If the number subtracted was the *i*-th Fibonacci number *F(i)*, put a 1 in place *i*−2 in the code word (counting the left-most digit as place 0).
3. Repeat the previous steps, substituting the remainder for *N*, until a remainder of 0 is reached.
4. Place an additional 1 after the rightmost digit in the code word.

To decode a code word, remove the final "1", assign the remaining values 1,2,3,5,8,13... (the Fibonacci numbers) to the bits in the code word, and sum the values of the "1" bits. 


## Creating a GPP String

The following details provide information on creating, storing, and managing a GPP String. The basic steps for creating a GPP String are as follows: 

<ol>
<li><b>Create discrete sections.</b>
<ul><li>For sections that use the recommended encoding mechanism:
	<ol type=1>
		<li>Create a bit representation of the section's header (if it exists).</li>
		<li>Add padding (0) on the right to get to a total bit length that is a multiple of 6 bits.</li>
		<li>To convert the bit sequence into strings, start by taking each 6 bits, convert the 6 bits into an integer, and use this integer as the index of the character in the table below. </li> 
		<li>Concatenate the header to the sub-sections using the "." (dot) character.</li>
	</ol></li>
<li>For sections that use a different encoding mechanism, ensure that the data is websafe and does not include the “~” (tilde) character or the "." (dot) character.</li>
</ul>
</li>
<li><b>Create header section.</b> See examples of the <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/consent-string-clarifications/Core/Consent%20String%20Specification.md?pr=%2FInteractiveAdvertisingBureau%2FGlobal-Privacy-Platform%2Fpull%2F83#header-examples">header section</a> below.
	<ol type=1>
		<li>Create a bit representation of the GPP header section including all Section IDs for discrete sections in a sorted order.</li>
		<li>Add padding (0) on the right to get to a total bit length that is a multiple of 6 bits.</li>
		<li>Convert the integer to convert the six bit sequence into a character where the integer is the index of the character in the table below.</li>
	</ol></li>
<li><b>Concatenate all sections.</b> Concatenate the encoded GPP header as the first item to the encoded versions of the discrete sections using “~” (tilde) as the delimiter. See examples of GPP strings below.</li>
</ol> 

Note that the header and the recommended encoding algorithm for discrete sections utilize a modified version of base64 url safe encoding which omits byte alignment. This modification adapts base64 byte encoding to GPP bit encoding. For example, the GPP header `DBABM` decodes to the 30 bit sequence `000011000001000000000001001100` but cannot be decoded with the standard base64 algorithm.

#### Base 64 URL Encoding Table from RFC 4648
<div>
<table>
<tbody>
<tr>
<td><strong>Value</strong></td>
<td><strong>Encoding</strong></td>
<td><strong>Value</strong></td>
<td><strong>Encoding</strong></td>
<td><strong>Value</strong></td>
<td><strong>Encoding</strong></td>
<td><strong>Value</strong></td>
<td><strong>Encoding</strong></td>
</tr>
<tr>
<td>0</td>
<td>A</td>
<td>17</td>
<td>R</td>
<td>34</td>
<td>i</td>
<td>51</td>
<td>z</td>
</tr>
<tr>
<td>1</td>
<td>B</td>
<td>18</td>
<td>S</td>
<td>35</td>
<td>j</td>
<td>52</td>
<td>0</td>
</tr>
<tr>
<td>2</td>
<td>C</td>
<td>19</td>
<td>T</td>
<td>36</td>
<td>k</td>
<td>53</td>
<td>1</td>
</tr>
<tr>
<td>3</td>
<td>D</td>
<td>20</td>
<td>U</td>
<td>37</td>
<td>l</td>
<td>54</td>
<td>2</td>
</tr>
<tr>
<td>4</td>
<td>E</td>
<td>21</td>
<td>V</td>
<td>38</td>
<td>m</td>
<td>55</td>
<td>3</td>
</tr>
<tr>
<td>5</td>
<td>F</td>
<td>22</td>
<td>W</td>
<td>39</td>
<td>n</td>
<td>56</td>
<td>4</td>
</tr>
<tr>
<td>6</td>
<td>G</td>
<td>23</td>
<td>X</td>
<td>40</td>
<td>o</td>
<td>57</td>
<td>5</td>
</tr>
<tr>
<td>7</td>
<td>H</td>
<td>24</td>
<td>Y</td>
<td>41</td>
<td>p</td>
<td>58</td>
<td>6</td>
</tr>
<tr>
<td>8</td>
<td>I</td>
<td>25</td>
<td>Z</td>
<td>42</td>
<td>q</td>
<td>59</td>
<td>7</td>
</tr>
<tr>
<td>9</td>
<td>J</td>
<td>26</td>
<td>a</td>
<td>43</td>
<td>r</td>
<td>60</td>
<td>8</td>
</tr>
<tr>
<td>10</td>
<td>K</td>
<td>27</td>
<td>b</td>
<td>44</td>
<td>s</td>
<td>61</td>
<td>9</td>
</tr>
<tr>
<td>11</td>
<td>L</td>
<td>28</td>
<td>c</td>
<td>45</td>
<td>t</td>
<td>62</td>
<td>-</td>
</tr>
<tr>
<td>12</td>
<td>M</td>
<td>29</td>
<td>d</td>
<td>46</td>
<td>u</td>
<td>63</td>
<td>_</td>
</tr>
<tr>
<td>13</td>
<td>N</td>
<td>30</td>
<td>e</td>
<td>47</td>
<td>v</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>14</td>
<td>O</td>
<td>31</td>
<td>f</td>
<td>48</td>
<td>w</td>
<td></td>
<td></td>
</tr>
<tr>
<td>15</td>
<td>P</td>
<td>32</td>
<td>g</td>
<td>49</td>
<td>x</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>16</td>
<td>Q</td>
<td>33</td>
<td>h</td>
<td>50</td>
<td>y</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
</tbody>
</table>
</div>

### How should the GPP String be stored?

The storage mechanism used for GPP Strings is up to a CMP, including any non-cookie storage mechanism.

### GPP String Format

The GPP string is comprised of distinct sections joined together on a “~” (tilde) character.

The string must contain a header and applicable discrete section(s): 
[Header]~[Discrete Section]


#### **Header**

The header is always required and comes first. The purpose of the Header is to identify which sections are included in a string payload and be a table of contents of where to find each signal in the string payload (broken into discrete sections). It is basically an ordered list of discrete sections that equate to different regions, countries or policies. It lets readers understand what is present in the string and in what order. (See [Discrete Sections](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#discrete-sections-) below)

The header contains only a GPP version, the section ID(s) and index of the place of the associated section in the string. The header delegates regional policy versions and technical encoding versions to each substring section so that each may develop independently of each other and the header design. (See [Discrete Sections](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#discrete-sections-) below)


#### **Section IDs**

For the full list of Section IDs, see [Section information](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md). 



#### **Header Encoding**

The Header is always required and always comes first. It consists of the following encoded fields and uses Fibonacci encoding. For more information about [Fibonacci Encoding](#fibonacci), see the “About Fibonacci Encoding” section.



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
    <td>Range(Fibonacci)</td>
    <td>List of <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md">Section IDs</a> that are contained in the GPP string. Each ID represents a discrete section that will be concatenated to the Header Section. The IDs must be represented in the order the related sections appear in the string. This is required to make real-time string processing less resource intensive.</td>
     </td>
     </td>
  </tr>
 </table>


#### **Header Examples**

<table>
  <tr>
    <td><strong>Header Example 1</strong></td>
  </tr>
  <tr>
<td>Conditions:
	<ul>
		<li>Version 1 of the GPP string is being used</li>
		<li>Includes the section for EU TCF v2</li>
	</ul>
</td>
  </tr>
  <tr>
<td>Header Bit Representation
	<ul>
		<li>Type = 000011</li>
		<li>Version = 000001</li>
		<li>Section Range</li>
			<ul>
				<li>Amount = 000000000001</li>
				<li>Item 1 Single = 0</li>
				<li>Item 1 start ID = 011</li>
			</ul>
	</ul>
Based on the Section ID table above, the Section ID for EU TCF v2 is 2.</td>
  </tr>
  <tr>
    <td><code>Full header bit string with padding: 000011 000001 000000 000001 001100</code></td>
 </tr>
  <tr>  
	  <td>Encoded header: <code>DBABM</code></td>
     </td>
     </td>
  </tr>
 </table>



<table>
  <tr>
    <td><strong>Header Example 2</strong></td>
  </tr>
  <tr>
<td>Conditions:
	<ul>
		<li>Version 1 of the GPP string is being used</li>
		<li>Includes the section for EU TCF v2 and US Privacy</li>
	</ul>
</td>
  </tr>
  <tr>
<td>Header Bit Representation
	<ul>
		<li>Type = 000011</li>
		<li>Version = 000001</li>
		<li>Section Range</li>
			<ul>
				<li>Amount = 000000000010</li>
				<li>Item 1 Single = 0</li>
				<li>Item 1 start ID = 011</li>
				<li>Item 2 Single = 0</li>
				<li>Item 2 offset to last ID = 1011</li>
		</ul>
	</ul>
Based on the Section ID table above, the Section ID for EU TCF is 2 and the Section ID for US Privacy is 6.</td>
  </tr>
  <tr>
    <td><code>Full header bit string with padding: 000011 000001 000000 000010 001101 011000</code></td>
 </tr>
  <tr>  
	  <td>Encoded header: <code>DBACNY</code></td>
     </td>
     </td>
  </tr>
 </table>



**Header Example 3** 


<table>
  <tr>
    <td><strong>Header Example 3</strong></td>
  </tr>
  <tr>
<td>Conditions:
	<ul>
		<li>Version 1 of the GPP string is being used</li>
		<li>Includes the section for Canadian TCF and US Privacy</li>
	</ul>
</td>
  </tr>
  <tr>
<td>Bit Representation
	<ul>
		<li>Type = 000011</li>
		<li>Version = 000001</li>
		<li>Section Range</li>
			<ul>
				<li>Amount = 000000000001</li>
				<li>Item 1 Single = 1</li>
				<li>Item 1 start ID = 00011</li>
				<li>Item 1 offset to last ID = 11</li>
		</ul>
	</ul>
Based on the Section ID table above, the Section ID for  Canadian TCF is 5 and the Section ID for US Privacy is 6. See Range (Fibonacci) in the <code>Data Types table</code> for more detail on these fields.</td>
  </tr>
  <tr>
    <td><code>Full bit string with padding: 000011 000001 000000 000001 100011 110000</code></td>
 </tr>
  <tr>  
	  <td>Encoded header: <code>DBABjw</code></td>
     </td>
     </td>
  </tr>
 </table>


#### Discrete Sections <a name="discretesections"></a>

Discrete sections are used to support multiple signals from one architecture while maintaining the ability to modify each section as needed. 

Each string section is scoped to the same body that updates the spec. This allows for regional sovereignty policies to make changes that might include more delimited information. For example, if TCF needs a version 3 and eliminates the concept of “out of band” vendors—which would result in the removal of DisclosedVendors and AllowedVendors—that should not require a version bump to the GPP string specification. 

 
#### Delimiters

In order to be backward compatible with IAB Europe’s TC String and US Privacy String formats, the delimiter used to separate sections is “~” (tilde).


> **Note:** URL-safe characters are important to meet the integration needs of those not reading privacy signals server side or via the client-side APIs. URL-safe characters are:

>- A-Z, a-z, 0-9
>- &#8211; (minus)
>- . (dot)
>- _ (underscore)
>- ~ (tilde)

>“.” and “-” and “_” are in use which leaves “~” as the only possible delimiter unless we re-use “.”.


#### Section Encoding

A discrete section is encoded according to that specific section’s needs. This means today’s implementations that read and adapt to TCF v2.0 signals or US Privacy signals don't need to change their logic for a given discrete section of the string, as long as the implementation is aware of where the discrete section is.

New sections should follow the guidelines below. Guidelines like these help developers quickly adopt new sections and allow for parsing new sections without the need to reinvent new data types.

The possible data types are: 

<table>
  <tr>
    <td><strong>Data Type</strong></td>
    <td><strong>Encoding</strong></td>
    <td><strong>JS API output</strong></td>
    <td><strong>Description</strong></td>	
  </tr>
  <tr>
    <td><code>Boolean</code></td>
    <td>1 bit</td>
    <td>true|false</td>
    <td>0=true, 1=false</td>
  </tr>
  <tr>
    <td><code>Integer (fixed length of x)</code></td>
    <td>x bit</td>
    <td>Number</td>
    <td>A fixed amount of bit representing an integer. Usual lengths are 3, 6 or 12 bit. <br><br> Example: int(6) “000101” represents the number 5</td>
  </tr>
  <tr>
    <td><code>Integer (Fibonacci)</code></td>
    <td>Variable Length</td>
    <td>Number</td>
    <td>Integer encoded using Fibonacci encoding <br><br> See <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/Consent%20String%20Specification.md#fibonacci-encoding-to-deal-with-string-length-"> “About Fibonacci Encoding” </a> for more detail</td>
  </tr>
  <tr>
    <td><code>String (fixed length of x) (including country codes)</code></td>
    <td>x*6 bit</td>
    <td>String</td>
    <td>A fixed amount of bit representing a string. The character’s ASCII integer ID is subtracted by 65 and encoded into an int(6). <br><br>Example: int(6) “101010” represents integer 47 + 65 = char “h”</td>
  </tr>
  <tr>
    <td><code>Datetime</code></td>
    <td>36 bit</td>
    <td>Date</td>
    <td>A datetime is encoded as a 36 bit integer representing the 1/10th seconds since January 01 1970 00:00:00 UTC. <br><br>Example JavaScript representation: Math.round((new Date()).getTime()/100)</td>
  </tr>
  <tr>
    <td><code>Bitfield (fixed length of x)</code></td>
    <td>x bit</td>
    <td>Array of Number</td>
    <td>A fixed amount of bit. Usually each bit represents a boolean for an ID within a group where the first bit corresponds to true/false for ID 1, the second bit corresponds to true/false for ID 2 and so on.</td>
 </tr>
  <tr>
	  <td><code>N-bitfield (Variable length Bitfield)</code></td>
	  <td>variable</td>
	  <td>Array of Number</td>
	  <td>Consists of two datapoints: a fixed length Integer(16) that denotes the length and a bitfield with that specific length.
		<p>Please note: Although the API reads/writes to fields (length + bitfield), it will only output the IDs from the bitfield via JS APIs.</p></td>
</tr>
  <tr>
    <td><code>Range (Int)</code></td>
    <td>variable</td>
    <td>Array of Number</td>
    <td>A range field always consists of the following fields: 
	    <ul>
		    <li>int(12) - representing the amount of items to follow</li>
		    <li>(per item) Boolean - representing whether the item is a single ID (0/false) or a group of IDs (1/true)</li>
		    <li>(per item) int(16) - representing a) the single ID or b) the start ID in case of a group</li>
		    <li>(per item + only if group)  int(16) - representing the end ID of the group</li>
	    </ul>
	Example: 
	    <ul>
		    <li>int(12) = 2 // 2 items</li>
		    <li>Bool = 0 // item 1 is type single ID</li>
		    <li>int(16) = 3 // ID of item 1</li>
		    <li>Bool = 1 // item 2 is type group</li>
		    <li>int(16) = 5 // item 2 start ID</li>
		    <li>int(16) = 8 // item 2 end ID</li>    
	    </ul>
	    <ul>
		    <li> Range = [3,5,6,7,8]</li>
		    <li>Bits = 000000000010 0 0000000000000011 1 0000000000000101 0000000000001000</li>
	    </ul> 
Note: items may not be in sorted order.</td>
  </tr>
  <tr>
    <td><code>Range (Fibonacci)</code></td>
    <td>variable</td>
    <td>Array of Number</td>
    <td>A range field always consists of the following fields: 
	    <ul>
		    <li>int(12) - representing the amount of items to follow</li>
		    <li>(per item) Boolean - representing whether the item is a single ID (0/false) or a group of IDs (1/true)</li>
		    <li>(per item) int(Fibonacci) - representing a) the offset to a single ID or b) the offset to the start ID in case of a group (the offset is from the last seen number, or 0 for the first entry)</li>
		    <li>(per item + only if group)  int(Fibonacci) - length of the group</li>
	    </ul>
	    Example: 
	    <ul>
		    <li>int(12) = 2 // 2 items</li>
		    <li>Bool = 0 // item 1 is type single ID</li>
		    <li>int(Fibonacci) = 3 // ID of item 1</li>
		    <li>Bool = 1 // item 2 is type group</li>
		    <li>int(Fibonacci) = 2 // offset to last ID (3+2 = 5 is first ID)</li>
		    <li>int(Fibonacci) = 3 // length of group (5+3 =>8 is last ID)</li>
	    </ul>
	    <ul>
		    <li>Range = [3,5,6,7,8]</li>
		    <li>Bits =  000000000010 0 0011 1 011 0011</li>
	    </ul>
Note: items MUST be in sorted order..</td>
  </tr>
  <tr>
	<td><code>OptimizedRange</code></td>
	<td>variable</td>
	<td>Array of Number</td>
	<td>Consists of two data types:
		<ul>
			<li>First data type is always a Boolean.</li>
			<li>If the first data type is 1/true, the second data type is a Fibonacci Range</li>
			<li>If the first data type is 0/false, the second data type is a Variable length bitfield.</li>
		</ul>
		Please note: although the API reads/writes multiple fields, the API will only return the array of found IDs</td>
	</tr>
	<tr>
	<td><code>OptimizedIntRange</code></td>
	<td>variable</td>
	<td>Array of Number</td>
	<td>Consists of three data types:
		<ul>
			<li>First data type is an Integer (fixed length of 16 bit).</li>
			<li>Second data type is always a Boolean.</li>
			<li>If the second data type is 1/true, the third data type is an Int Range</li>
			<li>If the second data type is 0/false, the second data type is a bitfield of length determined by the first data type (see above)</li>
		</ul>
		Note: This data type is used for downward compatibility only. OptimizedRange is the recommended data type to be used moving forward.</td>
	</tr>	
	<tr>
		<td><code>ArrayOfRanges</code></td>
		<td>variable</td>
		<td>[{'key':number, 'type':number, 'ids':Array of number}, {...}, ...]</td>
		<td>Consists of a variable amount of fields:
			<p><ul><li>First field is always of type Int(12). The value indicates the number of records to follow.</li></p>
				<li>Each entry consists of three datatypes:</li>
				<ul><li>key - Int(6)</li>
				<li>type - Int(2)</li>
				<li>ids - <code>OptimizedIntRange</code> (uses Range(Int) for range of IDs, see <code>OptimizedIntRange</code> data type above for more details)</li></ul></ul>
			<p>Note: <code>ArrayOfRanges</code> is used for downwards compatibility only.</p></td>
	</tr>
	<tr>
		<td><code>N-ArrayOfRanges(X,Y)</code></td>
		<td>variable</td>
		<td>[{'key':number, 'type':number, 'ids':Array of number}, {...}, ...]</td>
		<td>Consists of a variable amount of fields:
			<p><ul><li>First field is always of type Int(12). The value indicates the number of records to follow.</li></p>
				<li>Each record consists of three datatypes:</li>
				<ul><li><b>key</b> - Int(X) Where X is given by the field definition within the corresponding specification.</li>
				<li><b>type</b> - Int(Y) Where Y is given by the field definition within the corresponding specification.</li>
				<li><b>ids</b> - <code>OptimizedRange</code> (uses Fibonacci coding for range of IDs, see <code>OptimizedRange</code> data type above for more details)</li></ul></ul></td></td>
	</tr>
 </table>
 
 


When defining a new section, regional policy writers should consider the above format to describe their section. Policy writers must ensure that each field within the section has a name that is unique for this section. When using multiple sub-sections within the section, field names with similar meanings (such as "type" or "version") shall be prefixed in order to be unique for the section (e.g. "coreVersion" and "publisherVersion").


<table>
  <tr>
    <td><strong>Example Field name</strong></td>
    <td><strong>Example Type</strong></td>
    <td><strong>Example Description</strong></td>
  </tr>
  <tr>
    <td><code>Version</code></td>
    <td>int(6)</td>
    <td>Version of Specification XYZ</td>
  </tr>
  <tr>
    <td><code>LastUpdated</code></td>
    <td>datetime</td>
    <td>Datetime of last update</td>
  </tr>
  <tr>
    <td><code>OptOutPurposes</code></td>
    <td>Bitfield(6)</td>
    <td>Purposes the user opted out for, each bit representing the purpose ID</td>
  </tr>
  <tr>
    <td><code>...</code></td>
    <td>...</td>
    <td>...</td>
     </td>
     </td>
  </tr>
 </table>



> **Note:** It is recommended to use Field names in CamelCase and without any special characters or space. This allows the use of the same field names within other APIs (e.g. GPP JS API or GPP Mobile API)


**Sub-Sections / Sections**

If a section uses sub-sections to separate information or to be more flexible, it can use the delimiter “.” (dot) to separate the sub-sections from each other. 


## Where can I find specific section details?

You can find all section specific details in the discrete section’s [documentation](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections).

## GPP String Examples

Using the same cases as in the [Header Examples](#header) above, the following examples provide a sample GPP string that represents the stated conditions.


<table>
  <tr>
    <td><strong>GPP String Example 1</strong></td>
  </tr>
  <tr>
 <td>Conditions:
	<ul>
	<li>Version 1 of the GPP string is being used</li>
	<li>Includes the section for EU TCF v2</li>
	  </ul>
	</td>
  </tr>
  <tr>
	  <td>Encoded header:<br><code>DBABM</code></td>
	</tr>
	<tr>
		<td>Full GPP String:<br><br><code>DBABM~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA</code></td>
</td>
</td>
</tr>
</table>



<table>
  <tr>
    <td><strong>GPP String Example 2</strong></td>
  </tr>
  <tr>
<td>Conditions:
	<ul>
		<li>Version 1 of the GPP string is being used</li>
		<li>Includes the section for EU TCF v2 and US Privacy</li>
	<ul>
</td>
  </tr>
  <tr>
	  <td>Encoded header:<br><br><code>DBACNY</code></td>
	</tr>
	<tr>
		<td>Full GPP String:<br><br><code>DBACNY~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA~1YNN</code></td>
</td>
</td>
</tr>
</table>



<table>
  <tr>
    <td><strong>GPP String Example 3</strong></td>
  </tr>
  <tr>
<td>Conditions:
	<ul>
		<li>Version 1 of the GPP string is being used</li>
		<li>The GPP string includes the sections for Canadian TCF and US Privacy</li>
	<ul>
</td>
  </tr>
  <tr>
	  <td>Encoded header:<br><br><code>DBABjw</code></td>
	</tr>
	<tr>
		<td>Full GPP String:<br><br><code>DBABjw~CPXxRfAPXxRfAAfKABENB-CgAAAAAAAAAAYgAAAAAAAA~1YNN</code></td>
</td>
</td>
</tr>
</table>



## Signal Integrity

As part of the first version of GPP, signal integrity will be accomplished in concert with the [Accountability Platform.](https://iabtechlab.com/wp-content/uploads/2021/03/iabtechlab_accountability_platform_rfc_2021_march.pdf) The Global Privacy Working Group is committed to introducing signal integrity technology for GPP in future versions. 


## GPP Identifier <a name="gppstring"></a>

Callers needing to consume privacy signals with business entity level disclosures across multiple markets need the ability to do so with the assurance that business entities do not have duplicate or overlapping IDs. There are already existing vendor lists (see note with non-exhaustive list below) on which the same business entity may appear. Frameworks that are supported by the GPP must retrieve their IDs from the IAB Tech Lab Transparency Center. This will ensure the creation of concurrent non-overlapping vendor IDs. 


Registration to participate in a specific framework is governed by the local jurisdiction Policy and T&Cs, who would also be responsible for enforcement and compliance. 


### I’m a vendor, how do I get a GPP identifier?

Vendors should decide which framework signals they plan to participate in to determine which list registrations may be required. If approved, a GPP Identifier will be assigned. 


Vendors looking to register for the TCF EU GVL or TCF Canada GVL should do so on this [registration portal](https://register.consensu.org/). Additional details on the Global Vendor List can be found in the [TCF v2 Consent string and vendor list format](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-global-vendor-list) specification.


Vendors looking to sign the MSPA may do so at the [Transparency Center](https://tools.iabtechlab.com/lspa).  


### I’m a vendor and I already have an GVL ID, is there anything that I need to do?

If you are a vendor with a GVL ID for a specific framework, you already have a GPP ID. However, you may still need to complete registration to participate in a specific framework.



 # How does a URL-based service process the GPP String when it can’t execute Javascript?


When a creative is rendered, it may contain a number of pixels under `<img>` tags. For example, `<img src = "http://vendor-a.com/key1=val1&key2=val2">` which fires an HTTP GET request from the browser to Vendor A’s domain.


Since the pixel is in an `<img>` tag without the ability to execute Javascript, the CMP API cannot be used to obtain the GPP String. All parties in the ad supply chain who transact using URLs must add a pair of macros in their URLs where the [GPP String](#gppstring), and applicable GPP Section IDs (SID), are inserted. Any caller with access to the applicable GPP String must insert it within a URL containing the macros:

- `${GPP_STRING_XXXXX}` where `XXXXX` is the numeric GPP ID of the vendor receiving the string. - The applicable GPP Section ID must also be inserted, where the ${GPP_SID} macro is present.


Vendors not registered to participate in any framework supported by the Global Privacy Platform (e.g. MSPA, TCF CA, TCF EU) may pass ${GPP_STRING} without the GPP ID. Vendors who are registered to participate and have a GPP ID must include it in the macro. When vendors that are callers–who have the option to expand on the macros–are deciding how to proceed with vendor callees not participating in a GPP supported framework (e.g. MSPA, TCF CA, TCF EU), vendors should reference each framework's policy.

**Example when ${GPP_STRING} rather than ${GPP_STRING_XXXXX}may be used:**

The GPP String includes one of the US States sections or the US National section, but the string creator has indicated that the transaction is not covered by the MSPA. Vendors who do not participate in the MSPA may request the string, but may not have a GPP ID. In this case, ${GPP_STRING} may be used.

**Example when ${GPP_STRING_XXXXX}is used:**

Vendor A with ID 123 to receive a GPP String which includes the EU TCF v2 as applicable section, an image URL must include two key-value pairs with the URL parameters and macros `gpp=${GPP_STRING_123}` and `gpp_sid=${GPP_SID}`.

- The resulting URL is: 
`http://vendor-a.com/key1-val1&key2=val2&gpp=${GPP_STRING_123}&gpp_sid=${GPP_SID}`

- If the GPP String is: 
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


