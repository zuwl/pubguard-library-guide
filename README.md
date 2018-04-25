![alt text](imgs/pg-logo-hires.jpg)

# Pubguard Library

A guide to installing Pubguard on your application, with instructions, demos and FAQs

The Pubguard Library is solution that monitors the advertising content flowing through your mobile app, protecting against unwanted content and optimising revenues.

The data from the library is then accessible via your account on the Pubguard interface where you can set up preferences, alerts and browse the gallery.

---

Table of contents
=================

<!--ts-->
* [Table of contents](#table-of-contents)
* [Android](#android)
* [iOS](#ios)
* [Change Log](#change-log)
* [Library Size](#library-size)
* [SDK support](#support)
* [Requirements](#requirements)
* [Versioning](#versioning)
* [License](#license)
* [FAQs](https://github.com/pubguard/pubguard-library-guide/wiki/FAQs)

<!--te-->

# Getting Started

These instructions will enable you to get the Pubguard library running on your iOS/Android app.

## Prerequisites

Before installing the pubguard library you will need an application key which is available from your account, in order to receive a key please signup from https://www.pubguard.com or email support@pubguard.com. The key is used in both the iOS and Android installations.

```
pubguardKey = "xxxxxxxxxxxxxxxxxxx"
```

---

# Android


The latest version of the Android Pubguard Library is **1.0.15**



### Installing

Installing the Pubguard library requires the following lines to be added to your gradle build as follows:

#### Using Maven

Please add the following lines to your **build.Gradle(Module: app)** and update the credentials to use your key in 'password':

```
repositories {
    maven {
            url 'https://customer.pubguard.com/maven/releases'

            credentials {
            username 'pubguard'
            password '${pubguardKey}'
            }
        }
}

dependencies {
...

    implementation 'com.pubguard:pubguard-client:1.0.15'

}

```


#### Initialising the Library

The Pubguard Library should be initialised once at app launch, Here's an example of how to call the init method in your AppDelegate:

```
import com.pubguard.client.Pubguard;
…

public class QuizzyApplication extends Application {

    @Override public void onCreate() {
        super.onCreate();

        Pubguard.init(this, "pubguardKey");
        }
}
```

#### Proguard

If you are using Proguard please see our section on [using Pubguard with Proguard](drd-proguard-guide.md).

---

# iOS

The latest version of the iOS Pubguard Library is **1.0.8**

### Installing

There are 2 methods of installing the Pubguard framework:

#### Using cocoapods

Please add the following line to your Podfile (adding in your app key):

```
pod 'Pubguard', podspec: 'https://customer.pubguard.com/cocoapods/pubguard-ios-framework/1.0.8/Pubguard-1.0.8.podspec?access_token=${pubguardKey}'
```

Then run "pod install --repo-update"

#### Adding the library manually

If you are adding the library manually please refer to these [instructions](ios-manual-install.md).

#### Initialising the Library

The Pubguard Library should be initialised once at app launch, Here's an example of how to call the init method in your AppDelegate:

#### Swift

The Pubguard Library is written in Obj-c so if your app is Swift please see the guide on adding a [bridging header](adding-a-bridging-header.md).

```
*Example AppDelegate.m (excerpt)*

import Pubguard
…

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    var window: UIWindow?

        func application(_ application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {

        // Initialize the Pubguard Library.
        Pubguard.initiateTrackerWithKey("pubguardKey")

        return true
    }

}
```

#### Objective-C

```
*Example AppDelegate.m (excerpt)*

#import "Pubguard/Pubguard.h"
…

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application
didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    // Initialize the Pubguard Library.
    [Pubguard initiateTrackerWithKey:@"pubguardKey"];
    return YES;
}

@end
```

---

## Changelog


For all release notes and previous versions please see our [changelog](changelog.md).


---

## Library Size

The Pubguard team understands the importance of having a small footprint and our library is optimised to be as lightweight as possible on both iOS and Android.

Here is a guide based based on our compiling with our test apps, please bear in mind the size may increase or reduce based on the amount of SDKs you use and the amount of shared dependancies.

|Dependancies| iOS   | Android |
| ---- | ----- | ------- |
|gson | | ~50kb  |
|retrofit | | ~150kb  |
| Total |~140kb | ~450kb  |

---

## Support

### Advertising SDK support

These are SDKs designed specifically for serving advertising content into your app, if you would like information on a version or vendor that is not on this list please email support@pubguard.com

| SDK     | iOS   | Android |
| ------- | ----- | ------- |
| AdColony   | 3.3.0|    |
| AmazonAd   | 2.2.15.1 | 5.8.2   |
| AppNexusSDK | 4.0.1 |    |
| FBAudienceNetwork | 4.28.0 |   |
| Firebase/AdMob | 4.10.0 | 11.8.0  |
| Google-Mobile-Ads-SDK | 7.29.0 |  |
| InMobiSDK | 7.0.4 | 7.0.4  |
| IronSourceSDK | 6.7.7.0 | |
| MMAdSDK | 6.6.0| 4.20.0 |
| mopub-ios/drd-sdk | 4.20.0| 4.20.0 |
| RFMAdSDK | 6.4.0| 6.3.2|
| SmaatoSDK | 8.2.3 | 7.2.1 |

### Mediation Support

Mediation platforms can be used to manage the various SDKs within your platform, although most platforms don't affect Pubguard's monitoring solution in any way if you do have a question please email support@pubguard.com to clarify.

| Mediator     | iOS   | Android |
| ------- | ----- | ------- |
| AATKit (addApptr)   | 2.65.34|    |

## Requirements

### iOS Requirements

+ iOS 8.0 and up
+ Xcode 9.0 and up

### Android Requirements

+ Android 5.0 and up

---

## Versioning

Please use the most up to date version at all times to ensure maximum support.

---

## License

*© 2018 Minimised Media Limited (Pubguard© 2017 All Rights Reserved)*
