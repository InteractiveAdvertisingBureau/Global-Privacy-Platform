
# Document History
<table>
  <tr>
    <td><strong>Date</strong></td>
    <td><strong>Comments</strong></td>
  </tr>
  <tr>
	  <td>Sept 28, 2022</td>    
    <td>Published final public version</td>
  </tr>
  </table>
  
### Section IDs

Each section represents a unique privacy signal, usually a unique jurisdiction. Below are the supported discrete sections.

  <table>
  <tr>
    <td><strong>Section ID</strong></td>
    <td><strong>Client-side API Prefix</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td><code>1</code></td>
    <td>tcfeuv1</td>
    <td>EU TCF v1 section (deprecated)</td>
  </tr>
  <tr>
    <td><code>2</code></td>
    <td>tcfeuv2</td>
    <td><a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/EEA">EU TCF v2 section</a> (see note below)</td>
  </tr>
  <tr>
    <td><code>3</code></td>
    <td></td>
    <td>GPP Header section (REQUIRED, see note below)</td>
  </tr>
  <tr>
    <td><code>4</code></td>
    <td>--</td>
    <td>GPP signal integrity section</td>
      </tr>
  <tr>
    <td><code>5</code></td>
    <td>tcfca</td>
    <td><a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/Canada">Canadian TCF section</a></td>
  </tr>
  <tr>
    <td><code>6</code></td>
    <td>uspv1</td>
    <td><a href="https://github.com/InteractiveAdvertisingBureau/USPrivacy/blob/master/CCPA/US%20Privacy%20String.md">USPrivacy String </a>(Unencoded Format)</td>
  </tr>
  <tr>
    <td><code>7</code></td>
    <td>usnat</td>
    <td>US - national section (coming soon)</td>
  </tr>
  <tr>
    <td><code>8</code></td>
    <td>usca</td>
    <td>US - California section (coming soon)</td>
     </tr>
  <tr>
    <td><code>9</code></td>
    <td>usva</td>
    <td>US - Virginia section (coming soon)</td>
      </tr>
  <tr>
    <td><code>10</code></td>
    <td>usco</td>
    <td>US - Colorado section (coming soon)</td>
  </tr>
  <tr>
    <td><code>11</code></td>
    <td>usut</td>
    <td>US - Utah section (coming soon)</td>
  </tr>
  <tr>
    <td><code>12</code></td>
    <td>usct</td>
    <td>US - Connecticut section (coming soon)</td>
     </td>
     </td>
  </tr>
</table>

>**Note:** In order to make it simple to distinguish a GPP string from the existing IAB Europe TCF  v2 TC String the first space in the header should be the version. This would allow current implementations to more easily understand and adapt to a GPP string. If the reader of a string finds “C” as the first character this indicates the string is IAB Europe’s TCF v2.0 ("2" in bits corresponds to letter "C" in base64). If the reader of a string finds a “D” as the first character this indicates the string is GPP ("3" in bits corresponds to letter "D" in base64). 


### Reusable Sub-Sections

New privacy framework signals may start as reusable sub-sections in the GPP. Over time as they become more widely adopted, they may become sections with their own ID and referenced in the Header. Reusable sub-sections may be added to any section using the delimiter “.” (dot) to separate the sub-sections from each other. Details on a reusable sub-section, including whether it is available, required, or optional, for a specific section are included in each specific section’s documentation.
 
 
In order to be included as a supported reusable sub-section, the signal must meet the following criteria: 

- Be open designs
- Be widely understood and adopted
- Have a clear interface for machines


Below is a list of supported reusable sub-sections. 

### [Global Privacy Control (GPC)](https://globalprivacycontrol.github.io/gpc-spec/)

GPC is signaled in user agent headers `(Sec-GPC)` and a simple javascript API `(globalPrivacyControl)`. Entities creating GPP strings may check for whether GPC is set and pass along the value they find (from the headers or javascript API) in the GPC sub-section for all sections where it is available. Potential values in the user agent API are boolean (0/1 for header and true/false for javascript API). At the time of publication, true is an opt out of sale under CCPA (“Do not sell my personal information”).

