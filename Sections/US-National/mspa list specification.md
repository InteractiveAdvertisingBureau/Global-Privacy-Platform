# MSPA Signatory List 

The MSPA Signatory List is a technical document that any MSPA signatory can access to understand which partners are MSPA signatories. The MSPA Signatory List will be published in a standard location and updated weekly. 

## Version History

<table>
<tbody>
<tr>
<td><strong>Date</strong></td>
<td><strong>Version</strong></td>
<td><strong>Comments</strong></td>
</tr>
<tr>
<td>August 2026 <i>(Public Comment)</i></td>
<td>2.0</td>
<td>New spec</td>
</tr>
<tr>
</tbody>
</table>

### Object: MSPA Signatory List
<table>
<tbody>
<tr>
<td><strong>Field</strong></td>
<td><strong>Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>mspaListSpecVersion</code></td>
<td>String; required</td>
<td>The version of the MSPA Signatory List specification used.</td>
</tr>
<tr>
<td><code>mspaVersion</code></td>
<td>String; required</td>
<td>The version of the MSPA that applies.</td>
</tr>
<tr>
<td><code>listVersion</code></td>
<td>Integer; required</td>
<td>The version of the MSPA Signatory List. Incremented with each updated. Restarts at 1 when moving to a new mspaListSpecVersion</td>
</tr>
<tr>
<td><code>lastUpdated</code></td>
<td>String; required</td>
<td>The ISO-8601 date and time this version of the file was published.</td>
</tr>
<tr>
<td><code>certifiedPartners</code></td>
<td>Object array</td>
<td>Certified Partners list.</td>
</tr>
<tr>
<td><code>signatories</code></td>
<td>Object array</td>
<td>MSPA signatories list.</td>
</tr>
</tbody>
</table>

### Object: Certified Partners
<table>
<tbody>
<tr>
<td><strong>Field</strong></td>
<td><strong>Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>id</code></td>
<td>String; required</td>
<td>The unique identifier assigned to the Certified Partner.</td>
</tr>
<tr>
<td><code>registrationTimestamp</code></td>
<td>String; required</td>
<td>The ISO-8601 date and time when the Certified Partner was registered.</td>
</tr>
<tr>
<td><code>deletedTimestamp</code></td>
<td>String</td>
<td>The ISO-8601 date and time when the Certified Partner  was removed from the list.</td>
</tr>
<tr>
<td><code>partnerName</code></td>
<td>String; required</td>
<td>The name of the Certified Partner.</td>
</tr>
<tr>
<td><code>partnerProducts</code></td>
<td>String array; required</td>
<td>The products that are covered</td>
</tr>
</tbody>
</table>

### Object: Signatories
<table>
<tbody>
<tr>
<td><strong>Field</strong></td>
<td><strong>Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>id</code></td>
<td>String; required</td>
<td>The unique identifier assigned to the participant upon registration.</td>
</tr>
<tr>
<td><code>signatory</code></td>
<td>Object array; required</td>
<td>Information about the signatory.</td>
</tr>
</tbody>
</table>

### Object: Signatory
<table>
<tbody>
<tr>
<td><strong>Field</strong></td>
<td><strong>Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>signatoryType</code></td>
<td>String; required</td>
<td>First Party Publisher, First Party Advertiser, Downstream Vendor</td>
</tr>
<tr>
<td><code>registrationTimestamp</code></td>
<td>String; required</td>
<td>The ISO-8601 date and time when the signatory registered under this signatoryType</td>
</tr>
<tr>
<td><code>deletedTimestamp</code></td>
<td>String</td>
<td>The ISO-8601 date and time when the signatory was removed under this signatoryType</td>
</tr>
<tr>
<td><code>entityType</code></td>
<td>String; required</td>
<td>Company or individual</td>
</tr>
<tr>
<td><code>name</code></td>
<td>String; required</td>
<td>Company legal name or name of individual</td>
</tr>
<tr>
<td><code>coveredPropertiesWebsites</code></td>
<td>Object array</td>
<td>Websites that are covered. Only applicable when <code>signatoryType</code> is First Party Publisher or First Party Advertiser.</td>
</tr>
<tr>
<td><code>coveredPropertiesApps</code></td>
<td>Object array</td>
<td>Apps that are covered. Only applicable when <code>signatoryType</code> is First Party Publisher or First Party Advertiser.</td>
</tr>
<tr>
<td><code>domain</code></td>
<td>String</td>
<td>The domain name (e.g. the domain of the advertising system as referenced in ads.txt files when applicable). Only applicable when the <code>signatoryType</code> is Downstream Vendor.</td>
</tr>
<tr>
<td><code>optOutUrls</code></td>
<td>String array</td>
<td>The URL where a consumer may opt out. This may be empty if the entity indicated that the company does not sell or share personal information. </td>
</tr>
</tbody>
</table>

### Object: Covered Properties Websites
<table>
<tbody>
<tr>
<td><strong>Field</strong></td>
<td><strong>Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>property</code></td>
<td>String</td>
<td>The website that is covered</td>
</tr>
<tr>
<td><code>optOutUrl</code></td>
<td>String</td>
<td>The URL where a consumer may opt out. This may be empty if the entity indicated that the company does not sell or share personal information. </td>
</tr>
</tbody>
</table>

### Object: Covered Properties Apps
<table>
<tbody>
<tr>
<td><strong>Field</strong></td>
<td><strong>Type</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr>
<td><code>property</code></td>
<td>String</td>
<td>The name of the app that is covered</td>
</tr>
<tr>
<td><code>appId</code></td>
<td>String</td>
<td>The bundle id</td>
</tr>
<tr>
<td><code>appStore</code></td>
<td>String</td>
<td>Apple, Google Play, Amazon, Samsung, Roku, Other</td>
</tr>
<tr>
<td><code>optOutUrl</code></td>
<td>String</td>
<td>The URL where a consumer may opt out. This may be empty if the entity indicated that the company does not sell or share personal information. </td>
</tr>
</tbody>
</table>

#### Example JSON
```json
{
   "mspaListSpecVersion": "2.0",
   "mspaVersion": "5",
   "listVersion": 1,
   "lastUpdated": "2026-06-01T12:00:00Z",
   "certifiedPartners": {
       "2973": {
           "id": "2973",
           "registrationTimestamp": "2026-06-01T12:00:00Z",
           "deletedTimestamp": "2026-06-01T12:00:00Z",
           "partnerName": "Certified Partner Company",
           "partnerProducts": ["Certified Partner Product 1", "Certified Partner Product 2"]
           }
           },
   "signatories": {
       "1234": {
           "id": "1234",
           "signatory": [
               {
                   "signatoryType": "First Party Publisher", // First Party Publisher, First Party Advertiser, Downstream Vendor
                   "registrationTimestamp": "2026-06-01T12:00:00Z",
                   "deletedTimestamp": "2026-06-01T12:00:00Z", // If present, entity is no longer an MSPA signatory after this date/time.
                   "entityType": "Company", // Company or Individual
                   "name" "Company", // Company legal name or name of individual
                   "coverePropertiesWebsites": [
                       {
                           "property": "coveredwebsite1.com",
                           "optOutUrl": "https://coveredwebsite1.com/optout" // Empty if company indicated that it does not sell or share personal information.
                       },
                                               {
                           "property": "coveredwebsite2.com",
                           "optOutUrl": "https://coveredwebsite2.com/optout" // Empty if company indicated that it does not sell or share personal information.
                       }
                   ],
                   "coveredPropertiesApps": [
                       {
                           "property": "coveredapp1", // App name
                           "appId": "1234",
                           "appStore":"Apple", // Apple, Google Play, Amazon, Samsung, Roku, Other
                           "optOutUrl": "https://coveredapp1.com/optout" // Empty if company indicated that it does not sell or share personal information.
                       },
                                               {
                           "property": "coveredapp2",
                           "appId": "5678",
                           "appStore":"Google Play", // Apple, Google Play, Amazon, Samsung, Roku, Other
                           "optOutUrl": "https://coveredapp2.com/optout" // Empty if company indicated that it does not sell or share personal information.
                       }
                   ]
           },
           {
            "signatoryType": "First Party Advertiser", // First Party Publisher, First Party Advertiser, Downstream Vendor
                   "registrationTimestamp": "2026-06-01T12:00:00Z",
                   "deletedTimestamp": "2026-06-01T12:00:00Z", // If present, entity is no longer an MSPA signatory after this date/time.
                   "entityType": "Company", // Company or Individual
                   "name" "Company", // Company legal name or name of individual
                   "coverePropertiesWebsites": [
                       {
                           "property": "coveredwebsite1.com",
                           "optOutUrl": "https://coveredwebsite1.com/optout" // Empty if company indicated that it does not sell or share personal information.
                       },
                                               {
                           "property": "coveredwebsite2.com",
                           "optOutUrl": "https://coveredwebsite2.com/optout" // Empty if company indicated that it does not sell or share personal information.
                       }
                   ],
                   "coveredPropertiesApps": [] // Empty if no apps are covered.
                                         
           },
           {
               "signatoryType": "Downstream Vendor", // First Party Publisher, First Party Advertiser, Downstream Vendor
                   "registrationTimestamp": "2026-06-01T12:00:00Z",
                   "deletedTimestamp": "2026-06-01T12:00:00Z", // If present, entity is no longer an MSPA signatory after this date/time.
                   "entityType": "Company", // Company or Individual
                   "name" "Company", // Company legal name or name of individual
                   "domain": "downstreamvendor.com",
                   "optOutUrls":[
                       "downstreamvendor.com/optout1",
                       "downstreamvendor.com/optout2"
                   ]
           }
              
           ]
       }
   }
}
```
