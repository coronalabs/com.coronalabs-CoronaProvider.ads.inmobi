# inmobi.show()

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Function][api.type.Function]
> __Return value__      none
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          ads, advertising, inmobi
> __See also__          [ads.hide()][plugin.ads-inmobi.hide]
>								[ads.init()][plugin.ads-inmobi.init]
>								[inmobi.*][plugin.ads-inmobi]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

`ads.show()` begins showing ads at the specified screen location.


## Test Ads

To receive test ads, you must set up diagnostics for your property. First, you'll need to mark your property in test mode, then you'll need to send ad requests from a test device associated with that property. More Information on setting up diagnostics is available [here](http://www.inmobi.com/support/art/29128996/22868557/setting-up-diagnostics-to-identify-integration-issues-and-monetization-opportunities/#settestmode).


## Syntax

	ads.show( adUnitType [, params] )

##### adUnitType ~^(required)^~
_[String][api.type.String]._ InMobi supports the following types:

* `"banner320x50"`
* `"banner300x250"`
* `"banner728x90"`
* `"banner468x60"`
* `"banner120x600"`
* `"interstitial"`

##### params ~^(optional)^~
_[Table][api.type.Table]._ A table that specifies properties for the ad request — see the next section for details.


## Parameter Reference

The `params` table can include properties for the ad request, including demographic information to provide ads that are more relevant.

##### x ~^(optional)^~
_[Number][api.type.Number]._ The left position of the ad. Defaults to `0`. Does not apply to the `"interstitial"` unit type.

##### y ~^(optional)^~
_[Number][api.type.Number]._ The top position of the ad. Defaults to `0`. Does not apply to the `"interstitial"` unit type.

##### interval ~^(optional)^~
_[Number][api.type.Number]._ The ad refresh time, in seconds.

##### testMode ~^(optional)^~
_[Boolean][api.type.Boolean]._ Set to `true` for testing account. Defaults to `false`.

##### logLevel ~^(optional)^~
_[Constant][api.type.Constant]._ This will print the InMobi logs. The following values are valid:

* `"LOGLEVEL_NONE"`
* `"LOGLEVEL_DEBUG"`
* `"LOGLEVEL_VERBOSE"`

##### gender ~^(optional)^~
_[Constant][api.type.Constant]._ The following values are valid:

* `"GENDER_MALE"`
* `"GENDER_FEMALE"`
* `"GENDER_UNKNOWN"`	

##### education ~^(optional)^~
_[Constant][api.type.Constant]._ The following values are valid:

* `"EDUCATION_HIGHSCHOOLORLESS"`
* `"EDUCATION_COLLEGEORGRADUATE"`
* `"EDUCATION_POSTGRADUATEORABOVE"`
* `"EDUCATION_UNKNOWN"`

##### ethnicity ~^(optional)^~
_[Constant][api.type.Constant]._ The following values are valid:

* `"ETHNICITY_ASIAN"`
* `"ETHNICITY_HISPANIC"`
* `"ETHNICITY_AFRICAN_AMERICAN"`
* `"ETHNICITY_CAUCASIAN"`
* `"ETHNICITY_OTHER"`
* `"ETHNICITY_UNKNOWN"`

##### maritalStatus ~^(optional)^~
_[Constant][api.type.Constant]._ The following values are valid:

* `"MARITAL_STATUS_SINGLE"`
* `"MARITAL_STATUS_DIVORCED"`
* `"MARITAL_STATUS_ENGAGED"`
* `"MARITAL_STATUS_RELATIONSHIP"`
* `"MARITAL_STATUS_UNKNOWN"`

##### hasChildren ~^(optional)^~
_[Constant][api.type.Constant]._ The following values are valid:

* `"TRUE"`
* `"FALSE"`
* `"UNKNOWN"`

##### sexualOrientation ~^(optional)^~
_[Constant][api.type.Constant]._ The following values are valid:

* `"SEXUAL_ORIENTATION_STRAIGHT"`
* `"SEXUAL_ORIENTATION_BISEXUAL"`
* `"SEXUAL_ORIENTATION_GAY"`
* `"SEXUAL_ORIENTATION_UNKNOWN"`

##### dob ~^(optional)^~
_[String][api.type.String]._ Date of birth formatted as `DD-MM-YYYY`.

##### income ~^(optional)^~
_[Number][api.type.Number]._ Annual income, for example `50000`. The rate should be converted to USD.

##### age ~^(optional)^~
_[Number][api.type.Number]._ Age value in the range of 1-100.

##### language ~^(optional)^~
_[String][api.type.String]._ ISO language value, for example `"eng"`. Valid options can be located [here](http://www-01.sil.org/iso639-3/iso-639-3.tab).

##### postalCode ~^(optional)^~
_[String][api.type.String]._ Postal code as a string, for example `"12345"`.

##### areaCode ~^(optional)^~
_[String][api.type.String]._ Area code (phone) as a string, for example `"456"`.

##### interests ~^(optional)^~
_[String][api.type.String]._ Comma-delimited list of interests as a string, for example `"reading, writing, eating"`.

##### deviceIdMasks ~^(optional)^~
_[Array][api.type.Array]._ A table array of values, for example `{ "EXCLUDE_VENDOR_ID" }`. The following values are valid:

* `"EXCLUDE_ODIN1"` (iOS/Android)
* `"EXCLUDE_FB_ATTR_ID"` (iOS/Android)
* `"EXCLUDE_VENDOR_ID"` (iOS)
* `"EXCLUDE_UDID"` (iOS)
* `"EXCLUDE_ADVERTISER_ID"` (iOS)
* `"EXCLUDE_UM5"` (Android)
* `"INCLUDE_NONE"` (Android)
	

## Example

``````lua
local ads = require( "ads" )

local function adListener( event )
	if ( event.isError ) then
		--Failed to receive an ad
	end
end

ads.init( "inmobi", "myAppId", adListener )

ads.show( "banner320x50",
	{
		x = 0,
		y = 0,
		interval = 60,
		testMode = true,
		postalCode = "12345",
		areaCode = "456",
		dob = "12-10-1990",
		logLevel = "LOGLEVEL_DEBUG",
		income = 50000,
		age = 38,
		gender = "GENDER_MALE",
		education = "EDUCATION_UNKNOWN",
		ethnicity = "ETHNICITY_UNKNOWN",
		maritalStatus = "MARITAL_STATUS_UNKNOWN",
		hasChildren = "FALSE",
		sexualOrientation = "SEXUAL_ORIENTATION_UNKNOWN",
		language = "eng",
		interests = "reading, writing, eating"
	})
``````