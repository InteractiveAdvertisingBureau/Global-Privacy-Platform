
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
	  <tr>
	  <td>June, 2023</td>    
    <td>Fixed Canada api name</td>
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
    <td>tcfcav1</td>
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
    <td><a href="https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform/tree/main/Sections/US-National">MSPA US National Section</a></td>
  </tr>
  <tr>
    <td><code>8</code></td>
    <td>usca</td>
    <td>US - California section </td>
     </tr>
  <tr>
    <td><code>9</code></td>
    <td>usva</td>
    <td>US - Virginia section </td>
      </tr>
  <tr>
    <td><code>10</code></td>
    <td>usco</td>
    <td>US - Colorado section </td>
  </tr>
  <tr>
    <td><code>11</code></td>
    <td>usut</td>
    <td>US - Utah section </td>
  </tr>
  <tr>
    <td><code>12</code></td>
    <td>usct</td>
    <td>US - Connecticut section </td>
     </td>
     </td>
  </tr>
<tr>
    <td><code>13</code></td>
    <td>usfl</td>
    <td>US - Florida section </td>
     </td>
     </td>
<tr>
    <td><code>14</code></td>
    <td>usmt</td>
    <td>US - Montana section </td>
     </td>
     </td>
  </tr>
 <tr>
    <td><code>15</code></td>
    <td>usor</td>
    <td>US - Oregon section </td>
     </td>
     </td>
  </tr>
 <tr>
    <td><code>16</code></td>
    <td>ustx</td>
    <td>US - Texas section </td>
     </td>
     </td>
  </tr>
<tr>
    <td><code>17</code></td>
    <td>usde</td>
    <td>US - Delaware section </td>
     </td>
     </td>
  </tr>
 <tr>
    <td><code>18</code></td>
    <td>usia</td>
    <td>US - Iowa section </td>
     </td>
     </td>
  </tr>
 <tr>
    <td><code>19</code></td>
    <td>usne</td>
    <td>US - Nebraska section </td>
     </td>
     </td>
  </tr>
 <tr>
    <td><code>20</code></td>
    <td>usnh</td>
    <td>US - New Hampshire section </td>
     </td>
     </td>
  </tr>
 <tr>
    <td><code>21</code></td>
    <td>usnj</td>
    <td>US - New Jersey section </td>
     </td>
     </td>
  </tr>
 <tr>
    <td><code>22</code></td>
    <td>ustn</td>
    <td>US - Tennessee section </td>
     </td>
     </td>
  </tr>
  <tr>
    <td><code>23</code></mn>
    <td>usmn</td>
    <td>US - Minnesota section </mn>
     </td>
  </tr>
  <tr>
    <td><code>24</code></mn>
    <td>usmd</td>
    <td>US - Maryland section </mn>
     </td>
     </td>
  </tr>
  <tr>
    <td><code>25</code></mn>
    <td>usin</td>
    <td>US - Indiana section </mn>
     </td>
     </td>
  </tr>
  <tr>
    <td><code>26</code></mn>
    <td>usky</td>
    <td>US - Kentucky section </mn>
     </td>
     </td>
  </tr>
  <tr>
    <td><code>27</code></mn>
    <td>usri</td>
    <td>US - Rhode Island section </mn>
     </td>
     </td>
  </tr>
</table>

>**Note:** In order to make it simple to distinguish a GPP string from the existing IAB Europe TCF  v2 TC String the first space in the header should be the version. This would allow current implementations to more easily understand and adapt to a GPP string. If the reader of a string finds “C” as the first character this indicates the string is IAB Europe’s TCF v2.0 ("2" in bits corresponds to letter "C" in base64). If the reader of a string finds a “D” as the first character this indicates the string is GPP ("3" in bits corresponds to letter "D" in base64). 


### Reusable Subsections

New privacy framework signals may start as reusable subsections in the GPP. Over time as they become more widely adopted, they may become sections with their own ID and reference in the Header. Reusable subsections may be added to any section using the delimiter “.” (dot) to separate the subsections from each other. Details on a reusable subsection, including whether it is available, required, or optional, for a specific section are included in each specific section’s documentation.
 
 
In order to be included as a supported reusable subsection, the signal must meet the following criteria: 

- Be openly designed
- Be widely understood and adopted
- Have a clear interface for machines


Below is a list of supported reusable subsections. 

### [Global Privacy Control (GPC)](https://w3c.github.io/gpc/)

GPC is signaled in user agent headers `(Sec-GPC)` and a simple javascript API `(globalPrivacyControl)`. Entities creating GPP strings may check for whether GPC is set and pass along the value they find (from the headers or javascript API) in the GPC subsection for all sections where it is available. Potential values in the user agent API are boolean (0/1 for header and true/false for javascript API). At the time of publication, true is an opt out of sale under CCPA (“Do not sell my personal information”).

