# Protocol Documentation
<a name="top"/>

## Table of Contents

- [media.proto](#media.proto)
    - [Ad](#media.Ad)
    - [Ad.Audio](#media.Ad.Audio)
    - [Ad.Audit](#media.Ad.Audit)
    - [Ad.Display](#media.Ad.Display)
    - [Ad.Video](#media.Ad.Video)
  
  
  
  

- [Scalar Value Types](#scalar-value-types)



<a name="media.proto"/>
<p align="right"><a href="#top">Top</a></p>

## media.proto
The Media group of objects defines an actual ad including reference to its creative and metadata to enable proper
rendering, restrictions compliance, event tracking, and quality auditing. The following figure presents the objects
and interrelationships in this group. The objects are defined in the subsections thereafter.


<a name="media.Ad"/>

### Ad
This object is the root of a structure that defines in instance of advertising media. It includes metadata about
the ad overall and sub-objects that provide additional detail specific to the type of media comprising the creative.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Required. ID of the creative; unique at least throughout the scope of a vendor (e.g., an exchange or buying platform). Note that multiple instances of the same ad when used in transactions must have the same ID. |
| adomain | [string](#string) | repeated | Recommended. Advertiser domain; top two levels only (e.g., &#34;ford.com&#34;). This can be an array for the case of rotating creatives. |
| bundle | [string](#string) | repeated | When the product of the ad is an app, the unique ID of that app as a bundle or package name (e.g., &#34;com.foo.mygame&#34;). This should NOT be an app store ID (e.g., no iTunes store IDs). This can be an array of for the case of rotating creatives. |
| iurl | [string](#string) |  | URL without cache-busting to an image that is representative of the ad content for cursory level ad quality checking. |
| cat | [string](#string) | repeated | Array of content categories describing the ad using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| cattax | [int32](#int32) |  | The taxonomy in use for the &#34;cat&#34; attribute. Refer to List: Category Taxonomies. The default value is 2. |
| lang | [string](#string) |  | Language of the creative using ISO-639-1-alpha-2. In practice, vendors using this object may elect an alternate standard (e.g., BCP-47) in which case this must be communicated a priori. The non-standard code &#34;xx&#34; may also be used if the creative has no linguistic content (e.g., a banner with just a company logo). |
| attr | [int32](#int32) | repeated | Set of attributes describing the creative. Refer to List: Creative Attributes. |
| secure | [int32](#int32) |  | Flag to indicate if the creative is secure (i.e., uses HTTPS for all assets and markup), where 0 = no, 1 = yes. There is no default and thus if omitted, the secure state is unknown. However, as a practical matter, the safe assumption is to treat unknown as non-secure. |
| mrating | [int32](#int32) |  | Media rating per IQG guidelines. Refer to List: Media Ratings. |
| init | [string](#string) |  | Date/time of the original instantiation of this ad (i.e., this object or any of its children) in the format of ISO-8601; W3C profile. Refer to www.w3.org/TR/NOTE-datetime. |
| lastmod | [string](#string) |  | Date/time of most recent modification to this ad (i.e., this object or any of its children) in the format of ISO-8601; W3C profile. Refer to www.w3.org/TR/NOTE-datetime. |
| display | [Ad.Display](#media.Ad.Display) |  | If set, indicates this is a display ad and provides additional detail as such. Refer to Object: Display. |
| video | [Ad.Video](#media.Ad.Video) |  | If set, indicates this is a video ad and provides additional detail as such. Refer to Object: Video. |
| audio | [Ad.Audio](#media.Ad.Audio) |  | If set, indicates this is an audio ad and provides additional detail as such. Refer to Object: Audio. |
| audit | [Ad.Audit](#media.Ad.Audit) |  | An object depicting the audit status of the ad; typically part of a quality/safety review process. Refer to Object: Audit. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="media.Ad.Audio"/>

### Ad.Audio
This object provides additional detail about an ad specifically for audio ads.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| mimes | [string](#string) | repeated | Mime type(s) of the ad creative(s) (e.g., &#34;audio/mp4&#34;). |
| apis | [int32](#int32) | repeated | API required by the ad if applicable. Refer to List: API Frameworks |
| types | [int32](#int32) | repeated | Subtype of video creative. Refer to List: Creative Subtypes - Audio. |
| adm | [string](#string) |  | Video markup (e.g., DAAST document) for the asset. |
| curl | [string](#string) |  | A URL that returns the video markup (e.g., DAAST document) for the asset. If this ad is matched to a placement specification, the &#34;Placement.ref&#34; attribute indicates if this markup retrieval option is supported. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="media.Ad.Audit"/>

### Ad.Audit
This objects represents the outcome of some form of review of the ad. This is typical, for 
example, when scanning for malware or otherwise performing ad quality reviews.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| status | [int32](#int32) |  | The audit status of the ad. Refer to List: Audit Status Codes. |
| feedback | [string](#string) | repeated | One or more human-readable explanations as to reasons for rejection or any changes to fields for ad quality reasons (e.g., &#34;adomain&#34;, &#34;cat&#34;, &#34;attr&#34;, etc.) |
| init | [string](#string) |  | Date/time of the original instantiation of this object in the format of ISO-8601; W3C profile. Refer to www.w3.org/TR/NOTE-datetime. |
| lastmod | [string](#string) |  | Date/time of the original instantiation of this object in the format of ISO-8601; W3C profile. Refer to www.w3.org/TR/NOTE-datetime. |
| corr | [google.protobuf.Any](#google.protobuf.Any) |  | Correction object wherein the auditor can specify changes to attributes of the &#34;Ad&#34; object or its children they believe to be proper. For example, if the original &#34;Ad&#34; indicated a category of &#34;IAB3&#34;, but the auditor deems the correct category to be &#34;IAB13&#34;, then &#34;corr&#34; could include a sparse &#34;Ad&#34; object including just the &#34;cat&#34; array indicating &#34;IAB13&#34;. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="media.Ad.Display"/>

### Ad.Display
This object provides additional detail about an ad specifically for display ads. There are 
multiple attributes for specifying creative details: &#34;banner&#34; for simple banner images &#34;native&#34;
for native ads, &#34;ad&#34; for including general markup, and &#34;curl&#34; for referencing general markup via
URL. In any given &#34;Display&#34; object, only one of these attributes should be used to avoid
confusion. To the extent feasible, structured objects should be favored over general markup for
quality and safety issues.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| mime | [string](#string) |  | Mime type of the ad (e.g., &#34;image/jpeg&#34;). |
| api | [int32](#int32) | repeated | API required by the ad if applicable. Refer to List: API Frameworks. |
| type | [int32](#int32) | repeated | Subtype of display creative. Refer to List: Creative Subtypes - Display. |
| w | [int32](#int32) |  | Absolute width of the creative in device independent pixels (DIPS), typically for non-native ads. Note that mixing absolute and relative sizes is not recommended. |
| h | [int32](#int32) |  | Absolute height of the creative in device independent pixels (DIPS), typically for non-native ads. Note that mixing absolute and relative sizes is not recommended. |
| wratio | [int32](#int32) |  | Relative width of the creative when expressing size as a ratio, typically for non-native ads. Note that mixing absolute and relative sizes is not recommended. |
| hratio | [int32](#int32) |  | Relative height of the creative when expressing size as a ratio, typically for non-native ads. Note that mixing absolute and relative sizes is not recommended. |
| adm | [string](#string) |  | General display markup (e.g., HTML, AMPHTML) if not using a structured alternative (e.g., &#34;banner&#34;, &#34;native&#34;). |
| curl | [string](#string) |  | Optional means of retrieving display markup by reference; a URL that can return HTML, AMPHTML, or a collection native &#34;Asset&#34; object and their subordinates). If this ad is matched to a Placement specification, the &#34;Placement.ref&#34; attribute indicates if this markup retrieval option is supported. |
| banner | [Ad.Display.Banner](#media.Ad.Display.Banner) |  | Structured banner image object, recommended for simple banner creatives. Refer to Object: Banner. |
| native | [Ad.Display.Native](#media.Ad.Display.Native) |  | Structured native object, recommended for native ads. Refer to Object: Native. |
| event | [Ad.Display.Event](#media.Ad.Display.Event) | repeated | Array of events that the advertiser or buying platform wants to track. Refer to Object: Event. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="media.Ad.Video"/>

### Ad.Video
This object provides additional detail about an ad specifically for video ads.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| mimes | [string](#string) | repeated | Mime type(s) of the ad creative(s) (e.g., &#34;video/mp4&#34;). |
| apis | [int32](#int32) | repeated | API required by the ad if applicable. Refer to List: API Frameworks |
| types | [int32](#int32) | repeated | Subtype of video creative. Refer to List: Creative Subtypes - Video. |
| adm | [string](#string) |  | Video markup (e.g., VAST document) for the asset. |
| curl | [string](#string) |  | A URL that returns the video markup (e.g., VAST document) for the asset. If this ad is matched to a placement specification, the &#34;Placement.ref&#34; attribute indicates if this markup retrieval option is supported. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |





 

 

 

 



## Scalar Value Types

| .proto Type | Notes | C++ Type | Java Type | Python Type |
| ----------- | ----- | -------- | --------- | ----------- |
| <a name="double" /> double |  | double | double | float |
| <a name="float" /> float |  | float | float | float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long |
| <a name="bool" /> bool |  | bool | boolean | boolean |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str |
