# inmobi.*

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [CoronaProvider][api.type.CoronaProvider]
> __Library__           [ads.*][api.library.ads]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          ads, advertising, inmobi
> __Availability__		Basic, Pro, Enterprise
> __Platforms__			Android, iOS
> --------------------- ------------------------------------------------------------------------------------------


## Overview

The InMobi plugin offers easy integration of inMobi ads using the [ads][api.library.ads] library and [ads.init()][plugin.ads-inmobi.init].


## Registration

Using InMobi requires a free InMobi account &mdash; please [register](http://inmobi.com) before proceeding.


## Syntax

	local ads = require( "ads" )


## Functions

#### [ads.init()][plugin.ads-inmobi.init]

#### [ads.show()][plugin.ads-inmobi.show]

#### [ads.hide()][plugin.ads-inmobi.hide]


## Project Settings

To use this plugin, add an entry into the `plugins` table of `build.settings`. When added, the build server will integrate the plugin during the build phase.

``````lua
settings =
{
	plugins =
	{
		["CoronaProvider.ads.inmobi"] =
		{
			publisherId = "com.coronalabs",
		},
	},		
}
``````

### Android

For Android, the following permissions/features are automatically added when using this plugin:

``````lua
	android =
	{
		usesPermissions =
		{
			"android.permission.INTERNET",
			"android.permission.READ_PHONE_STATE",
			"android.permission.ACCESS_NETWORK_STATE",
			"android.permission.ACCESS_ASSISTED_GPS",
			"android.permission.ACCESS_COARSE_LOCATION",
			"android.permission.ACCESS_FINE_LOCATION",
			"android.permission.ACCESS_GPS",
			"android.permission.ACCESS_LOCATION",
			"android.permission.ACCESS_WIFI_STATE",
			"android.permission.CALL_PHONE",
			"android.permission.CHANGE_WIFI_STATE",
			"android.permission.MODIFY_AUDIO_SETTINGS",
			"android.permission.READ_LOGS",
			"android.permission.RECORD_AUDIO",
			"android.permission.VIBRATE",
			"android.permission.WRITE_EXTERNAL_STORAGE",
		},
	},
``````


## Sample

[https://github.com/coronalabs/plugins-sample-ads-InMobi/](https://github.com/coronalabs/plugins-sample-ads-InMobi)


## Support

* [http://inmobi.com/](https://www.inmobi.com/support/)
* [Corona Forums](http://forums.coronalabs.com/forum/611-inmobi/)
