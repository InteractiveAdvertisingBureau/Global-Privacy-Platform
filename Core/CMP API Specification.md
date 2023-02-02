# Consent Management Platform API


## Version History
<table>
  <tr>
    <td><strong>Date</strong></td>
	  <td><strong>Version</strong></td>
    <td><strong>Comments</strong></td>
  </tr>
    <tr>
      <td>TBD</td>    
      <td><code>1.1</code></td>
      <td>Removal of return values in favor of callback functions. Removal of getGPPData command</td>
    </tr>
  <tr>
	<td>Sept 28, 2022</td>    
    <td><code>1.0</code></td>
    <td>Published final public version</td>
  </tr>
</table>



## Introduction
This is one of the IAB Tech Lab Global Privacy Platform Specifications. It defines the API for Consent Management Platforms (CMPs). The CMP API is the interface a CMP provides to callers (web and in-app) to access information regarding the privacy preferences disclosed and obtained from the end user by the CMP. Both required functionality that the CMP must provide and optional features are described.


### About the Global Privacy Platform
The Global Privacy Platform (GPP) enables advertisers, publishers and technology vendors in the digital advertising industry to adapt to regulatory demands across markets. It is a single protocol designed to streamline transmitting privacy, consent, and consumer choice signals from sites and apps to ad tech providers. IAB Tech Lab stewards the development of these technical specifications.


### License
Global Privacy Platform technical specifications governed by the IAB Tech Lab is licensed under a Creative Commons Attribution 3.0 License. To view a copy of this license, visit creativecommons.org/licenses/by/3.0/ or write to Creative Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA.


**Disclaimer**

THE STANDARDS, THE SPECIFICATIONS, THE MEASUREMENT GUIDELINES, AND ANY OTHER MATERIALS OR SERVICES PROVIDED TO OR USED BY YOU HEREUNDER (THE “PRODUCTS AND SERVICES”) ARE PROVIDED “AS IS” AND “AS AVAILABLE,” AND IAB TECHNOLOGY LABORATORY, INC. (“TECH LAB”) MAKES NO WARRANTY WITH RESPECT TO THE SAME AND HEREBY DISCLAIMS ANY AND ALL EXPRESS, IMPLIED, OR STATUTORY WARRANTIES, INCLUDING, WITHOUT LIMITATION, ANY WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AVAILABILITY, ERROR-FREE OR UNINTERRUPTED OPERATION, AND ANY WARRANTIES ARISING FROM A COURSE OF DEALING, COURSE OF PERFORMANCE, OR USAGE OF TRADE. TO THE EXTENT THAT TECH LAB MAY NOT AS A MATTER OF APPLICABLE LAW DISCLAIM ANY IMPLIED WARRANTY, THE SCOPE AND DURATION OF SUCH WARRANTY WILL BE THE MINIMUM PERMITTED UNDER SUCH LAW. THE PRODUCTS AND SERVICES DO NOT CONSTITUTE BUSINESS OR LEGAL ADVICE. TECH LAB DOES NOT WARRANT THAT THE PRODUCTS AND SERVICES PROVIDED TO OR USED BY YOU HEREUNDER SHALL CAUSE YOU AND/OR YOUR PRODUCTS OR SERVICES TO BE IN COMPLIANCE WITH ANY APPLICABLE LAWS, REGULATIONS, OR SELF-REGULATORY FRAMEWORKS, AND YOU ARE SOLELY RESPONSIBLE FOR COMPLIANCE WITH THE SAME.


### About IAB Tech Lab

The IAB Technology Laboratory ("Tech Lab") is a non-profit research and development consortium that produces and provides standards, software, and services to drive growth of an effective and sustainable global digital media ecosystem. Comprised of digital publishers and ad technology firms, as well as marketers, agencies, and other companies with interests in the interactive marketing arena, IAB Tech Lab aims to enable brand and media growth via a transparent, safe, effective supply chain, simpler and more consistent measurement, and better advertising experiences for consumers, with a focus on mobile and "TV"/digital video channel enablement. The IAB Tech Lab portfolio includes the DigiTrust real-time standardized identity service designed to improve the digital experience for consumers, publishers, advertisers, and third-party platforms. Established in 2014, the IAB Tech Lab is headquartered in New York City with an office in San Francisco and representation in Seattle and London.

Learn more about IAB Tech Lab here: https://www.iabtechlab.com/


## CMP API

### What does the CMP API support?

Consent Management Platforms (CMPs) provide a user interface to establish transparency to users, and obtain consent or register objections from end users, and capture their preferences in signals. These signals are packaged in a standardized, easily communicated payload called a GPP String. The CMP API provides a standardized means for parties, such as the hosting publisher or an advertising vendor, to access these preferences managed by the CMP.

Using the API, scripts may obtain the GPP String payload and the information it contains, which is ready to use without having to understand how to “unpack” the payload format. This makes it easy to make immediate data processing decisions based on the returned information.

This API allows for accessing signals across legislations, regulations, and standards. It provides a common interface that can be used to access underlying APIs such as the [IAB TCF](https://github.com/patrickverdon/GDPR-Transparency-and-Consent-Framework/blob/TCF-Canada/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md) and [USPrivacy](https://github.com/InteractiveAdvertisingBureau/USPrivacy/blob/master/CCPA/USP%20API.md). 

#### API Prefixes

In order to distinguish between the different underlying APIs, each API will be assigned a prefix. A complete list of available API prefixes can be found in the [Section information](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md).


Example API prefixes: 


<table>
  <tr>
    <td><strong>API</strong></td>
	  <td><strong>Prefix</strong></td>
  </tr>
  <tr>
	  <td>IAB TCF1 (EU)</td>    
<td><code>tcfeuv1 (no longer used)</code></td>
  </tr>
  <tr>
	  <td>IAB TCF v2 (EU)</td>    
<td><code>tcfeuv2</code></td>
     </tr>
  <tr>
	  <td>IAB TCF v1 (Canada)</td>    
<td><code>tcfcav1</code></td>
   </tr>
  <tr>
	  <td>IAB CCPA/USP v1</td>    
<td><code>uspv1</code></td>
  </tr>
</table>



### How does the CMP provide the API?


Every consent manager must provide the following API function: 

<code>__gpp(command, callback, parameter, [version])</code>


Requirements for the interface: 
- The <code>__gpp</code> function must always be a function and cannot be any other type, even if only temporarily on initialization – the API must be able to handle calls at all times.
- The command must always be a string.
- The callback must always be a function.
- Parameter can be of mixed type depending on used command
- The <code>__gpp</code> function does not have a return value
- If a CMP cannot immediately respond to a query, the CMP must queue all calls to the function and execute them later. The CMP must execute the commands in the same order in which the function was called.
- A CMP must support all generic commands. All generic commands must always be available when a <code>__gpp</code> function is present on the page. This means that “[stub code](#stubcode)” that supports all generic commands must be in place before/during CMP load.
	


### What required API commands must a CMP support? <a name="javascript"></a>


All CMPs must support all generic commands. Generic commands are commands that can be used independent of [section specifications](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/SectionInformation.md). All generic commands must always be executed immediately without any asynchronous logic and call the supplied callback function immediately. The generic commands are: [‘ping’](#ping), [‘addEventListener’](#addeventlistener), [‘removeEventListener’](#removeeventlistener), [‘hasSection’](#hassection), [‘getSection’](#getsection), and [‘getField’](#getfield). 

________
#### `ping` <a name="ping"></a>

The `ping` command can be used to determine the state of the CMP. 
<table>
  <tr>
    <td><strong>argument</strong></td>
    <td><strong>type</strong></td>
    <td><strong>value</strong></td>
  </tr>
  <tr>
    <td><code>command</code></td>
    <td>string</td>
    <td>"ping"</td>
  </tr>
  <tr>
    <td><code>callback</code></td>
    <td>function</td>
    <td>function (data: <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#pingreturn-">PingReturn</a>)</td>
  </tr>
  <tr>
    <td><code>parameter</code></td>
    <td>not used</td>
    <td></td>
  </tr>     
</table>



*Example:*

``` javascript
__gpp('ping', myFunction);
```

#### `PingReturn` <a name="pingreturn"></a>

This object contains information about the loading status and configuration of the CMP.

```javascript
PingReturn = {

gppVersion : String, // must be “Version.Subversion”, current: “1.0”

cmpStatus : String, // possible values: stub, loading, loaded, error

cmpDisplayStatus: String, // possible values: hidden, visible, disabled

supportedAPIs : Array of string, // list of supported APIs (prefix strings), e.g. used while loading. Example: ["tcfeuv2","uspv1"] 

cmpId : Number, // IAB assigned CMP ID, may be 0 during stub/loading

sectionList : Array of Number, // may be empty during loading of the CMP

applicableSections: Array of Number, // Section ID considered to be in force for this transaction. In most cases, this field should have a single section ID. In rare occasions where such a single section ID can not be determined, the field may contain up to 2 values. The value can be 0 or a Section ID specified by the Publisher / Advertiser, during stub / load. When no section is applicable, the value will be -1.

gppString: String // the complete encoded GPP string, may be empty during CMP load

}

```


**Ping Status Codes**

<table>
  <tr>
    <td><strong>Status Code</strong></td>
    <td><strong>Applicable for</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td><code>'stub'</code></td>
    <td>cmpStatus</td>
    <td>CMP not yet loaded - stub still in place</td>
  </tr>
  <tr>
    <td><code>'loaded'</code></td>
    <td>cmpStatus</td>
    <td>CMP is finished loading</td>
  </tr>
  <tr>
    <td><code>'error'</code></td>
    <td>cmpStatus</td>
    <td>CMP is in an error state.  A CMP shall not repsond to any other API requests if this cmpStatus is present. A CMP may set this status if, for any reason, it is unable to perform the operation.</td>
  </tr>
  <tr>
    <td><code>'visible'</code></td>
    <td>cmpDisplayStatus</td>
    <td>User interface is currently displayed</td>
    </tr>
  <tr>
    <td><code>'hidden'</code></td>
    <td>cmpDisplayStatus</td>
    <td>User interface is not yet or no longer displayed</td>
  </tr>
  <tr>
    <td><code>'disabled'</code></td>
    <td>cmpDisplayStatus</td>
    <td>User interface will not show (no Sections apply or data is current and does not need renewal)</td>
     </td>
     </td>
  </tr>
</table>


___________
#### `addEventListener` <a name="addeventlistener"></a> 

The `addEventListener` command can be used to define a callback function that can be used to detect changes in the CMP. The callback shall be called with an `EventListener` object immediately. The GPP script will then call the callback function and return a new EventListener object every time the CMP detects a change (see events below).  A value of `false` will be passed as the argument to the `success` parameter if the CMP fails to process this command. 


<table>
  <tr>
    <td><strong>argument</strong></td>
    <td><strong>type</strong></td>
    <td><strong>value</strong></td>
  </tr>
  <tr>
    <td><code>command</code></td>
    <td>string</td>
    <td>"addEventListener"</td>
  </tr>
  <tr>
    <td><code>callback</code></td>
    <td>function</td>
    <td>function (data: <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Core/CMP%20API%20Specification.md#eventlistener-">EventListener</a>, success: boolean)</td>
  </tr>
  <tr>
    <td><code>parameter</code></td>
    <td>not used</td>
    <td></td>
  </tr>
 </table>
 


*Example:*

```javascript
__gpp('addEventListener', myFunction);
```
  

#### `EventListener` <a name="eventlistenerobject"></a>

The EventListener object is defined as: 

```javascript
EventListener = {
eventName : String, // for possible values see events below
listenerId : Number, // Registered ID of the listener
data: mixed, // data supplied by the underlying API
pingData : object // see PingReturn

}
```


A call to the `addEventListener` command must always trigger an immediate call to the callback function. When registering new event listeners, the CMP (and stub) must therefore generate new listenerIds for each call to this command.


<table>
  <tr>
    <td><strong>Event Name</strong></td>
    <td><strong>Type of data property</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td><code>listenerRegistered</code></td>
    <td>boolean</td>
    <td>Only used within the return object to addEventListener command. The data property signals whether the event listener was registered successfully. If data equals true, a listenerId must be sent, otherwise the listenerId must be 0 (zero).</td>
  </tr>
  <tr>
    <td><code>listenerRemoved</code></td>
    <td>boolean</td>
    <td>Only used within the return object to removeEventListener command. The data property signals whether the event listener was successfully removed.</td>
  </tr>
  <tr>
    <td><code>cmpStatus</code></td>
    <td>string</td>
    <td>Event is called whenever the status of the CMP changes (e.g. the CMP has finished loading). The data property will contain the new status (e.g. “loaded”)</td>
  </tr>
  <tr>
    <td><code>cmpDisplayStatus</code></td>
    <td>string</td>
    <td>Event is called whenever the display status of the CMP changes (e.g. the CMP shows the consent layer). The data property will contain the new display status (e.g. “visible”).</td>
    </tr>
  <tr>
    <td><code>error</code></td>
    <td>string</td>
    <td>Event can be called by the CMP in case of an error. The data property will contain a human readable error message.</td>
  </tr>
  <tr>
    <td><code>sectionChange</code></td>
    <td>string</td>
    <td>Event is called whenever the status or content of a section changes (e.g. consent is obtained). The data property will indicate the name (API prefix) of the changed section.</td>
   </tr>
  <tr>
    <td><code>[API.prefix] or [API-prefix].[Eventname]</code></td>
    <td>mixed</td>
    <td>Event is called by the CMP depending on the specific API needs (e.g. IAB TCF EU may specify different events than IAB USP). If the API defines different event types, these can be used by combining API-prefix and eventname, If the API does not specify different event types (e.g. in IAB TCF v2.0), the API-prefix is used as name. The data property will contain mixed data depending on API.</td>
     </td>
     </td>
  </tr>
</table>

______
#### `removeEventListener` <a name="removeeventlistener"></a>

The `removeEventListener` command can be used to remove an existing event listener. The callback shall be called with `false` as the argument for the `success` parameter if the listener could not be removed (e.g. the CMP cannot find a registered listener corresponding to `listenerId`).


<table> 
  <tr>
    <td><strong>argument</strong></td>
    <td><strong>type</strong></td>
    <td><strong>value</strong></td>
  </tr>
  <tr>
    <td><code>command</code></td>
    <td>string</td>
    <td>"removeEventListener"</td>
  </tr>
  <tr>
    <td><code>callback</code></td>
    <td>function</td>
    <td>function (success: boolean)</td>
  </tr>
  <tr>
    <td><code>parameter</code></td>
    <td>number</td>
    <td>ID of the listenerId property that was returned from addEventListener command</td>
  </tr>
 </table>
 
 


*Example:*

```javascript
__gpp('removeEventListener', myFunction, listenerId);
``` 

__________
#### `hasSection` <a name="hassection"></a>

The `hasSection` command can be used to detect if the CMP has generated a section of a certain specification. The callback shall be called with `true` as the argument for the `data` parameter if the CMP has generated a section for the requested API prefix string. The `data` parameter may be `null` when the CMP is not yet loaded. The callback shall be called with `false` as the argument for the `success` parameter if the CMP fails to process this command.



<table>
  <tr>
    <td><strong>argument</strong></td>
    <td><strong>type</strong></td>
    <td><strong>value</strong></td>
  </tr>
  <tr>
    <td><code>command</code></td>
    <td>string</td>
    <td>"hasSection"</td>
  </tr>
  <tr>
    <td><code>callback</code></td>
    <td>function</td>
    <td>function (data: boolean, success: boolean)</td>
  </tr>
  <tr>
    <td><code>parameter</code></td>
    <td>string</td>
    <td>API Prefix string</td>
  </tr>
 </table> 
 
Example:

A client wants to ask the CMP if there is data for IAB TCF v2.0:

```javascript
__gpp('hasSection', myFunction, "tcfeuv2");
```

______
#### `getSection` <a name="getsection"></a>

The `getSection` command can be used to receive the (parsed) object representation of a section of a certain specification. The callback shall be called with the (parsed) object representation as the argument for the `data` parameter. The `data` parameter may be `null` when the CMP is not yet loaded. The callback shall be called with `false` as the argument for the `success` parameter if the CMP fails to process this command. 



<table>
  <tr>
    <td><strong>argument</strong></td>
    <td><strong>type</strong></td>
    <td><strong>value</strong></td>
  </tr>
  <tr>
    <td><code>command</code></td>
    <td>string</td>
    <td>"getSection"</td>
  </tr>
  <tr>
    <td><code>callback</code></td>
    <td>function</td>
    <td>function (data: object or null, success: boolean)</td>
  </tr>
  <tr>
    <td><code>parameter</code></td>
    <td>string</td>
    <td>API Prefix string</td>
  </tr>
 </table>



For example, client can ask the CMP to get the IAB TCF v2.0 TCData: 


```javascript
__gpp('getSection', myFunction, "tcfeuv2");
```

______
#### `getField` <a name="getfield"></a>

The `getField` command can be used to receive a specific field out of a certain section. The callback shall be called with the value of the requested field as the argument for the `data` parameter. The `data` parameter may be `null` when the CMP is not yet loaded. The callback shall be called with `false` as the argument for the `success` parameter if the CMP fails to process this command.


<table>
  <tr>
    <td><strong>argument</strong></td>
    <td><strong>type</strong></td>
    <td><strong>value</strong></td>
  </tr>
  <tr>
    <td><code>command</code></td>
    <td>string</td>
    <td>"getField"</td>
  </tr>
  <tr>
    <td><code>callback</code></td>
    <td>function</td>
    <td>function (data: mixed or null, success)</td>
  </tr>
  <tr>
    <td><code>parameter</code></td>
    <td>string</td>
    <td>API Prefix string + "." (dot) + fieldname</td>
  </tr>

 </table>



For example, a client can ask the CMP to get the last updated field from the IAB TCF v2.0 TCData. 

```javascript
__gpp('getField', myFunction, "tcfeuv2.LastUpdated");
```

### What are non-generic commands?

In addition to the generic commands, a CMP can support other commands that are defined by any GPP section. See the non-generic commands by reviewing a specific sections’ specifications. Any GPP section that wants to make use of the GPP API spec should define a set of commands as follows: 

```
Example command xyz

Command:     prefix.command

Callback:    function (…)    or   “not used”

Parameter:   data type       or   “not used”

A description of the command, what it does, what it’s meant for, when to use it and how.
```

Using the IAB TCF v2.0 as an example, the `getVendorList`command would be defined as: 

```
getVendorList

Command:     iabtcfeuv2.getVendorList

Callback:    function (gvl: GlobalVendorList, success: boolean)

Parameter:   (optional) int or string

Calling with this command and a valid vendorListVersion parameter shall return a GlobalVendorList object to the callback function….
```

In the example above, a call to` __gpp (‘iabtcfeuv2.getVendorList’,myfunction)` will be treated in the same way as a call to `__tcfapi(‘getVendorList’,2,myfunction)` by the CMP.


__________

## In-App Details

How is a CMP used in-app? <a name="gppinapp"></a>

The GPP standardizes storage locations and naming for the content of the GPP data and GPP string so that ad tags embedded in mobile apps can find the GPP data and string in a consistent way. 


The pre-parsed GPP data as well as the GPP string shall be stored under [NSUserDefaults](https://developer.apple.com/documentation/foundation/nsuserdefaults#1664798?language=objc)(iOS) or [SharedPreferences](https://developer.android.com/training/data-storage/shared-preferences) (Android). This will allow:

- Vendors to easily access GPP data
- GPP data to persist across app sessions
- GPP data to be portable between CMPs to provide flexibility for a publisher to exchange one CMP SDK for another
- Vendors within an app to avoid code duplication by not being required to include a GPP string decoder while still enabling all typical use cases

> **Note:** If a Publisher chooses to remove a CMP SDK from their app they are responsible for clearing all IABGPP_* vestigial values for users so that vendors do not continue to use the GPP data therein. 

### In-App Key Names

The key names are a combination of the “IABGPP_” prefix followed by the section prefix followed by an underline and then followed by the name of the value (field name from the corresponding specification) it represents. The relevant sections documented in this spec are HDR (header), TCFEU2 (tcfv2), TCFCA1 (Canadian TCF), USP1 (U.S. Privacy).

 [NSUserDefaults](https://developer.apple.com/documentation/foundation/nsuserdefaults#1664798?language=objc) (iOS) or [SharedPreferences](https://developer.android.com/training/data-storage/shared-preferences) (Android) values
 
 

<table>
  <tr>
    <td><strong>Key Name</strong></td>
    <td><strong>Data type</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td><code>IABGPP_HDR_Version</code></td>
    <td>String</td>
    <td>GPP Version</td>
  </tr>
  <tr>
    <td><code>IABGPP_HDR_Sections</code></td>
    <td>String</td>
    <td>List of Section IDs</td>
  </tr>
  <tr>
    <td><code>IABGPP_HDR_GppString</code></td>
    <td>String</td>
    <td>Full consent string in its encoded form</td>
  </tr>
  <tr>
    <td><code>IABGPP_GppSID</code></td>
    <td>String</td>
    <td>Section ID(s) considered to be in force. Multiple IDs are separated by underscore, e.g. “2_3”</td>
   </tr>
  <tr>
    <td><code>IABGPP_[SectionID]_String</code></td>
    <td>String</td>
    <td>String representaiton of each section. E.g. IAB TCF EU v2 String will be found at IABGPP_2_String</td>
     </td>
     </td>
  </tr>
 </table>
 
 

The data stored in the in-app storage is not encoded or compressed because the storage is private to the application. However, the resulting string will follow the encoding rules as listed in this spec.


Valid data types are Integer and String. All other data types such as Boolean, Date and Array (Range, Bitfield, Fibonacci-Range, …) should be converted into an Integer or String representation as follows:



<table>
  <tr>
    <td><strong>Input Data Type</strong></td>
    <td><strong>In-app Data Type</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td><code>Boolean</code></td>
    <td>Integer (0/1)</td>
    <td>Convert True = 1, False = 0</td>
  </tr>
  <tr>
    <td><code>Integer / Integer Fibonacci</code></td>
    <td>Integer</td>
    <td>unchanged</td>
  </tr>
  <tr>
    <td><code>String</code></td>
    <td>String</td>
    <td>unchanged</td>
  </tr>
  <tr>
    <td><code>Datetime</code></td>
    <td>Integer</td>
    <td>Convert date to amount of milliseconds since 1.1.1970 00:00:00 UTC </td>
   </tr>
  <tr>
    <td><code>Bitfield / Vairable length Bitfield / Range / Range Fibonacci / Optimized Range</code></td>
    <td>String</td>
    <td>Convert all included IDs into a string separated by underscore, e.g. “1_4_5_6_99”</td>
     </td>
     </td>
  </tr>
 </table>



*Example key names:*

Below are example key names from existing APIs. For a complete list of key names for a specific section, see [Sections.](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/blob/main/Sections/Section%20Information.md)



<table>
  <tr>
    <td><strong>Key Name</strong></td>
	  <td><strong>Description</strong></td>
  </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_Version</code></td>    
<td>IAB TCF EU v2 Version number (see  <a href="https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md#the-core-string">IAB TCF EU v2 specification)</td>
  </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_Created</code></td>    
<td>IAB TECF EU v2 creation date</td>
     </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_LastUpdated</code></td>    
<td>IAB TCF EU v2 last update date</td>
   </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_CmpId</code></td>    
<td>IAB TCF EU v2 CMP ID</td>
    </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_CmpVersion</code></td>    
<td>IAB TCF EU v2 CMP Version</td>
     </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_PurposesConsent</code></td>    
<td>IAB TCF EU v2 CMP Purpose consents list</td>
   </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_VendorConsent</code></td>    
<td>IAB TCF EU v2 CMP Vendor consents list</td>
    </tr>
  <tr>
	  <td><code>IABGPP_TCFEU2_...</code></td>    
<td>Other IAB TCF EU v2 fields according to IAB TCF UE specification</td>
     </tr>
  <tr>
	  <td><code>IABGPP_TCFCA1_Version</code></td>    
<td>IAB TCF CA v2 Version number (see  <a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/Canada">IAB TCF CA v1 specification)</td>
   </tr>
  <tr>
	  <td><code>IABGPP_TCFCA1_Created</code></td>    
<td>IAB TCF CA v1 creation date</td>
    </tr>
  <tr>
	  <td><code>IABGPP_TCFCA1_…</code></td>    
<td>Other IAB TCF CA v1 fields according to IAB TCF CA specification</td>
     </tr>
  <tr>
	  <td><code>IABGPP_USP1_Version</code></td>    
<td>IAB US Privacy String Version number (see <a href="https://github.com/InteractiveAdvertisingBureau/USPrivacy/blob/master/CCPA/US%20Privacy%20String.md#us-privacy-string-format">IAB US Privacy v1 specification)</td>
   </tr>
  <tr>
	  <td><code>IABGPP_USP1_Notice</code></td>    
<td>IAB US Privacy notice has been provided</td>
    </tr>
  <tr>
	  <td><code>IABGPP_USP1_OptOut</code></td>    
<td>IAB US Privacy opt out of sale</td>
    </tr>
  <tr>
	  <td><code>IABGPP_USP1_LSPACovered</code></td>    
<td>IAB US Privacy publisher is signatory to the LSPA</td>
   </td>
   </td>
  </tr>
</table>




How do third-party SDKs (vendors) access the consent information in-app?

On both Android OS and iOS, the vendor can be notified when the values of the shared keys changes.  See [NSUserDefaultsDidChangeNotification](https://developer.apple.com/documentation/foundation/nsuserdefaultsdidchangenotification?language=objc) and [SharedPreferences.OnSharedPreferenceChangeListener.](https://developer.android.com/reference/android/content/SharedPreferences.OnSharedPreferenceChangeListener.html) 


On Android OS, the GPP data and GPP string shall be stored in the default Shared Preferences for the application context. This can be accessed using the `getDefaultSharedPreferences` method from the *android.preference.PreferenceManager* class using the application context. The GPP data values can be retrieved from the application Shared Preferences by key name using the get methods on the *android.content.SharedPreferences* class.


## Connected TV (CTV) Details

How is a CMP used in the CTV context?

The context of the CTV application will determine the storage locations and naming of the GPP data.


### Web Runtime

Applications running in a web runtime environment that supports, at minimum, the Web Storage (Second Edition) specification shall follow all storage and naming conventions detailed in the [Javascript](#javascript) section of this spec. Data is to be retrieved using the Generic and Non-generic API commands, offering a consistent interface for Vendors to access GPP information.

Should data not persist in Web Storage beyond the lifecycle of the application (application close, standby, or device shutdown), all data storage and naming conventions are to follow the specifications outlined in the [CTV Native Private Storage](#native) section of this spec.


### Native <a name="native"></a>

Native CTV applications are to follow the naming conventions of the GPP data and GPP String outlined in the [How is GPP used in-app](#gppinapp) section of this spec. Data is to be limited to the context of the Application and inaccessible to external applications.
 
 
 
*Application Preferences (Registry)*

 
Application Preferences, also referred to as a Registry in certain CTV environments, shall be used in a Native CTV Application environment under the condition that the GPP data and GPP String fit within the device constraints. Private Storage is to be used if the GPP data and GPP String do not fit within the device constraints.
 
 
*Private Storage*
 
Private Storage shall be used under the condition that the CTV environment does not offer a Web Runtime that supports the Web Storage (Second Edition) specification, data does not persist beyond the lifecycle of the Application, or offer an Application Preferences (Registry) interface. The GPP data and GPP String are to be saved in a standardized and private storage space. Files are to follow the same naming convention as the key names detailed in the [How is GPP used in-app](#gppinapp) section of this spec with the contents being the value of the corresponding key.
 
> **Note:** CTV Applications require proper permission scopes to be configured to read and write to the virtual Application file system.




## Using the CMP API


## Examples

*Example stub code* <a name="stubcode"></a>

The following code represents an example stub code.

```javascript
window.__gpp_addFrame = function (n)
{
 if (!window.frames[n])
 {
  if (document.body)
  {
   var i           = document.createElement('iframe');
   i.style.cssText = 'display:none';
   i.name          = n;
   document.body.appendChild(i);
  }
  else
  {
   window.setTimeout(window.__gppaddFrame, 10, n);
  }
 }
};
window.__gpp_stub = function ()
{
 var b       = arguments;
 __gpp.queue = __gpp.queue || [];
 if (!b.length){ return __gpp.queue; }
 var cmd = b[0];
 var clb = b.length > 1 ? b[1] : null;
 var par = b.length > 2 ? b[2] : null;
 if (cmd === 'ping')
 {
  return {
  gppVersion      : '1.0', // must be “Version.Subversion”, current: “1.0”
  cmpStatus       : 'stub', // possible values: stub, loading, loaded, error
  cmpDisplayStatus: 'hidden', // possible values: hidden, visible, disabled
  supportedAPIs      : ['tcfeuv2', 'tcfcav2', 'uspv1'], // list of supported APIs
  cmpId           : 31 // IAB assigned CMP ID, may be 0 during stub/loading
  };
 }
 else if (cmd === 'addEventListener')
 {
  __gpp.events = __gpp.events || [];
  if (!('lastId' in __gpp)){ __gpp.lastId = 0; }
  __gpp.lastId++;
  var lnr = __gpp.lastId;
  __gpp.events.push({
                     'id'       : lnr,
                     'callback' : clb,
                     'parameter': par
                    });
  return {
   eventName : 'listenerRegistered',
   listenerId: lnr, // Registered ID of the listener
   data      : true, // positive signal
pingData: {
 gppVersion      : '1.0',
 cmpStatus       : 'stub',
 cmpDisplayStatus: 'hidden',
 supportedAPIs   : ['tcfeuv2', 'tcfva', 'usnat'],
 cmpId           : 31
}
  };
 }
 else if (cmd === 'removeEventListener')
 {
  var success = false;
  __gpp.events = __gpp.events || [];
  for(var i=0; i<__gpp.events.length; i++)
  {
   if(__gpp.events[i].id == par)
   {
    __gpp.events[i].splice(i,1);
    success = true;
    break;
   }
  }
  return {
   eventName : 'listenerRemoved', 
   listenerId: par, // Registered ID of the listener
   data      : success, // status info
pingData: {
 gppVersion      : '1.0',
 cmpStatus       : 'stub',
 cmpDisplayStatus: 'hidden',
 supportedAPIs   : ['tcfeuv2', 'tcfva', 'usnat'],
 cmpId           : 31
}
  };
}
 //these commands must not be queued but may return null while in stub-mode
 else if (cmd === 'hasSection' || cmd === 'getSection' || cmd === 'getField')
 {
  return null;
 }
 //queue all other commands
 else
 {
  __gpp.queue.push([].slice.apply(b));
 }
};
window.__gpp_msghandler = function (event)
{
 var msgIsString = typeof event.data === 'string';
 try{ var json = msgIsString ? JSON.parse(event.data) : event.data; }
 catch (e){ var json = null; }
 if (typeof (json) === 'object' && json !== null && '__gppCall' in json)
 {
  var i = json.__gppCall;
  window.__gpp(i.command, function (retValue, success)
{
var returnMsg = {
 '__gppReturn': {
  'returnValue': retValue,
  'success'    : success,
  'callId'     : i.callId
 }
};
event.source.postMessage(msgIsString ? JSON.stringify(returnMsg) : returnMsg, '*');
},'parameter' in i? i.parameter: null, 'version' in i ? i.version : '1.1');
 }
};
if (!('__gpp' in window) || (typeof (window.__gpp) !== 'function'))
{
 window.__gpp = window.__gpp_stub;
 window.addEventListener('message', window.__gpp_msghandler, false);
 window.__gpp_addFrame('__gppLocator');
}
```

Example of determining vendor consent under TCF Canada
The following example demonstrates how a vendor can listen to changes for IAB TCF Canada and find out if consent is given for a specific vendor or purpose.

```javascript
if(__gpp)
{
 __gpp('addEventListener', function (evt)
 {
  //callback will receive all events, we only want to react on TCF canada events
  if(evt.pingData.currentAPI !== 'tcfcav2'){return ;}

  //react on changes or when the data is loaded
  if(
     evt.eventName === 'sectionChange' //TCF canada section has changed (new consent?)
     ||
     (
      //cmp is loaded and not/no longer visible, a tc string should be available
      evt.pingData.cmpStatus === 'loaded' && 
      evt.pingData.cmpDisplayStatus !== 'visible'
     )
     // optional additional/instead check:
     // __gpp('hasSection', null, 'tcfcav2') === true
    )
  {
   var consentData =__gpp('getSection', null, 'tcfcav2');
   //will return the parsed IAB TCF Canada TCstring. All info is in there.	

   var vendorConsent = consentData.VendorExpressConsent; 
   // equivalent to: __gpp('getField', null, 'tcfcav2.VendorExpressConsent');
   var vendorImpConsent = consentData.VendorImpliedConsent;
   // equivalent to: __gpp('getField', null, 'tcfcav2.VendorImpliedConsent');
   var purposeConsent = consentData.PurposesExpressConsent; 
   // equivalent to: __gpp('getField', null, 'tcfcav2.PurposesExpressConsent');
   // ... do something Canadian !
  }
 });
}
```

## How can vendors that use iframes call the CMP API from an iframe?

### Using postmessage

The `window.postMessage()` method may be used from a child iframe to make requests from a parent or any ancestor frame's CMP API. To locate an ancestor frame capable of responding to postMessage() CMP API calls, search for an ancestor frame that has a child frame named `'__gppLocator'`.

CMPs shall create an event listener to handle postMessage requests via the CMP “stub” API script so that postMessage events can be queued and processed by the full-implementation of the CMP API as soon as it is initialized.

### Sent Message

The sent message shall follow the form outlined below. The command, parameter and version object properties correspond to their namesake parameters defined as method argument parameters for `__gpp()` method. The “sent message” also requires a unique `callId` property to help match the request with a response. The callId property shall be either a string or a number, but the calling script shall not use the two types interchangeably.

```javascript
{
  __gppCall: {
    command: "command",
    parameter: “parameter”,
    version: '1.1',
    callId: “randomID”
  }
}
```

The `event.data` object payload shall follow the form outlined below. The `returnValue` object property shall be the corresponding TC data object for the command used upon sending the “sent message”. The success object property shall reflect the `__gpp()` success callback argument and the callId will correspond to the “sent message” unique id passed in the callId property.

```javascript
{
  __gppReturn: {
   returnValue: returnValue,
   success: boolean,
   callId: uniqueId
  }
}
```


