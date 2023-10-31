<h1>Data Deletion Request Framework</h1>

<h3> Public Comment closes on December 2, 2023.
Email support@iabtechlab.com to submit comments.

<h2>Introduction</h2>
<p>The &lsquo;Right to Delete&rsquo; is a Data Subject Right (DSR) included as part of the GDPR, US state privacy laws, and additional privacy legislation such as Quebec Law 25.&nbsp;</p>
<p>The US Privacy <a href="https://github.com/InteractiveAdvertisingBureau/USPrivacy/blob/master/CCPA/Data%20Deletion%20Request%20Handling.md" target="_blank" rel="noopener">specification</a>, which is due to be deprecated 31 January 2024, supported California Consumer Privacy Act (CCPA) requirements with an included data deletion request handling mechanism. However, the original mechanism only supported the CCPA, which is now too limited a scope. As privacy legislation evolves across California, other US state laws, and global jurisdictions beyond GDPR, the data deletion request framework needs to also evolve.&nbsp;</p>
<p>Handling data deletion request signals is a challenge for the adtech ecosystem. Existing DSR tools in-market do not have integrations with adtech companies. To support adtech, we need a protocol that successfully communicates data deletion requests to participants, ensuring all related parties who share data can receive the request signal. This specification describes a data deletion signaling mechanism that is intended to be an interoperable standard within the Global Privacy Platform (GPP).</p>
<h3>Terms</h3>
<p>The following terms have specific meaning within this document:</p>
<ul>
<li>Deletion Request</li>
<ul>
<li>A deletion request is a request made by a user to a party, referred to as a 1st-party, which they have a direct relationship with.</li>
</ul>
<li>Deletion Request Transaction</li>
<ul>
<li>A deletion request transaction is an interaction consisting of the communication of a deletion request by a requester and the acknowledgement of the request by a recipient.</li>
</ul>
<li>Deletion Request Chain</li>
<ul>
<li>A deletion request chain is a series of one more deletion request transactions originating from a given requester.</li>
</ul>
<li>1st Party</li>
<ul>
<li>A 1st Party (also first-party) is an adtech ecosystem participant which has direct relationships with users and which may receive requests from those users to delete their data.</li>
</ul>
<li>Vendor</li>
<ul>
<li>A Vendor is an adtech ecosystem participant which has direct or indirect relationships with 1st Parties and which may receive deletion requests from those 1st Parties.</li>
</ul>
<li>Requester</li>
<ul>
<li>A requester is a party which initiates a data-deletion transaction by communicating a data deletion request on behalf of a user. A 1st-party is always the first requester in a deletion request chain.</li>
</ul>
<li>Recipient</li>
<ul>
<li>A recipient is a party which receives a deletion request from a requester. Recipients may themselves become requesters in succeeding transactions.</li>
</ul>
</ul>
<h2>Requirements</h2>
<ol>
<li>Provide a standard protocol that allows parties to communicate data deletion request signals.</li>
<li>Provide a standard for recipients to indicate what must be provided and how it must be packaged to execute data deletion requests.</li>
<li>Provide a standard for recipients of data deletion requests to validate the 1st-party origin of a request.</li>
<li>Provide a standard means by which recipients of data deletion requests can determine the authenticity of the requester.</li>
<li>Provide a standard for recipients to confirm receipt of a data deletion request.</li>
<li>Provide a standard for parties to have deletion requests and request receipts cryptographically signed by those making and receiving the requests, respectively.</li>
</ol>
<h4>Scope</h4>
<p>This proposal is focused specifically on defining a two stage process by which deletions are requested and affirmed. In the first stage, requests are communicated from a requester to a recipient and the recipient acknowledges receipt of the request. A recipient may also become a requester if they need to forward the request to partners.</p>
<h4>Out-of-scope</h4>
<ol>
<li>Verifying the original data-subject request: it is assumed that first-parties will be responsible for authenticating and validating requests prior to communicating them via this protocol.&nbsp;&nbsp;</li>
<li>How deletion request recipients act on them: it is assumed each participant will decide independently what their obligations for acting on a request and what their requirements are for satisfying those obligations.&nbsp;</li>
<li>Supporting any other types of data subject rights requests.</li>
<li>Determining what partners a participant must communicate deletion requests to: it is assumed participants will be responsible for deciding which of their partners they must forward deletion requests to in order to properly honor them.</li>
</ol>
<h4>Resources Required</h4>
<p>All participants will be required to publish a file with configuration parameters needed by other participants who support the standard. The file must be called dsrdelete.json and available at a &ldquo;well-known location&rdquo; that it is easily discoverable by other participants.</p>
<p>The following information is required from participants in their dsrdelete.json resource:</p>
<p>From All Parties:</p>
<ul>
<li>All parties must publish cryptographic public keys in their dsrdelete.json files, which will be used to verify signatures generated with the associated private keys.</li>
<li>All parties must publish an API endpoint to which partners can send acknowledgement of deletion requests.</li>
</ul>
<p>From Vendors:</p>
<ul>
<li>Vendors must publish in their dsrdelete.json files information 1st Parties will use to determine how to submit deletion requests to them and what the requirements for submitting the requests are (e.g. what identifiers/data must be provided and what API endpoint deletion requests must be sent to).</li>
<li>Vendors must publish an API endpoint as defined in their dsrdelete.json to which 1st Parties can send deletion requests.</li>
</ul>
<h2>Deletion Request Sequence</h2>
<h4>Request Sequence</h4>
<p>Deletion request sequences always begin with a user requesting that a 1st Party delete their data through a flow provided by the 1st Party as identified in step 1 below. Once the 1st Party has determined that the request needs to be communicated to partners, which partners it must be communicated to, and what information they must provide &ndash; a series of one or more discrete transactions occurs to propagate a request for each individual identifier subject to the request to all concerned parties.&nbsp;</p>
<p>The two parties in these transactions are a <strong>requester</strong>, who has received a deletion request from a data subject, and a <strong>recipient</strong>, who the requester has a data relationship with. The interactions between the requester and recipient are described in steps 2 through 10 below. If a recipient has additional partners with whom they have data relationships, they will in turn become the requester in subsequent transactions.</p>
<p>A given deletion request may be forwarded by a requester to one or more than one recipient and the recipient may in turn forward the request to one or more subsequent recipients. The result will be chains of one or more transactions which fan out across the partner graph.</p>
<ol>
<li><span style="color: #ff0000;"><strong>*Data Subject</strong></span><span style="color: #ff0000;"> requests a data deletion from a 1st Party*</span></li>
<ol>
<li><span style="color: #ff0000;">1st Party validates the request.</span></li>
<li><span style="color: #ff0000;">1st Party determines what data is subject to the request.&nbsp;</span></li>
<li><span style="color: #ff0000;">1st Party determines partners that data has been shared with which the request must be communicated to.</span></li>
</ol>
<li><strong>Requester</strong> accesses data deletion configuration from the dsrdelete.json file on the recipient's domain.</li>
<li><strong>Requester</strong> generates a deletion packet with the values described under <a href="https://docs.google.com/document/d/1PnERrW-Dt_TKl-1cJ2YipFsZjRfbFalJfTMbCh7UZ2I/edit#heading=h.orcsfubg4iue" target="_blank" rel="noopener">Request Data</a>, below and based on the recipient&rsquo;s configuration.</li>
<li><strong>Requester</strong> sends the deletion packet to the Recipient.</li>
<li><strong>Recipient</strong> receives the deletion packet and verifies the signed portions from the 1st Party and the requester using public keys published in the dsrdelete.json file on the domains of the 1st party and the requester.&nbsp;</li>
<li><strong>Recipient</strong> acknowledges receipt to the requester. This includes the original request ID, a result code indicating successful receipt of the request or an error, and a signature.&nbsp;</li>
<li><strong>Requester</strong> verifies Recipient&rsquo;s receipt signature using a public key published in the dsrdelete.json file on the Recipient&rsquo;s domain.</li>
<li><span style="color: #ff0000;"><strong>*Requester</strong></span><span style="color: #ff0000;"> logs all data provided to the recipient in final communication.*</span></li>
<li><span style="color: #ff0000;"><strong>*Recipient</strong></span><span style="color: #ff0000;"> logs all data received from 1st Party in final communication.*</span></li>
<li><span style="color: #ff0000;"><strong>*Recipient</strong></span><span style="color: #ff0000;"> executes data deletion.*</span></li>
</ol>
<h4>Out-of-scope</h4>
<p>The following steps have been marked with an asterisk because they are not part of the standard:</p>
<ul>
<li>Steps 1&ndash;including 1a, 1b, and 1c&ndash;and Step 9 are the sole responsibility of the 1st-party.&nbsp;</li>
<li>Step 10 is the sole responsibility of the Recipient.</li>
</ul>
<h4>Request Data</h4>
<p>Each request needs to be an atomic unit, as described by the request data table, which can be individually processed by the recipient. The deletion request packet referred to in step 3 above will include the following values:</p>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>version</td>
<td>string</td>
<td>1.0 (version of this specification)</td>
<td>required</td>
</tr>
<tr>
<td>fpRequestId</td>
<td>string</td>
<td>A GUID generated by the first-party that identifies a deletion request. All transactions resulting from a given user deletion request will include this value.</td>
<td>required</td>
</tr>
<tr>
<td>rqTransactionId</td>
<td>string</td>
<td>A GUID that identifies the transaction between requester and recipient.</td>
<td>required</td>
</tr>
<tr>
<td>fpTimestamp</td>
<td>numeric</td>
<td>Time in seconds since the Unix epoch at which the first-party made the request.</td>
<td>required</td>
</tr>
<tr>
<td>fpIdentifier</td>
<td>object</td>
<td>Identifier information.</td>
<td>required</td>
</tr>
<tr>
<td>optionalParameters</td>
<td>object</td>
<td>Additional information and extensions</td>
<td>optional</td>
</tr>
<tr>
<td>origin</td>
<td>object</td>
<td>Request origin information.</td>
<td>required</td>
</tr>
<tr>
<td>requester</td>
<td>object</td>
<td>Requester information</td>
<td>required</td>
</tr>
</tbody>
</table>
</div>
<h5>fpIdentifier object</h5>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>identifierValue</td>
<td>string</td>
<td>Identifier value, (e.g., "johndoe@example.com")</td>
<td>required</td>
</tr>
<tr>
<td>identifierType</td>
<td>string</td>
<td>Type of identifier, (e.g., "email")</td>
<td>required</td>
</tr>
<tr>
<td>identifierFormat</td>
<td>string</td>
<td>Identifier format, (e.g., "sha256")</td>
<td>required</td>
</tr>
</tbody>
</table>
</div>
<h5>origin &amp; requester Object</h5>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>domain</td>
<td>string</td>
<td>eTLD+1 of the original requester or immediate requester entity making the request.</td>
<td>required</td>
</tr>
<tr>
<td>signature</td>
<td>string</td>
<td>A hash value generated from version + fpRequestId + domain + fpTimestamp + fpIdentifier.Value and then encrypted with the private key of the 1st party / requester.</td>
<td>required</td>
</tr>
</tbody>
</table>
</div>
<h5>optionalParameters object</h5>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>relayDomain</td>
<td>Array of string</td>
<td>List of domains of known service providers of the deletion request recipient</td>
<td>optional</td>
</tr>
<tr>
<td>ext</td>
<td>object</td>
<td>Reserved for bilateral agreements</td>
<td>optional</td>
</tr>
</tbody>
</table>
</div>
<h5>Recipient Acknowledgement</h5>
<p>The recipient acknowledgement referred to in step 6 above will include all of the values described under &ldquo;Request Data&rdquo; above as well as the following values:</p>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>The fields Version, fpRequestId, rqTransactionId, fpTimestamp from the above request data table.</td>
<td>
</td>
<td>
</td>
<td>required</td>
</tr>
<tr>
<td>raTimestamp</td>
<td>numeric</td>
<td>Time in seconds since Unix epoch at which receipt acknowledgement was sent.</td>
<td>required</td>
</tr>
<tr>
<td>raResultCode</td>
<td>numeric</td>
<td>A code indicating the request was successfully validated or identifying an error.</td>
<td>required</td>
</tr>
<tr>
<td>raSignature</td>
<td>string</td>
<td>A hash value generated from rqSignature + raTimestamp + raResultCode and then encrypted with the private key of the recipient.</td>
<td>required</td>
</tr>
</tbody>
</table>
</div>

## Example Deletion Packet

A data deletion request is accomplished by sending a POST request to the data deletion request API, which returns a response in JSON format. This protocol is implemented via a standard API and request format with a defined JSON payload.


##### Example Deletion Packet with required parameters


```
Request:
POST https://vendor2.com/gpp/v1/
Content-Type: application/json

{
  "version": "1.0",
  "fpRequestId": "12345",
  "rqTransactionId": "1A2B3C",
  "fpTimestamp": "1693459424",
  "fpIdentifier": {
    "identifierValue": "johndoe@example.com",
    "identifierType": "email",
    "identifierFormat": "sha256"
  },
  "origin": {
    "domain": "publisher1.com",
    "signature": "0x650c9f2...d41372b"
  },
  "requester": {
    "domain": "vendor1.com",
    "signature": "0x87e2a95...39e11c3"
  }
}


Response:
HTTP/1.1 200
content-type: application/json

{"status": 202}
```



##### Example Request including optional parameters:

```
Request:
POST https://vendor2.com/gpp/v1/
Content-Type: application/json

{
  "version": "1.0",
  "fpRequestId": "12345",
  "rqTransactionId": "1A2B3C",
  "fpTimestamp": "1693459424",
  "fpIdentifier": {
    "identifierValue": "johndoe@example.com",
    "identifierType": "email",
    "identifierFormat": "sha256"
  },
  "origin": {
    "domain": "publisher1.com",
    "signature": "0x650c9f2...d41372b"
  },
  "requester": {
    "domain": "vendor1.com",
    "signature": "0x87e2a95...39e11c3"
  },
  "optionalParameters": {
    "relayDomain": ["vendor3.com", "vendor4.com", "vendor5.com"]
  }
}

Response:
HTTP/1.1 200
content-type: application/json

{"status": 202}
```



##### Example Acknowledgement


```
Request:
POST https://vendor2.com/gpp/v1/
Content-Type: application/json

{
  "status": 202,
  "message": "acknowledgement of receipt",
  "rqTransactionId": "1A2B3C",
  "rqTimestamp": "1693459424",
  "rqSignature": "0x7a8b4d5...9b1e8f7",
  "recipientAcknowledgement": {
    "raTransactionId": "6G7H8J",
    "raTimestamp": "8574628394",
    "raSignature": "1t8nb98e...9a2f8k0"
  }
}

Response:
HTTP/1.1 200
content-type: application/json

{"status": 202}
```

<h2>Identifiers</h2>
<p>There are generally two classes of identifiers used in ad-interactions distinguished by access limitations: those which are directly accessible by 1st-parties and those which are only accessible to 3rd parties. The first class includes any identifiers available in the 1st-party context, including on web pages and 1st-party local storage. The second class includes identifiers maintained in protected 3rd-party storage, such as 3rd-party cookies. Probabilistic identifiers, which are based on constellations of data values, presumably may fall into the first, second or a combination of both classes, depending on how they are constructed.</p>
<h4>Identifier Communication</h4>
<p>The initial version of this proposal only provides support for identifiers a 1st-party has access to prior to initiating communication of the data deletion request. It is the responsibility of the 1st Party to determine what identifiers they must provide to which partners in deletion requests and to provide them in a form usable by those partners for satisfying the request.&nbsp;</p>
<p>The details of what identifiers a participant can accept and what format they can accept them in are provided by each participant in the dsrdelete.json file on their domain.</p>
<p>The following are examples of identifier types that may be included in a request. This would populate the &ldquo;type&rdquo; field in the body of the request when shared:</p>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
</tr>
<tr>
<td>Email</td>
<td>Email address</td>
</tr>
<tr>
<td>Cookie</td>
<td>Cookies tied to a specific web browser</td>
</tr>
<tr>
<td>User ID</td>
<td>Unique customer identifier</td>
</tr>
<tr>
<td>Vendor ID</td>
<td>Vendor specific identifier</td>
</tr>
<tr>
<td>Device Advertising ID</td>
<td>(Ex: IDFA, AAID)</td>
</tr>
<tr>
<td>Platform Advertising ID</td>
<td>(Ex: Roku ID, Samsung TIFA, Amazon Fire ID)</td>
</tr>
<tr>
<td>Alternative ID</td>
<td>(Ex: UID2, ID5, Ramp ID)</td>
</tr>
</tbody>
</table>
</div>
<h2>Request/Response Signatures</h2>
<p>To ensure deletion requests are legitimate and unmodified, participants will cryptographically sign requests and responses with private keys, the corresponding public keys for which they publish in their dsrdelete.json files so that other participants can use them to verify signatures.</p>
<h4>Signature Process</h4>
<p>After the data for a deletion request or acknowledgement has been assembled by a participant, they will generate a hash from a subset of fields as described in the Request Data section, above. They will then encrypt the hash with a private key for which they have published a corresponding public key in their dsrdelete.json file as described in the Discovery section, below. They will then include the signature with the data communicated as described in the Request Data section, above.</p>
<p>To verify the communication, the recipient will decrypt the signature using the public key and compare the result to a hash generated from the same subset of fields as the party which created the signature.&nbsp;</p>
<p>If the resulting hashes do not match, the receiving party will indicate to the sender that the communication is invalid.</p>
<p>If the resulting hashes match, the receiving party will generate a hash from the original request and their result code as described in the Request Data section, and sign it with their own private key. They will then send the original request, result code and their signature to the other party which will validate the signature and affirm receipt.</p>
<p><b> Example Hash Generation</b><p>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field</strong></span></td>
<td><span style="color: #ffffff;"><strong>Value</strong></span></td>
</tr>
<tr>
<td>version</td>
<td>1.0</td>
</tr>
<tr>
<td>fpRequestId</td>
<td>12345</td>
</tr>
<tr>
<td>domain</td>
<td>publisher1.com</td>
</tr>
<tr>
<td>fpTimestamp</td>
<td>1698767029</td>
</tr>
<tr>
<td>fpIdentifierValue</td>
<td>johndoe@example.com</td>
</tr>
<tr>
</tr>
<tr>
<td>Hash Input</td>
<td>1.012345publisher1.com1698767029johndoe@example.com</td>
</tr>
<tr>
<td>Hash Output (SHA-256)</td>
<td>569c1808da97047d417f271ed15d42a8f57b051e17f9cb19b30920ce624c8af1</td>
</tr>
</tbody>
</table>
</div>
<h2>Discovery</h2>
<p>This specification defines a standard method by which participants communicate what information they require to execute data deletion requests and resources needed by other participants when interacting with them, such as cryptographic keys. To achieve this, there will be two options of discovery for participants. Both options are available to support multiple use-cases for discovery. To achieve this, participants will be required to create a dsrdelete.json file, which will be considered the authoritative version of a participant's information.</p>
<h4>dsrdelete.json File</h4>
<p>For easy access and discovery, participants must provide a JSON file named dsrdelete.json in the root of their domain. Parties supporting this standard would be expected to periodically read the files published by their partners and assure they support what is required by those partners in order to honor requests. Having participants publish this information directly on their domains allows them to fully and directly manage it, allows partners to work directly with them to resolve issues, and eliminates the potential for a single point of failure to disable communications.&nbsp;</p>
<p>1st Parties should read the data provided in well-known resources from the vendor. This resource should include the following:</p>
<h5>Example Resource</h5>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>endpoint</td>
<td>string</td>
<td>API endpoint for deletion requests.</td>
<td>Required</td>
</tr>
<tr>
<td>identifiers</td>
<td>Array of object</td>
<td>List of supported identifiers.</td>
<td>Required</td>
</tr>
<tr>
<td>keys</td>
<td>Array of object</td>
<td>Reference key object table below</td>
<td>Required</td>
</tr>
<tr>
<td>vendorScriptRequirement</td>
<td>boolean</td>
<td>True or false for requirement to use vendor script</td>
<td>Required</td>
</tr>
<tr>
<td>vendorScript</td>
<td>string</td>
<td>Optional field for vendors to publish a HTML code (e.g. a &lt;scrip&gt;) if this is needed to gather an identifier for a deletion request.</td>
<td>Optional</td>
</tr>
</tbody>
</table>
</div>
<h5>Implementing Script-based deletion requests</h5>
<p>Participants that only support script based deletion requests, can do so by providing a property vendorScript along with a property vendorScriptRequirement in their dsrdelete.json file. A first party that wants to start the deletion process, will execute the script.</p>
<p><strong>Note</strong>: Please note that supporting only script based deletion requests will limit the ability to receive deletion requests where requests are chained via endpoints.</p>
<h5>Example Identifier Object</h5>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>identifierType</td>
<td>string</td>
<td>Type of identifier required for deletion (e.g. email).</td>
<td>Required</td>
</tr>
<tr>
<td>identifierFormat</td>
<td>string</td>
<td>The expected format of the identifier (e.g. raw).</td>
<td>Required</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
</tbody>
</table>
</div>

<h5>Example Keys Object</h5>
<div>
<table>
<tbody>
<tr>
<td><span style="color: #ffffff;"><strong>Field Name</strong></span></td>
<td><span style="color: #ffffff;"><strong>Type</strong></span></td>
<td><span style="color: #ffffff;"><strong>Description</strong></span></td>
<td><span style="color: #ffffff;"><strong>Required/Optional</strong></span></td>
</tr>
<tr>
<td>kId</td>
<td>string</td>
<td>A unique identifier for the vendor key.</td>
<td>Required</td>
</tr>
<tr>
<td>kty</td>
<td>string</td>
<td>Key Type used for digital signature (e.g. OKP)</td>
<td>Required</td>
</tr>
<tr>
<td>crv</td>
<td>string</td>
<td>Signature will use the elliptic curve-based EdDSA algorithm (Ed25519).</td>
<td>Required</td>
</tr>
<tr>
<td>use</td>
<td>string</td>
<td>Signature is the use of the key</td>
<td>Required</td>
</tr>
<tr>
<td>x</td>
<td>string</td>
<td>Public key value for an Ed25519 key</td>
<td>Required</td>
</tr>
<tr>
<td>expireDate</td>
<td>number</td>
<td>Time in seconds since Unix epoch at which the key will expire.</td>
<td>Optional</td>
</tr>
<tr>
<td>ttl</td>
<td>number</td>
<td>Number of seconds a participant is allowed to cache the key. If no ttl is given, the default of 86400 (one day) is assumed.</td>
<td>Optional</td>
</tr>
</tbody>
</table>
</div>
<p><strong>Key Rotation Guidance</strong></p>
<p>Should a key become compromised, the participant should remove it from their dsrdelete.json file. It is expected that a participant has no more than 4 active keys at any time, and compromised keys are removed completely. If KeyIds (kId) should be reused, participants should make sure these don't collide with key ids from pending transactions.</p>
<p><strong>Key Caching Guidance</strong></p>
<p>Public keys published by participants on their domains may be cached for a duration lower than or equal to the TTL value of the record containing the keys. Public keys must not be cached for a duration longer than the TTL value.</p>

<h5> Example Resource for dsrdelete.json: </h5>

```
https://www.publisher1.com/.well-known/dsrdelete.json

{
  "endpoint": "https://www.publisher1.com/api/delete/",
  "identifiers": [
    {
      "identifierType": "email",
      "identifierFormat": "sha256"
    },
    {
      "identifierType": "idfa",
      "identifierFormat": "hash"
    }
  ],
  "keys": [
    {
      "kid": "1",
      "kty": "OKP",
      "crv": "Ed25519",
      "use": "sig",
      "x": "0I6olrZGYml7JGusuKJW9G7D0DZ9UormSady9kR7V4Q"
    }
  ],
  "vendorScript": "<script>.....</script>"
}
```

<h4>Directory</h4>
<p>An optional discovery method will be available via access to a directory provided by the Tech Lab. The directory would live in the Tech Lab tools portal and provide participants with the location of each dsrdelete.json resource. To create the directory entries, Tech Lab will crawl dsrdelete.json resources and automatically create entries&ndash;similar to ads.txt. The results would appear in the Tools Portal and in an API. Participants might use the directory to look up primary domains for companies that operate across multiple domains, validate a vendor has adopted the standard with the established request format, or to simplify a bulk lookup of endpoints from participants. All endpoints can be looked up, but not all endpoints need to be used.</p>
