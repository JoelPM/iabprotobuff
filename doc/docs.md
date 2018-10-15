# Protocol Documentation
<a name="top"/>

## Table of Contents

- [context.proto](#context.proto)
    - [Content](#adcom.context.Content)
    - [Data](#adcom.context.Data)
    - [Device](#adcom.context.Device)
    - [DistributionChannel](#adcom.context.DistributionChannel)
    - [DistributionChannel.App](#adcom.context.DistributionChannel.App)
    - [DistributionChannel.DOOH](#adcom.context.DistributionChannel.DOOH)
    - [DistributionChannel.Site](#adcom.context.DistributionChannel.Site)
    - [Geo](#adcom.context.Geo)
    - [Producer](#adcom.context.Producer)
    - [Publisher](#adcom.context.Publisher)
    - [Regs](#adcom.context.Regs)
    - [Segment](#adcom.context.Segment)
    - [User](#adcom.context.User)
  
  
  
  

- [enum.proto](#enum.proto)
    - [Creative](#adcom.Creative)
  
    - [APIFramework](#adcom.APIFramework)
    - [AudioFeedType](#adcom.AudioFeedType)
    - [AuditStatusCode](#adcom.AuditStatusCode)
    - [CategoryTaxonomy](#adcom.CategoryTaxonomy)
    - [ClickType](#adcom.ClickType)
    - [CompanionType](#adcom.CompanionType)
    - [ConnectionType](#adcom.ConnectionType)
    - [ContentContext](#adcom.ContentContext)
    - [Creative.Attribute](#adcom.Creative.Attribute)
    - [Creative.AudioType](#adcom.Creative.AudioType)
    - [Creative.DisplayType](#adcom.Creative.DisplayType)
    - [Creative.VideoType](#adcom.Creative.VideoType)
    - [DOOHVenueType](#adcom.DOOHVenueType)
    - [DeliveryMethod](#adcom.DeliveryMethod)
    - [DeviceType](#adcom.DeviceType)
    - [DisplayContextType](#adcom.DisplayContextType)
    - [DisplayPlacementType](#adcom.DisplayPlacementType)
    - [EventTrackingMethod](#adcom.EventTrackingMethod)
    - [EventType](#adcom.EventType)
    - [ExpandableDirection](#adcom.ExpandableDirection)
    - [LinearityMode](#adcom.LinearityMode)
    - [LocationService](#adcom.LocationService)
    - [LocationType](#adcom.LocationType)
    - [MediaRating](#adcom.MediaRating)
    - [NativeDataAssetType](#adcom.NativeDataAssetType)
    - [NativeImageAssetType](#adcom.NativeImageAssetType)
    - [OperatingSystem](#adcom.OperatingSystem)
    - [PlacementPosition](#adcom.PlacementPosition)
    - [PlaybackCessationMode](#adcom.PlaybackCessationMode)
    - [PlaybackMethod](#adcom.PlaybackMethod)
    - [ProductionQuality](#adcom.ProductionQuality)
    - [SizeUnit](#adcom.SizeUnit)
    - [VideoPlacementSubtype](#adcom.VideoPlacementSubtype)
    - [VolumeNormalizationMode](#adcom.VolumeNormalizationMode)
  
  
  

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



<a name="context.proto"/>
<p align="right"><a href="#top">Top</a></p>

## context.proto
This group of objects represent concepts that are interacting, presenting, enclosing, or are 
otherwise relating to the world in which impressions live. These include the user, their device,
their location, the channel (e.g., site, app, digital out-of-home) with which they are 
interacting, the channel&#39;s publisher, its content, and any regulations that are in effect
(e.g., COPPA, GDPR).


<a name="adcom.context.Content"/>

### Content
This object describes the content in which an impression can appear, which may be syndicated or 
non-syndicated content. This object may be useful when syndicated content contains impressions 
and does not necessarily match the publisher&#39;s general content. An exchange may or may not have 
knowledge of the page where the content is running as a result of the syndication method (e.g., 
a video impression embedded in an iframe on an unknown web property or device).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | ID uniquely identifiying the content. |
| episode | [int32](#int32) |  | Episode number. |
| title | [string](#string) |  | Content title. Video examples: &#34;Search Committee&#34; (television), &#34;Star Wars, A New Hope&#34; (movie), or &#34;Endgame&#34; (made for web). Non-video Example: &#34;Why an Antarctic Glacier Is Melting So Quickly&#34; (Time magazine article). |
| series | [string](#string) |  | Content series. Video examples: &#34;The Office&#34; (television), &#34;Star Wars&#34; (movie), or &#34;Arby &#39;N&#39; The Chief&#34; (made for web). non-video example: &#34;Ecocentric&#34; (Time Magazine blog). |
| season | [string](#string) |  | Content season (e.g., &#34;Season 3&#34;). |
| artist | [string](#string) |  | Artist credited with the content. |
| genre | [string](#string) |  | Genre that best describes the content (e.g., rock, pop, etc). |
| album | [string](#string) |  | Album to which the content belongs; typically for audio. |
| isrc | [string](#string) |  | International Standard Recording Code conforming to ISO-3901. |
| url | [string](#string) |  | URL of the content, for buy-sdie contextualization or review. |
| cat | [string](#string) | repeated | Array of content categories describing the content using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| cattax | [int32](#int32) |  | The taxonomy in use for the &#34;cat&#34; attribute. Refer to List: Category Taxonomies. |
| prodq | [int32](#int32) |  | Produciton quality. Refer to List: Production Qualities. |
| context | [int32](#int32) |  | Type of content (game, video, text, etc.). Refer to List: Content Contexts |
| rating | [string](#string) |  | Content rating (e.g., MPAA). |
| mrating | [int32](#int32) |  | Media rating per IQG guidelines. Refer to List: Media Ratings. |
| keywords | [string](#string) | repeated | Array of kewyords describing the content. TOOD(@joelpm): deviates but makes more sense to me. |
| live | [bool](#bool) |  | Indication of live content, where false = not live, true = live (e.g. stream, live blog). |
| srcrel | [int32](#int32) |  | Source relationship, where 0 = indirect, 1 = direct. TODO(@joelpm): rename drctsrcrel and make boolean? |
| len | [int32](#int32) |  | Length of content in seconds; typically for video or audio. |
| lang | [string](#string) |  | Content language using ISO-639-1-alpha-2. |
| embed | [bool](#bool) |  | Indicator of whether or not the content is embedded off-site from the site or app described in those objects (e.g., an embedded video player), where false = no, true = yes. |
| producer | [Producer](#adcom.context.Producer) |  | Details about the content producer. Refer to Object: Producer. |
| data | [Data](#adcom.context.Data) | repeated | Additional user data. Each &#34;Data&#34; object represents a different data source. Refer to Object: Data. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.Data"/>

### Data
The data and segment objects together allow additional data about the related object (e.g., 
user, content) to be specified. This data may be from multiple sources whether from the exchange
itself or third parties as specified by the &#34;id&#34; attribute. When in use, vendor-specific IDs 
should be communicated a priori among the parties.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Vendor-specific ID for the data provider. |
| name | [string](#string) |  | Vendor-specific displayable name for the data provider. |
| segment | [Segment](#adcom.context.Segment) | repeated | Array of &#34;Segment&#34; objects that contain the actual data values. Refer to Object: Segment. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.Device"/>

### Device
This object provides information pertaining to the device through which the user is interacting.
Device information includes its hardware, platform, location, and carrier data. The device can 
refer to a mobile handset, a desktop computer, set top box, or other digital device.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| type | [int32](#int32) |  | The general type of device. Refer to List: Device Types. |
| ua | [string](#string) |  | Browser user agent string. |
| ifa | [string](#string) |  | ID sanctioned for advertiser use in the clear (i.e., not hashed). |
| dnt | [bool](#bool) |  | Standard &#34;Do Not Track&#34; flag as set in the header by the browser, where false = tracking is unrestricted, true = do not track. |
| lmt | [bool](#bool) |  | &#34;Limit Ad Tracking&#34; signal commercially endorsed (e.g., iOS, Android), where false = tracking is unrestricted, true = tracking must be limited per commercial guidelines. |
| make | [string](#string) |  | Device make (e.g., &#34;Apple&#34;). |
| model | [string](#string) |  | Device model (e.g., &#34;iPhone&#34;). |
| os | [int32](#int32) |  | Device operating system. Refer to List: Operating Systems. |
| hwv | [string](#string) |  | Hardware version of the device (e.g. &#34;5S&#34; for iPhone 5S). |
| h | [int32](#int32) |  | Physical height of the screen in pixels. |
| w | [int32](#int32) |  | Physical width of the screen in pixels. |
| ppi | [int32](#int32) |  | Screen size as pixels per linear inch. |
| pxratio | [float](#float) |  | The ratio of pixels to device independent pixels. |
| js | [bool](#bool) |  | Support for Javascript, where false = no, true = yes. |
| lang | [string](#string) |  | Browser language using ISO-639-1-alpha-2. |
| ip | [string](#string) |  | IPv4 address closest to device. |
| ipv6 | [string](#string) |  | IPv6 address closest to device. |
| xff | [string](#string) |  | The value of the x-frowarded-for header. |
| iptr | [bool](#bool) |  | Indicator of truncation of any of the IP attributes (i.e., &#34;ip&#34;, &#34;ipv6&#34;, &#34;xff&#34;, where true = yes, false = no (e.g., from 1.2.3.4 to 1.2.3.0). Refer to tools.ietf.org/html/rfc6235#section-4.1.1 for more information on IP truncation. |
| carrier | [string](#string) |  | Carrier or ISP (e.g., &#34;VERIZON&#34;) using exchange curated string names which should be published to bidders a priori. |
| mccmnc | [string](#string) |  | Mobile carrier as the concatenated MCC-MNC code (e.g., &#34;310-005&#34; identifies Verizon Wireless CDMA in the USA). Refer to en.wikipedia.org/wiki/Mobile_country_code for further information and references. Note that the dash between the MCC and MNC parts is required to remove parsing ambiguity. |
| mccmncsim | [string](#string) |  | MCC and MNC of the SIM card using the same format as &#34;mccmnc&#34;. When both values are available, a difference between them reveals that a user is roaming. |
| contype | [int32](#int32) |  | Network connection type. Refer to List: Connection Types. |
| feofetch | [bool](#bool) |  | Indicates if the geolocation API will be available to Javascript code running in display ad, where false = no, true = yes. |
| geo | [Geo](#adcom.context.Geo) |  | Location of the device (i.e., typically the user&#39;s current location). Refer to Object: Geo. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.DistributionChannel"/>

### DistributionChannel
A distribution channel is an abstraction of the various types of entities or channels through 
which ads are distributed. Examples include websites, mobile apps, and digital out-of-home (DOOH)
systems. This generalized class contains those attributes and relationships that are common to 
all distribution channels and as such, all of its attributes and relationships are inherited by 
each of its derived classes.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Vendor specific unique identifier of the distribution channel. Recommended. |
| name | [string](#string) |  | Displayable name of the distribution channel. |
| pub | [Publisher](#adcom.context.Publisher) |  | Details about the publisher of the distribution channel. Refer to Object: Publisher. |
| content | [Content](#adcom.context.Content) |  | Details about the content within the distribution channel. Refer to Object: Content. |
| site | [DistributionChannel.Site](#adcom.context.DistributionChannel.Site) |  |  |
| app | [DistributionChannel.App](#adcom.context.DistributionChannel.App) |  |  |
| dooh | [DistributionChannel.DOOH](#adcom.context.DistributionChannel.DOOH) |  |  |






<a name="adcom.context.DistributionChannel.App"/>

### DistributionChannel.App
This object is used to define an ad supported non-browser application, in contrast to a typical
website.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| domain | [string](#string) |  | Domain of the app (e.g., &#34;mygame.foo.com&#34;) |
| cat | [string](#string) | repeated | Array of content categories describing the app using IDs from the taxomony indicated in &#34;cattax&#34;. |
| sectcat | [string](#string) | repeated | Array of content categories describing the current section of the app using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| pagecat | [string](#string) | repeated | Array of content categories describing the current page or view of the app using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| cattax | [int32](#int32) |  | The taxonomy in use for the &#34;cat&#34;, &#34;sectcat&#34;, &#34;pagecat&#34; attributes. Refer to List: Category Taxonomies. |
| privpolicy | [bool](#bool) |  | Indicates if the site has a privacy policy, where false = no, true = yes. |
| keywords | [string](#string) | repeated | Array of keywords about the app. TODO(@joelpm): deviates from standard, check if this makes sense |
| bundle | [string](#string) |  | Bundle or package name of the app (e.g., &#34;com.foo.mygame&#34;) and should NOT be app store IDs (e.g., Apple iTunes, Google Play) |
| storeid | [string](#string) |  | The ID of the app in an app store (e.g., Apple iTunes, Google Play). |
| storeurl | [string](#string) |  | App store URL for an installed app; for IQG 2.1 compliance. |
| ver | [string](#string) |  | Application version. |
| paid | [bool](#bool) |  | Indicator of whether or not this is a paid app, where false = free, true = paid. Default = false |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.DistributionChannel.DOOH"/>

### DistributionChannel.DOOH
This object is used to define an ad supported digital out-of-home (DOOH) experience such as a 
public kiosk or digital billboard.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| venue | [int32](#int32) |  | The type of out-of-home venue. Refer to List: DOOH Venue Types. |
| fixed | [int32](#int32) |  | Indicates whether the DOOH placement is in a fixed location (e.g., kiosk, billboard, elevator) or is movable (e.g., taxi), where 1 = fixed, 2 = movable. |
| etime | [int32](#int32) |  | The exposure time in seconds per view that the creative will be displayed before refreshing to the next creative. |
| dpi | [int32](#int32) |  | Minimum DPI for text-based creative elements to display clearly. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.DistributionChannel.Site"/>

### DistributionChannel.Site
This object is used to define an ad supported website, in contrast to a non-browser 
application, for example.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| domain | [string](#string) |  | Domain of the site (e.g., &#34;mysite.foo.com&#34;). |
| cat | [string](#string) | repeated | Array of content categories describing the site using IDs from the taxomony indicated in &#34;cattax&#34;. |
| sectcat | [string](#string) | repeated | Array of content categories describing the current section of the site using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| pagecat | [string](#string) | repeated | Array of content categories describing the current page or view of the site using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| cattax | [int32](#int32) |  | The taxonomy in use for the &#34;cat&#34;, &#34;sectcat&#34;, &#34;pagecat&#34; attributes. Refer to List: Category Taxonomies. |
| privpolicy | [bool](#bool) |  | Indicates if the site has a privacy policy, where false = no, true = yes. |
| keywords | [string](#string) | repeated | Array of keywords about the site. TODO(@joelpm): deviates from standard, check if this makes sense |
| page | [string](#string) |  | URL of the page within the site. |
| ref | [string](#string) |  | Referrer URL that casued navigation to the current page. |
| search | [string](#string) |  | Search string that caused navigation to the current page. |
| mobile | [bool](#bool) |  | Indicates if the site has been programmed to optimize layout when viewed on mobile devices, where false = no, true = yes. |
| amp | [bool](#bool) |  | Indicates if the page is built with AMP HTML, where false = no, true = yes. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.Geo"/>

### Geo
This object encapsulates various methods for specifying a geographic location. When subordinate 
to a &#34;Device&#34; object, it indicates the location of the device which can also be interpreted as 
the user&#39;s current location. When subordinate to a &#34;User&#34; object, it indicates the location of 
the user&#39;s home base (i.e., not necessarily their current location).

The &#34;lat&#34; and &#34;lon&#34; attributes should only be passed if they conform to the accuracy depicted in
the &#34;type&#34; attribute. For example, the centroid of a large region (e.g., postal code) should not
be passed.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| type | [int32](#int32) |  | Source of location data; recommended when passing lat/lon. Refer to List: Location Types. |
| lat | [float](#float) |  | Latitude from -90.0 to &#43;90.0, where negative is south. |
| lon | [float](#float) |  | Longitude from -180.0 to &#43;180.0, where negative is west. |
| accur | [int32](#int32) |  | Estimated location accuracy in meters; recommended when lat/lon are specified and derived from a device&#39;s location services (i.e., type = 1). Note that this is the accuracy as reported from the device. Consult OS specific documentation (e.g., Android, iOS) for exact interpretation. |
| lastfix | [int32](#int32) |  | Number of seconds since this geolocation fix was established. Note that devices may cache location data across multiple fetches. Ideally, this value should be from the time the actual fix was taken. |
| ipserv | [int32](#int32) |  | Service or provider used to determine geolocation from IP address if applicable (i.e., &#34;type&#34; = 2). Refer to List: IP Location Services. |
| country | [string](#string) |  | Country code using ISO-3166-1-alpha-2. Note that alpha-3 codes may be encountered and vendors are encouraged to be tolerant of them. |
| region | [string](#string) |  | Region code using ISO-3166-2; 2-letter state code if USA |
| metro | [string](#string) |  | Regional marketing areas such as Nielsen&#39;s DMA codes or other similar taxonomy to be agreed among vendors prior to use. Note that DMA is a trademarked asset of The Nielsen Company. Vendors are encouraged to ensure their use of DMAs is properly licensed. |
| city | [string](#string) |  | City using United Nations Code for Trade &amp; Transport Locations &#34;UN/LOCODE&#34; with the space between country and city suppressed (e.g., Boston MA, USA = &#34;USBOS&#34;). Refer to UN/LOCODE Code List. |
| zip | [string](#string) |  | ZIP or postal code. |
| utcoffset | [int32](#int32) |  | Local time as the number of &#43;/- of minutes from UTC. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.Producer"/>

### Producer
This object defines the producer of the content in which ad will be displayed. This is 
particularly useful when the content is syndicated and may be distributed through different 
publishers and thus when the producer and publisher are not necessarily the same entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Vendor-specific unique producer identifer. Useful if content is syndicated and may be posted a site using using embed tags. Recommended. |
| name | [string](#string) |  | Displayable name of the producer. |
| domain | [string](#string) |  | Highest level domain of the producer (e.g., &#34;producer.com&#34;). |
| cat | [string](#string) | repeated | Array of content categories that describe the producer using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| cattax | [int32](#int32) |  | The taxonomy in use for the &#34;cat&#34; attributed. Refer to List: Category Taxonomies. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.Publisher"/>

### Publisher
This object describes the publisher of the media in which ads will be displayed.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Vendor-specific unique publisher identifier, as used in ads.txt files. Recommended. |
| name | [string](#string) |  | Displayable name of the publisher. |
| domain | [string](#string) |  | Highest level domain of the publisher (e.g., &#34;publisher.com&#34;). |
| cat | [string](#string) | repeated | Array of content categories that describe the publisher using IDs from the taxonomy indicated in &#34;cattax&#34;. |
| cattax | [int32](#int32) |  | The taxonomy in use for the &#34;cat&#34; attribute. Refer to List: Category Taxonomies. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.Regs"/>

### Regs
This object contains any known legal, governmental, or industry regulations that are in effect.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| coppa | [bool](#bool) |  | Flag indicating if COPPA regulations apply, where false = no, true = yes. The Children&#39;s Online Privacy Protection Act (COPPA) was established by the U.S. Federal Trade Commission. |
| gdpr | [bool](#bool) |  | Flag indicating if GDPR regulations apply, where false = no, true = yes. The General Data Protection Regulation (GDPR) is a regulation of the European Union. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.Segment"/>

### Segment
Segment objects are essentially key-value pairs that convey specific units of data. The parent 
&#34;Data&#34; object is a collection of such values from a given data provider. When in use, vendor-
specific IDs should be communicated a priori among the parties.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | ID of the data segment specific to the data provider. |
| name | [string](#string) |  | Displayable name of the data segment specific to the data provider. |
| value | [string](#string) |  | String representation of the data segment value. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |






<a name="adcom.context.User"/>

### User
This object contains information known or derived about the human user of the device (i.e., the 
audience for advertising). The user ID is a vendor-specific artifact and may be subject to 
rotation or other privacy policies. However, this user ID must be stable long enough to serve 
reasonably as the basis for frequency capping and retargeting.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Vendor-specific ID for th euser. At least one of &#34;id&#34; or &#34;buyeruid&#34; is strongly recommended. |
| buyeruid | [string](#string) |  | Buyer-specific ID for the user as mapped by an exchange for the buyer. At least one of &#34;id&#34; or &#34;buyeruid&#34; is strongly recommended. |
| yob | [int32](#int32) |  | Year of birth as a 4-digit integer. |
| gender | [string](#string) |  | Gender, where &#34;M&#34; = male, &#34;F&#34; = female, &#34;O&#34; = known to be other (i.e., omitted is unknown). |
| keywords | [string](#string) | repeated | Array of keywords, interests, or intent. TODO(@joelpm): deviates. |
| consent | [string](#string) |  | GDPR content string if applicable, complying with the IAB standard Consent String Format in the Transparency and Consent Framework technical specifications. |
| geo | [Geo](#adcom.context.Geo) |  | Location of the user&#39;s home base (i.e., not necessarily their current location). Refer to Object: Geo. |
| data | [Data](#adcom.context.Data) | repeated | Additional user data. Each &#34;Data&#34; object represents a different data source. Refer to Object: Data. |
| ext | [google.protobuf.Any](#google.protobuf.Any) |  | Optional vendor-specific extensions. |





 

 

 

 



<a name="enum.proto"/>
<p align="right"><a href="#top">Top</a></p>

## enum.proto
The following enumerations are referenced by attributes in AdCOM objects.


<a name="adcom.Creative"/>

### Creative






 


<a name="adcom.APIFramework"/>

### APIFramework
The following enum is a list of API frameworks either supported by a placement or required
by an ad.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_APIF | 0 | Equivalent to an unset value. |
| VPAID_1_0 | 1 | VPAID 1.0 |
| VAPID_2_0 | 2 | VPAID 2.0 |
| MRAID_1_0 | 3 | MRAID 1.0 |
| ORMMA | 4 | ORMMA |
| MRAID_2_0 | 5 | MRAID 2.0 |
| MRAID_3_0 | 6 | MRAID 3.0 |
| OMID_1_0 | 7 | OMID 1.0 |



<a name="adcom.AudioFeedType"/>

### AudioFeedType
The following enum defines the types of feeds for audio.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_AUDIO_FT | 0 | Equivalent to an unset value. |
| MUSIC_SERVICE | 1 | Music Service. |
| FM_AM_BROADCAST | 2 | FM/AM Broadcast. |
| PODCAST | 3 | Podcast. |



<a name="adcom.AuditStatusCode"/>

### AuditStatusCode
The following enum lists the codes used in &#34;Audit&#34; objects to reflect status or workflow state.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_ASC | 0 | Equivalent to an unset value. |
| PENDING_AUDIT | 1 | Pending Audit: An audit has not yet been completed on this ad. A recommendation cannot be made to use this ad, but vendors&#39; policies may override. |
| PREAPPROVED | 2 | Pre-Approved: An audit has not yet been completed on this ad. Subject to vendors&#39; policies, it can be recommended for use. However, once the audit has been completed, its status will change and it may or may not be approved for continued use. |
| APPROVED | 3 | Approved: The audit is complete and the ad is approved for use. Note, however, that some attributes (e.g., &#34;adomain&#34;, &#34;cat&#34;, &#34;attr&#34;, etc.) may have been changed in the process by the auditor. |
| DENIED | 4 | Denied: The audit is complete, but the ad has been found unacceptable in some material aspect and is disapproved for use. |
| CHANGE_RESUBMIT | 5 | Changed; Resubmission Requested: A version of the ad has been detected in use that is materially different from the version that was previously audited, which may result in rejection during use until the ad is resubmitted for audit and approved. Vendors need to communicate offline as to the criteria that constitutes a material change. |



<a name="adcom.CategoryTaxonomy"/>

### CategoryTaxonomy
This enum identiifes the taxonomy in effect when content categories are listed.
http://www.iab.com/guidelines/taxonomy

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_CAT_TAX | 0 | Equivalent to an unset value. |
| IAB_CNTNT_CAT_TAX_1_0 | 1 | IAB Content Category Taxonomy 1.0 |
| IAB_CNTNT_CAT_TAX_2_0 | 2 | IAB Content Category Taxonomy 2.0 |
| IAB_AD_PROD_TAX_1_0 | 3 | IAB Ad Product Taxonomy 1.0 |



<a name="adcom.ClickType"/>

### ClickType
The following enum defines the types of creative action (i.e., click) behavior types.

| Name | Number | Description |
| ---- | ------ | ----------- |
| NON_CLICKABLE | 0 | Non-Clickable |
| CLICKABLE_UNKNOWN | 1 | Details Unknown |
| CLICKABLE_EMBEDDED | 2 | Embedded Browser/Webview |
| CLICKABLE_NATIVE | 3 | Native Browser |



<a name="adcom.CompanionType"/>

### CompanionType
The following enum defines the options to indicate markup types allowed for companion ads that
apply to video and audio ads. This enum is derived from VAST 2.0&#43; and DAAST 1.0&#43; specifications.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_COMP_TYPE | 0 | Equivalent to an unset value. |
| STATIC_RSRC | 1 | Static resource. |
| HTML_RSRC | 2 | HTML resource. |
| IFRAME_RSRC | 3 | Iframe resource. |



<a name="adcom.ConnectionType"/>

### ConnectionType
The following enum defines the options for the type of device connectivity.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_CONN_TYPE | 0 | Equivalent to an unset value. |
| WIRED | 1 | Wired ethernet connection. |
| WIFI | 2 | WIFI. |
| CELL_UNKNOWN | 3 | Cellular Network - unknown generation. |
| CELL_2G | 4 | Cellular Network - 2g. |
| CELL_3G | 5 | Cellular Network - 3g. |
| CELL_4G | 6 | Cellular Network - 4g. |
| CELL_5G | 7 | Cellular Network - 5g. |



<a name="adcom.ContentContext"/>

### ContentContext
The following enum defines the various options for indicating the type of content being used or 
consumed by the user in which ads may appear. This enum has values derived from the TAG 
Inventory Quality Guidelines (IQG).

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_CON_CON | 0 |  |
| VIDEO | 1 | Video (i.e., video file or stream such as Internet TV broadcasts). |
| GAME | 2 | Game (i.e., an interactive software game). |
| MUSIC | 3 | Music (i.e., audio file or stream such as Internet radio broadcasts). |
| APPLICATION | 4 | Application (i.e., an interactive software application). |
| TEXT | 5 | Text (i.e., primarily textual document such as a web page, eBook, or news article). |
| OTHER | 6 | Other (i.e., none of the other categories applies). |
| UNKNOWN | 7 | Unknown content context. |



<a name="adcom.Creative.Attribute"/>

### Creative.Attribute
The following enum defines a standard list of creative attributes that can describe an actual ad
or restrictions relative to a given placement.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_ATTR | 0 | Equivalent to an unset value. |
| AUDIO_AUTOPLAY | 1 | Audio Ad (Autoplay). |
| AUDIO_USER_INIT | 2 | Audio Ad (User Initiated). |
| EXPANDABLE_AUTO | 3 | Expandable (Automatic). |
| EXPANDABLE_ONCLICK | 4 | Expandable (User Initiated - Click). |
| EXPANDABLE_ONROLLOVER | 5 | Expandable (User Initiated - Rollover). |
| IB_VIDEO_AUTO | 6 | In-Banner Video Ad (Autoplay). |
| IB_VIDEO_USER_INIT | 7 | In-Banner Video Ad (User Initiated). |
| POP | 8 | Pop (e.g., Over, Under, or Upon Exit). |
| PROVOCATIVE | 9 | Provocative or Suggestive Imagery. |
| ANNOYING | 10 | Shaky, Flashing, Flickery, Extreme Animation, Smileys. |
| SURVEYS | 11 | Surveys. |
| TEXT_ONLY | 12 | Text Only |
| USER_INTERACTIVE | 13 | User Interactive (e.g., Embedded Games). |
| DIALOG_ALERT | 14 | Windows Dialog or Alert Style. |
| AUDIO_ON_OFF | 15 | Has Audio On/Off Button. |
| SKIP_BUTTON | 16 | Ad Provides Skip Button (e.g., VPAID-rendered skip button on pre-roll video). |
| ADOBE_FLASH | 17 | Adobe Flash. |
| RESPONSIVE | 18 | Responsive; Sizeless; Fluid (i.e., creatives that dynamically resize to env). |



<a name="adcom.Creative.AudioType"/>

### Creative.AudioType
The following enum defines the various subtypes of audio ad creatives.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_AT | 0 | Equivalent to an unset value. |
| DAAST_1_0 | 1 | DAAST 1.0 |
| DAAST_1_0_WRAP | 2 | DAAST 1.0 Wrapper |



<a name="adcom.Creative.DisplayType"/>

### Creative.DisplayType
The following enum defines the various subtypes of display ad creatives.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_DT | 0 | Equivalent to an unset value. |
| HTML | 1 | HTML |
| AMPHTML | 2 | AMP HTML |
| IMAGE | 3 | Structured Image object |
| NATIVE | 4 | Structured Native Object |



<a name="adcom.Creative.VideoType"/>

### Creative.VideoType
The following enum defines the various subtypes of video ad creatives.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_VT | 0 | Equivalent to an unset value. |
| VAST_1_0 | 1 | VAST 1.0 |
| VAST_2_0 | 2 | VAST 2.0 |
| VAST_3_0 | 3 | VAST 3.0 |
| VAST_1_0_WRAP | 4 | VAST 1.0 Wrapper |
| VAST_2_0_WRAP | 5 | VAST 2.0 Wrapper |
| VAST_3_0_WRAP | 6 | VAST 3.0 Wrapper |
| VAST_4_0 | 7 | VAST 4.0 |
| VAST_4_0_WRAP | 8 | VAST 4.0 Wrapper |
| VAST_4_1 | 9 | VAST 4.1 |
| VAST_4_1_WRAP | 10 | VAST 4.1 Wrapper |



<a name="adcom.DOOHVenueType"/>

### DOOHVenueType
This enum presents the digital out-of-home venue types and is derived from the DPAA Programmatic 
Standards.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_DOOH_VT | 0 | Equivalent to an unset value. |
| AIRBORNE | 1 | Airborne. |
| AIRPORT_GENERAL | 2 | Airports - General. |
| AIRPORT_BAG_CLAIM | 3 | Airports - Baggage Claim. |
| AIRPORT_TERMINAL | 4 | Airports - Terminal |
| AIRPORT_LOUNGE | 5 | Airports - Lounges. |
| ATM | 6 | ATMs. |
| BACKLIGHT | 7 | Backlights. |
| BAR | 8 | Bars. |
| BENCH | 9 | Benches. |
| BIKE_RACK | 10 | Bike rack. |
| BULLETIN | 11 | Bulletins. |
| BUS | 12 | Buses. |
| CAFE | 13 | Cafes. |
| CASUAL_DINING | 14 | Casual Dining Restaurants. |
| CHILD_CARE | 15 | Child Care. |
| CINEMA | 16 | Cinema. |
| CITY_INFO_PANEL | 17 | City Information Panels. |
| CONVENIENCE_STORE | 18 | Convenience Stores. |
| DED_WILD_POSTING | 19 | Dedicated Wild Posting. |
| DOC_OFFICE_GEN | 20 | Doctors Offices - General. |
| DOC_OFFICE_OB | 21 | Doctors Offices - Obstetrics. |
| DOC_OFFICE_PEDS | 22 | Doctors Offices - Pediatrics. |
| FAMILY_ENT | 23 | Family entertainment. |
| FERRY | 24 | Ferries. |
| FINANCIAL_SERVICE | 25 | Financial Services. |
| GAS_STATION | 26 | Gas Stations. |
| GOLF_COURSE | 27 | Golf Courses. |
| GYM | 28 | Gyms. |
| HOSPITAL | 29 | Hospitals. |
| HOTEL | 30 | Hotels. |
| JR_POSTER | 31 | Junior Posters. |
| KIOSK | 32 | Kiosks. |
| MALL_GENERAL | 33 | Malls - General. |
| MALL_FOOD_COURT | 34 | Malls - Food Courts. |
| MARINE | 35 | Marine. |
| MOBILE_BILLBOARD | 36 | Mobile Billboards. |
| MOVIE_THEATER_LOB | 37 | Movie Theater Lobbies. |
| NEWSSTAND | 38 | Newsstands. |
| OFFICE_BUILDING | 39 | Office Buildings. |
| PHONE_KIOSK | 40 | Phone Kiosks. |
| POSTER | 41 | Posters. |
| QSR | 42 | QSR. |
| RAIL | 43 | Rail. |
| RECEPTACLE | 44 | Receptacles. |
| RESORT | 45 | Resorts / Leisure. |
| RETAIL | 46 | Retail. |
| SALON | 47 | Salons. |
| SHELTER | 48 | Shelters. |
| SPORTS_ARENA | 49 | Sports Arenas. |
| SUBWAY | 50 | Subway. |
| TAXI_WRAP_VEHICLE | 51 | Taxis / Wrapped vehicles. |
| TRUCKSIDE | 52 | Truckside. |
| UNIVERSITY | 53 | Universities. |
| URBAN_PANEL | 54 | Urban Panels. |
| VET_OFFICE | 55 | Veterinarian Offices. |
| WALL_SPECTACULAR | 56 | Walls / Spectaculars. |
| OTHER_X | 57 | Other. |



<a name="adcom.DeliveryMethod"/>

### DeliveryMethod
The following enum defines the various options for the delivery of video or audio content.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_DEL_METH | 0 | Equivalent to an unset value. |
| STREAMING | 1 | Streaming video or audio. |
| PROGRESSIVE | 2 | Progressive video or audio. |
| DOWNLOAD | 3 | Downloadable video or audio. |



<a name="adcom.DeviceType"/>

### DeviceType
The following enum defines the types of devies. This enum has values derived from the TAG
Inventory Quality Guidelines (IQG).

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_DEV_TYPE | 0 | Equivalent to an unset value. |
| MOBILE_TABLET | 1 | Mobile/Tablet - General. |
| PC | 2 | Personal Computer. |
| CONNECTED_TV | 3 | Connected TV. |
| PHONE | 4 | Smart Phone. |
| TABLET | 5 | Tablet. |
| CONNECTED_DEV | 6 | Connected Device. |
| SET_TOP_BOX | 7 | Set Top Box. |



<a name="adcom.DisplayContextType"/>

### DisplayContextType
The following enum defines the types of context in which a native ad may appear (i.e., the type 
of content surrounding the ad on the page). This is intended to denote primary content although 
other content may also appear on the page. Note that there are two levels of detail grouped by 
10s (i.e., 12 is a refined case of 100).

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_DISP_CT | 0 | Equivalent to an unset value. |
| CONTENT_CENTRIC | 10 | Content-centric context (e.g., newsfeed, article, image gallery, video gallery, etc.). |
| ARTICLE | 11 | Primarily article content, which could include images, etc. as part of the article. |
| VIDEO_X | 12 | Primarily video content. |
| AUDIO | 13 | Primarily audio content. |
| IMAGE | 14 | Primarily image content. |
| USER_GENERATED | 15 | User generated content (e.g., forums, comments, etc). |
| SOCIAL | 20 | Social-centric context (e.g., social network feed, email, chat, etc). |
| EMAIL | 21 | Primarily email content. |
| CHAT | 22 | Primarily chat/IM content. |
| PRODUCT | 30 | Product context (e.g., product listings, details, recommendations, reviews, etc.). |
| APP_STORE | 31 | App store/marketplace. |
| PRODUCT_REVIEWS | 32 | Product reviews site primarily, which may sell product secondarily. |



<a name="adcom.DisplayPlacementType"/>

### DisplayPlacementType
The following enum defines the general types of display placements; the locations where a 
native ad may be shown in relationship to the surrounding content.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_DISP_PT | 0 | Equivalent to an unset value. |
| FEED_CONTENT | 1 | In the feed of content (e.g., as an item inside the organic feed, grid, |
| ATOMIC_CONTENT | 2 | listing carousel, etc.).

In the atomic unit of the content (e.g., in the article page or single image page). |
| OUTSIDE_CONTENT | 3 | Outside the core content (.e.g, in the ads section on the right rail, as a banner |
| RECOMMENDATION | 4 | style placement near the content, etc.).

Recommendation widget; most commonly presented below article content. |



<a name="adcom.EventTrackingMethod"/>

### EventTrackingMethod
This enum lists the available methods of tracking of ad events. Vendor specific codes may
include custom measurement companies (e.g., Moat, Doubleverify, IAS, etc.).

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_EVENT_TM | 0 | Equivalent to an unset value. |
| IMAGE_PIXEL | 1 | Image-Pixel: URL provided will be inserted as a 1x1 pixel at time of the event. |
| JAVASCRIPT | 2 | JavaScript : URL provided will be inserted as a JavaScript tag at time of the event. |



<a name="adcom.EventType"/>

### EventType
The following enum defines the types of ad events available for tracking. These types refer to 
the actual event, timing, etc.; not the method of firing. Scripts that are performing 
measurement should be deployed at impression time.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_EVENT_T | 0 | Equivalent to an unset value. |
| IMPRESSION | 1 | impression: Initial creative rendering. |
| VIEWABLE_MRC50 | 2 | viewable-mrc50: Visible impression using MRC definition of 50% in view for 1 second. |
| VIEWABLE_MRC100 | 3 | viewable-mrc100: 100% in view for 1 second (i.e., the GroupM standard). |
| VIEWABLE_VID50 | 4 | viewable-video50: Visible impression for video using MRC definition of |



<a name="adcom.ExpandableDirection"/>

### ExpandableDirection
The following enum defines the directions in which an expandable ad may expand, given the 
positioning of the ad unit on the page and constraints imposed by the content.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_EXPAND_D | 0 | Equivalent to an unset value. |
| LEFT | 1 |  |
| RIGHT | 2 |  |
| UP | 3 |  |
| DOWN | 4 |  |
| FULLSCREEN | 5 |  |



<a name="adcom.LinearityMode"/>

### LinearityMode
The following enum indicates the options for media linearity, typically for video.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_LIN_M | 0 | Equivalent to an unset value. |
| LINEAR | 1 | Linear (i.e., In-Stream such as Pre-Roll, Mid-Roll, Post-Roll) |
| NONLINEAR | 2 | Non-Linear (i.e., Overlay) |



<a name="adcom.LocationService"/>

### LocationService
The following enum defines the services and/or vendors used for resolving IP addresses to
geolocations.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_LOC_S | 0 | Equivalent to an unset value. |
| IP2LOCATION | 1 | ip2location. |
| NEUSTAR | 2 | Neustar (Quova). |
| MAXMIND | 3 | MaxMind. |
| NETAQUITY | 4 | NetAquity (Digital Element). |



<a name="adcom.LocationType"/>

### LocationType
The following enum defines the options to indicate how the geographic information was determined.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_LOC_T | 0 | Equivalent to an unset value. |
| GPS_LOC_SERVICE | 1 | GPS/Location Services. |
| IP_ADDRESS | 2 | IP Address. |
| USER_PROVIDED | 3 | User Provided (e.g., registration data). |



<a name="adcom.MediaRating"/>

### MediaRating
The following enum defines the media ratings used in describing content based on the TAG 
Inventory Quality Guidelines (IQG) v2.1 categorization. Refer to 
www.iab.com/guidelines/digital-video-suite for more information.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_MEDIA_R | 0 | Equivalent to an unset value. |
| ALL_AUDIENCES | 1 | All Audiences. |
| OVER_12 | 2 | Everyone Over Age 12. |
| MATURE | 3 | Mature Audiences. |



<a name="adcom.NativeDataAssetType"/>

### NativeDataAssetType
The following enum defines the common data asset types. This list is non-exhaustive and is 
intended to be expanded over time. Size recommendations are noted as &#34;maximum length of at 
least&#34;, which means the publisher or supply platform should support a maximum length of at least
this value and the buying platform knows that a string of this size should be accepted.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_NATIVE_DAT | 0 | Equivalent to an unset value. |
| SPONSORED | 1 | sponsored: &#34;Sponsored By&#34; message which should contain the brand name of the sponsor. Recommended maximum length of at least 25 characters. |
| DESCRIPTIVE | 2 | desc: Descriptive text associated with the product or service being advertised. Long text lengths may be truncated or ellipsed when rendered. Recommended maximum length of at least 140 characters. |
| RATING | 3 | rating: Numeric rating of the product (e.g., an app&#39;s rating). Recommended integer range of 0-5. |
| LIKES | 4 | likes: Number of social ratings or &#34;likes&#34; of the product. |
| DOWNLOADS | 5 | downloads: Number downloads and/or installs of the product. |
| PRICE | 6 | price: Price of the product, app, or in-app purchase. Value should include currency symbol in localized format (e.g., &#34;$10&#34;). |
| SALEPRICE | 7 | saleprice: Sale price that can be used together with &#34;price&#34; to indicate a comparative discounted price. Value should include currency symbol in localized format (e.g. &#34;$8.50&#34;). |
| PHONE_X | 8 | phone: A formatted phone number. |
| ADDRESS | 9 | address: A formatted address. |
| DESC2 | 10 | desc2: Additional descriptive text associated with the product. |
| DISPLAY_URL | 11 | displayurl: Display URL for the ad. To be used when sponsoring entity does not own the content (e.g., &#34;Sponsored by Brand on Site&#34;, where Site is specified in this data asset). |
| CTA_TEXT | 12 | ctatext: Description of the call to action (CTA) button for the destination URL. Recommended maximum length of at least 15 characters. |



<a name="adcom.NativeImageAssetType"/>

### NativeImageAssetType
The following enum defines the set of common image asset types. This list is non-exhaustive and 
is intended to be expanded over time. Size recommendations are noted as &#34;maximum height or width
of at least&#34;, which means the publisher or supply platform should support a maximum height or 
width of at least this value and the buying platform knows that an image of this size should be 
accepted.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_NATIVE_IAT | 0 | Equivalent to an unset value. |
| ICON | 1 | Icon: Icon image. Maximum height at least 50 device independent pixels (DIPS); aspect ratio 1:1. |
| MAIN | 3 | Main: Large image preview for the ad. At least one of 2 size variants required: Small: Maximum height at least 627 DIPS; maximum width at least 627, 836, or 1198 DIPS (i.e., aspect ratios of 1:1, 4:3, or 1.91:1, respectively). Large: Maximum height at least 200 DIPS; maximum width at least 200, 267, or 382 DIPS (i.e., aspect ratios of 1:1, 4:3, or 1.91:1, respectively). |



<a name="adcom.OperatingSystem"/>

### OperatingSystem
The following enum defines the options for device operating system.

| Name | Number | Description |
| ---- | ------ | ----------- |
| OTHER_Y | 0 | Other Not Listed |
| NINTENDO_3DS | 1 | Nintendo 3DS System Software |
| ANDROID | 2 | Android |
| APPLE_TV | 3 | Apple TV Software |
| ASHA | 4 | Asha |
| BADA | 5 | Bada |
| BLACKBERRY | 6 | BlackBerry |
| BREW | 7 | BREW |
| CHROMEOS | 8 | ChromeOS |
| DARWIN | 9 | Darwin |
| FIREOS | 10 | FireOS |
| FIREFOXOS | 11 | FirefoxOS |
| HELENOS | 12 | HelenOS |
| IOS | 13 | iOS |
| LINUX | 14 | Linux |
| MACOS | 15 | MacOS |
| MEEGO | 16 | MeeGo |
| MORPHOS | 17 | MorphOS |
| NETBSD | 18 | NetBSD |
| NUCLEUSPLUS | 19 | NucleusPLUS |
| PSVITA | 20 | PS Vita System Software |
| PS3 | 21 | PS3 System Software |
| PS4 | 22 | PS4 System Software |
| PSP | 23 | PSP System Software |
| SYMBIAN | 24 | Symbian |
| TIZEN | 25 | Tizen |
| WATCHOS | 26 | WatchOS |
| WEBOS | 27 | WebOS |
| WINDOWS | 28 | Windows |



<a name="adcom.PlacementPosition"/>

### PlacementPosition
The following enum defines the placement positions as a relative measure of visibility or 
prominence. This enum has values derived from the TAG Inventory Quality Guidelines (IQG).

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_PLACE_P | 0 | Equivalent to an unset value. |
| ATF | 1 | Above the Fold. |
| LOCKED | 2 | Locked (i.e., fixed position). |
| BTF | 3 | Below the Fold. |
| HEADER | 4 | Header. |
| FOOTER | 5 | Footer. |
| SIDEBAR | 6 | Sidebar. |
| FULLSCREEN_X | 7 | Full screen. |



<a name="adcom.PlaybackCessationMode"/>

### PlaybackCessationMode
The following enum defines the various modes for when media playback terminates.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_PLAYBACK_CM | 0 | Equivalent to an unset value. |
| ON_COMPLETION | 1 | On Video Completion or when Terminated by User. |
| ON_VIEWPORT_EXIT | 2 | On Leaving Viewport or when Terminated by User. |
| ON_EXIT_FLOAT | 3 | On Leaving Viewport Continues as a Floating/Slider Unit until Video |



<a name="adcom.PlaybackMethod"/>

### PlaybackMethod
The following table lists the various media playback methods.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_PLAYBACK_M | 0 | Equivalent to an unset value. |
| PAGE_LOAD_SOUND_ON | 1 | Initiates on Page Load with Sound On. |
| PAGE_LOAD_SOUND_OFF | 2 | Initiates on Page Load with Sound Off by Default. |
| CLICK_SOUND_ON | 3 | Initiates on Click with Sound On. |
| MOUSEOVER_SOUND_ON | 4 | Initiates on Mouse-Over with Sound On. |
| VIEWPORT_SOUND_ON | 5 | Initiates on Entering Viewport with Sound On. |
| VIEWPORT_SOUND_OFF | 6 | Initiates on Entering Viewport with Sound Off. |



<a name="adcom.ProductionQuality"/>

### ProductionQuality
The following enum defines the options for content quality. These values are defined by the IAB;
refer to www.iab.com/wp-content/uploads/2015/03/long-form-video-final.pdf for more information.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_PROD_Q | 0 | Equivalent to an unset value. |
| PROFESSIONAL | 1 | Professionally Produced. |
| PROSUMER | 2 | Prosumer. |
| UGC | 3 | User Generated Content. |



<a name="adcom.SizeUnit"/>

### SizeUnit
The following enum lists the units of height and width used by creatives, assets, and placement
specifications where noted.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_SIZE_U | 0 | Equivalent to an unset value. |
| DIPS | 1 | Device Independent Pixels. |
| INCH | 2 | Inches. |
| CENTIMETER | 3 | Centimeters. |



<a name="adcom.VideoPlacementSubtype"/>

### VideoPlacementSubtype
The following enum lists the various types of video placements derived largely from the IAB 
Digital Video Guidelines.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNSET_VIDEO_PS | 0 | Equivalent to an unset value. |
| IN_STREAM | 1 | In-Stream: Played before, during or after the streaming video content that the consumer has requested (e.g., Pre-roll, Mid-roll, Post-roll). |
| IN_BANNER | 2 | In-Banner: Exists within a web banner that leverages the banner space to deliver a video experience as opposed to another static or rich media format. The format relies on the existence of display ad inventory on the page for its delivery. |
| IN_ARTICLE | 3 | In-Article: Loads and plays dynamically between paragraphs of editorial content; existing as a standalone branded message. |
| IN_FEED | 4 | In-Feed: Found in content, social, or product feeds. |
| INTERSTITIAL | 5 | Interstitial/Slider/Floating: Covers the entire or a portion of screen area, but is always on screen while displayed (i.e. cannot be scrolled out of view). |



<a name="adcom.VolumeNormalizationMode"/>

### VolumeNormalizationMode
The following enum defines the types of volume normalization modes, typically for audio.

| Name | Number | Description |
| ---- | ------ | ----------- |
| NO_NORMALIZATION | 0 |  |
| VOL_AVG_NORMALIZATION | 1 | Ad Volume Average Normalized to Content. |
| VOL_PEAK_NORMALIZATION | 2 | Ad Volume Peak Normalized to Content. |
| LOUDNESS_NORMALIZATION | 3 | Ad Loudness Normalized to Content. |
| VOL_CUST_NORMALIZATION | 4 | Custom Volume Normalization. |


 

 

 



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

