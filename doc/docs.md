# Protocol Documentation
<a name="top"/>

## Table of Contents

- [media.proto](#media.proto)
    - [Ad](#media.Ad)
    - [Ad.Audio](#media.Ad.Audio)
    - [Ad.Audit](#media.Ad.Audit)
    - [Ad.Display](#media.Ad.Display)
    - [Ad.Video](#media.Ad.Video)
  
  
  
  

- [placement.proto](#placement.proto)
    - [Placement](#placement.Placement)
    - [Placement.AudioPlacement](#placement.Placement.AudioPlacement)
    - [Placement.Companion](#placement.Placement.Companion)
    - [Placement.DisplayPlacement](#placement.Placement.DisplayPlacement)
    - [Placement.VideoPlacement](#placement.Placement.VideoPlacement)
  
  
  
  

- [Scalar Value Types](#scalar-value-types)



<a name="media.proto"/>
<p align="right"><a href="#top">Top</a></p>

## media.proto
The Media group of objects defines an actual ad including reference to its creative and metadata 
to enable proper rendering, restrictions compliance, event tracking, and quality auditing. The 
following figure presents the objects and interrelationships in this group. The objects are 
defined in the subsections thereafter.


<a name="media.Ad"/>

### Ad
This object is the root of a structure that defines in instance of advertising media. It includes
metadata about the ad overall and sub-objects that provide additional detail specific to the type 
of media comprising the creative.


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





 

 

 

 



<a name="placement.proto"/>
<p align="right"><a href="#top">Top</a></p>

## placement.proto
The Placement group includes objects that define the set of allowed ads for a given impression.
This can include mechanical information (e.g., sizes, supported mime types and other rendering 
options), placement details and positioning, various restrictions lists (e.g., advertiser 
domains, content categories), and more.


<a name="placement.Placement"/>

### Placement
This object represents the properties of a placement and the characteristics of ads permitted to
be rendering within them. Placements of all types begin with this object as their root. It 
contains one or more subtype objects (i.e., &#34;display&#34;, &#34;video&#34;, &#34;audio&#34;) that define the kinds of
media permitted as well as media specific placement behaviors.

The other attributes in this object apply to all aspects and substructures of the placement
(i.e., the same block lists, language, secure status, etc. apply to all media types and native 
assets as applicable).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| tagid | [string](#string) |  | Identifier for specific ad placement or ad tag; unique within a distribution channel. |
| ssai | [int32](#int32) |  | Indicates if server-side ad insertion (e.g., stitching an ad into an audio or video stream) is in use and the impact of this on asset and tracker retrieval, where 1 = all client-side, 2 = assets stitched server-side but tracking pixels fired client-side, 3 = all server-side. Default = 0. |
| sdk | [string](#string) |  | Name of ad mediation partner, SDK technology, or player responsible for rendering ad (typically video, audio, or mobile); used by some ad servers to customize ad code by partner. |
| sdkver | [string](#string) |  | Version of the SDK specified in the &#34;sdk&#34; attribute. |
| reward | [int32](#int32) |  | Indicates if this is a rewarded placement, where 0 = no, 1 = yes. Default = 0. |
| bcats | [string](#string) | repeated | Block list of content categories using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| cattax | [int32](#int32) |  | The taxonomy in use for the &#34;bcat&#34; attribute. Default = 2. Refer to List: Category Taxonomies. |
| badvs | [string](#string) | repeated | Block list of advertisers by their domains (e.g., &#34;ford.com&#34;). |
| bapps | [string](#string) | repeated | Block list of apps for which ads are disallowed. These should be bundle or package names (e.g., &#34;com.foo.mygame&#34;) and should NOT be app store IDs (e.g., not iTunes store IDs). |
| battrs | [int32](#int32) | repeated | Block list of creative attributes. Refer to List: Creative Attributes. |
| wlangs | [string](#string) | repeated | Whitelist of permitted languages of the creative using ISO-639-1-alpha-2. In practice, vendors using this object may elect an alternate standard (e.g., BCP-47) in which case this must be communicated a priori. Omission of this attribute indicates there are no restrictions. |
| secure | [int32](#int32) |  | Flag to indicate if the creative is secure (i.e., uses HTTPS for all assets and markup), where 0 = no, 1 = yes. There is no default and thus if omitted, the secure state is unknown. However, as a practical matter, the safe assumption is to treat unknown as non-secure. |
| admx | [int32](#int32) |  | Indicates if including markup is supported (i.e., the various &#34;ad&#34; attributes throughout the &#34;Placement&#34; structure), where 0 = no, 1 = yes. |
| curlx | [int32](#int32) |  | Indicates if retrieving markup via URL reference is supported (i.e., the various &#34;curl&#34; attributes throughout the &#34;placement&#34; structure), where 0 = no, 1 = yes. |
| display | [Placement.DisplayPlacement](#placement.Placement.DisplayPlacement) |  | Placement Subtype Object that indicates that this may be a display placement and provides additional detail related thereto. Refer to Object: DisplayPlacement. * At least one placement subtype is required. |
| video | [Placement.VideoPlacement](#placement.Placement.VideoPlacement) |  | Placement Subtype Object that indicates that this may be a video placement and provides additional detail related thereto. Refer to Object: VideoPlacement. * At least one placement subtype is required. |
| audio | [Placement.AudioPlacement](#placement.Placement.AudioPlacement) |  | Placement Subtype Object that indicates that this may be an audio placement and provides additional detail related thereto. Refer to Object: AudioPlacement. * At least one placement subtype is required. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="placement.Placement.AudioPlacement"/>

### Placement.AudioPlacement
This object signals that the placement may be an audio placement and provides additional 
detail about permitted audio ads (e.g., DAAST).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| delay | [int32](#int32) |  | Indicates the start delay in seconds for pre-roll, mid-roll, or post-roll placements. For additional generic values, refer to List: Start Delay Modes. |
| skip | [bool](#bool) |  | Indicates if the placement imposes ad skippability, where false = no, true = yes. |
| skipmin | [int32](#int32) |  | The placement allows creatives of total duration greater than this number of seconds to be skipped; only applicable if the ad is skippable. Default 0. |
| skipafter | [int32](#int32) |  | Number of seconds a creative must play before the placement enables skipping; only applicable if the ad is skippable. |
| playmethod | [int32](#int32) |  | Playback method in use for this placement. Refer to List: Playback Methods. |
| playend | [int32](#int32) |  | The event that causes playback to end for this placement. Refer to List: Playback Cessation Modes. |
| feed | [int32](#int32) |  | Type of audio feed for this placement. Refer to List: Feed Types. |
| nvol | [int32](#int32) |  | Volume normalization mode of this placement. Refer to List: Volume Normalization Modes. |
| mime | [string](#string) | repeated | Array of supported mime types (e.g., &#34;audio/mp4&#34;). If omitted, all types are assumed. Required. |
| api | [int32](#int32) | repeated | List of supported APIs for this placement. If an API is not explicitly listed, it is assumed to be unsupported. Refer to List: API Frameworks. |
| ctype | [int32](#int32) | repeated | Creative subtypes permitted for this placement. Refer to List: Creative Subtypes - Audio. |
| mindur | [int32](#int32) |  | Minimum creative duration in seconds. |
| maxdur | [int32](#int32) |  | Maximum creative duration in seconds. |
| maxext | [int32](#int32) |  | Maximum extended creative duration if extension is allowed. If 0, extension is not allowed. If -1, extension is allowed and there is no time limit imposed. If greater than 0, then the value represents the number of seconds of extended play supported beyond the &#34;maxdur&#34; value. |
| minbitr | [int32](#int32) |  | Minimum bit rate of the creative in Kbps. |
| maxbitr | [int32](#int32) |  | Maximum bit rate of the creative in Kbps. |
| delivery | [int32](#int32) | repeated | Array of supported creative delivery methods. If omitted, all can be assumed. Refer to List: Delivery Methods. |
| maxseq | [int32](#int32) |  | The maximum number of ads that can be played in a pod. |
| comp | [Placement.Companion](#placement.Placement.Companion) | repeated | Array of objects indicating that companion ads are available and providing the specifications thereof. Refer to Object: Companion. |
| comptype | [int32](#int32) | repeated | Supported companion ad types; recommended if companion ads are specified in &#34;comp&#34;. Refer to List: Companion Types |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="placement.Placement.Companion"/>

### Placement.Companion
This object is used in video and audio placements to specify an associated or so-called
companion display ad. Video and audio placements can specify an array of companion ads.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Identifier of the companion ad; unique within this placement. |
| vcm | [int32](#int32) |  | Indicates the companion ad rendering mode relative to the associated video or audio ad, where 0 = concurrent, 1 = end card. For a given placement, typically only one companion at most should be designated as an end card. |
| display | [Placement.DisplayPlacement](#placement.Placement.DisplayPlacement) |  | Display specification object representing the companion ad. Refer to Object: DisplayPlacement. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="placement.Placement.DisplayPlacement"/>

### Placement.DisplayPlacement
This object signals that the placement may be a display placement. It provides additional
detail about permitted display ads including simple banners, AMPHTML (i.e., Accelerated Mobile
Pages), and native.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| pos | [int32](#int32) |  | Placement position on screen. Refer to List: Placement Positions. |
| instl | [int32](#int32) |  | Inidicates if this is an interstitial placement, where 0 = no, 1 = yes. Default 0. |
| topframe | [int32](#int32) |  | Indicates if the placement will be loaded into an iframe or not, where 0 = unfriendly iframe or unknown, 1 = top frame, friendly iframe, or SafeFrame. A value of &#34;1&#34; can be understood to mean that expandable ads are technically capable of being delivered. |
| ifrbusts | [string](#string) | repeated | Array of iframe busters supported by this placement. The meaning of strings in this attribute must be coordinated a priori among vendors. |
| clktype | [int32](#int32) |  | Indicates the click type of this placement. Refer to List: Click Types. |
| ampren | [int32](#int32) |  | AMPHTML rendering treatment for AMP ads in this placement, where 1 = early loading, 2 = standard loading. |
| ptype | [int32](#int32) |  | Recommended. The display placement type. Refer to List: Display Placement Types. |
| context | [int32](#int32) |  | Recommended. The context of the placement. Refer to List: Display Context Types |
| mimes | [string](#string) | repeated | Array of supported mime types (e.g., &#34;image/jpeg&#34;, &#34;image/gif&#34;). If omitted, all types are assumed. |
| apis | [int32](#int32) | repeated | List of supported APIs. If an API is not explicitly listed, it is assumed to be unsupported. Refer to List: API Frameworks. |
| ctypes | [int32](#int32) | repeated | Creative subtypes permitted. Refer to List: Creative Subtypes - Display. |
| w | [int32](#int32) |  | Width of the placement in units specified by &#34;unit&#34;. Note that this size applies to the placement itself; permitted creative sizes are specified elsewhere (e.g. &#34;DisplayFormat&#34;, &#34;ImageAssetFormat&#34;, etc.). |
| h | [int32](#int32) |  | Width of the placement in units specified by &#34;unit&#34;. Note that this size applies to the placement itself; permitted creative sizes are specified elsewhere (e.g., &#34;DisplayFormat&#34;, &#34;ImageAssetFormat&#34;, etc.). |
| unit | [int32](#int32) |  | Unit of size used for placement size (i.e., &#34;w&#34; and &#34;h&#34; attributes). Default = 1. Refer to List: Size Units. |
| displayfmts | [Placement.DisplayPlacement.DisplayFormat](#placement.Placement.DisplayPlacement.DisplayFormat) | repeated | Array of objects that govern the attributes (e.g., sizes) of a banner display placement. Note that including both &#34;displayfmt&#34; and &#34;nativefmt&#34; is not recommended. Refer to Object: DisplayFormat. |
| nativefmt | [Placement.DisplayPlacement.NativeFormat](#placement.Placement.DisplayPlacement.NativeFormat) |  | This object specified the required and permitted assets and attributes of a native display placement. Note that including both &#34;displayfmt&#34; and &#34;nativefmt&#34; is not recommended. Refer to Object: NativeFormat. |
| event | [Placement.DisplayPlacement.EventSpec](#placement.Placement.DisplayPlacement.EventSpec) | repeated | Array of supported ad tracking events. Refer to Object: EventSpec |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="placement.Placement.VideoPlacement"/>

### Placement.VideoPlacement
This object signals that the placement may be a video placement and provides additional detail
about permitted video ads (e.g., VAST).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ptype | [int32](#int32) |  | Placement subtype. Refer to List: Placement Subtypes - Video. |
| pos | [int32](#int32) |  | Placement position on screen. Refer to List: Placement Positions. |
| delay | [int32](#int32) |  | Indicates the start delay in seconds for pre-roll, mid-roll, or post-roll placements. For additional generic values, refer to List: Start Delay Modes. |
| skip | [bool](#bool) |  | Indicates if the placement imposes ad skippability, where false = no, true = yes. |
| skipmin | [int32](#int32) |  | The placement allows creatives of total duration greater than this number of seconds to be skipped; only applicable if the ad is skippable. Default = 0. |
| skipafter | [int32](#int32) |  | Number of seconds a creative must play before the placement enables skipping; only applicable if the ad is skippable. Default = 0. |
| playmethod | [int32](#int32) |  | Playback method in use for this placement. Refer to List: Playback Methods. |
| playend | [int32](#int32) |  | The event that causes playback to end for this placement. Refer to List: Playback Cessation Modes. |
| clktype | [int32](#int32) |  | Indicates the click type of the placement. Refer to List: Click Types. |
| mime | [string](#string) | repeated | Array of supported mime types (e.g., &#34;video/mp4&#34;). If omitted, all types are assumed. Required. |
| api | [int32](#int32) | repeated | List of supported APIs for this placement. If an API is not explicitly listed, it is assumed to be unsupported. Refer to List: API Frameworks. |
| ctype | [int32](#int32) | repeated | Creative subtypes permitted for this placement. Refer to List: Creative Subtypes - Video. |
| w | [int32](#int32) |  | Width of the creative in units specified by &#34;unit&#34;. |
| h | [int32](#int32) |  | Height of the creative in units spcified by &#34;unit&#34;. |
| unit | [int32](#int32) |  | Units of size used for &#34;w&#34; and &#34;h&#34; attributes. Refer to List: Size Units. Default = 1. |
| mindur | [int32](#int32) |  | Minimum creative duration in seconds. |
| maxdur | [int32](#int32) |  | Maximum creative duration in seconds. |
| maxext | [int32](#int32) |  | Maximum extended creative duration if extension is allowed. If 0, extension is not allowed. If -1, extension is allowed and there is no time limit imposed. If greater than 0, then the value represents the number of seconds of extended play supported beyond the &#34;maxdur&#34; value. Default = 0. |
| minbitr | [int32](#int32) |  | Minimum bit rate of the creative in Kbps. |
| maxbitr | [int32](#int32) |  | Maximum bit rate of the creative in Kbps. |
| delivery | [int32](#int32) | repeated | Array of supported creative delivery methods. If omitted, all can be assumed. Refer to List: Delivery Methods. |
| maxseq | [int32](#int32) |  | The maximum number of ads that can be played in an ad pod. |
| linear | [int32](#int32) |  | Indicates if the creative must be linear, nonlinear, etc. If none specified, no restrictions are assumed. Refer to List: Linearity Modes. |
| boxing | [bool](#bool) |  | Indicates if letterboxing of 4:3 creatives into a 16:9 window is allowed, where false = no, true = yes. Default = true. TODO(@joelpm): bool defaults to false - consider changing spec? |
| comp | [Placement.Companion](#placement.Placement.Companion) | repeated | Array of objects indicating that companion ads are available and providing the specifications thereof. Refer to Object: Companion. |
| comptype | [int32](#int32) | repeated | Supported companion ad types; recommended if companion ads are specified in &#34;comp&#34;. Refer to List: Companion Types. |
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

