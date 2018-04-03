# Using Pubguard on Android with Proguard

The Pubguard Library requires certain advertising SDK classnames to be accessible in order to monitor the content.

Proguard will by default rename these classes therefore you are required to add the following exceptions in proguard-rules.pro:

```
##START Pubguard Library rules
-keep class com.smaato.** { *; }
-keep class com.inmobi.** { *; }
-keep class com.rfm.** { *; }
-keep class com.amazon.** { *; }
-keep class com.millennialmedia.** { *; }
-keep class com.mopub.** { *; }
-keep class com.google.android.gms.** { *; }

-keepnames class com.mopub.** { *; }
-keepnames class com.millennialmedia.** { *; }
-keepnames class com.amazon.** { *; }
-keepnames class com.rfm.** { *; }
-keepnames class com.inmobi.** { *; }
-keepnames class com.smaato.** { *; }
-keepnames class com.google.android.gms.** { *; }

-keepclasseswithmembers class * {
@com.smaato.* <methods>;
}
-keepclasseswithmembers class * {
@com.inmobi.* <methods>;
}
-keepclasseswithmembers class * {
@com.rfm.* <methods>;
}
-keepclasseswithmembers class * {
@com.amazon.* <methods>;
}
-keepclasseswithmembers class * {
@com.millennialmedia.* <methods>;
}
-keepclasseswithmembers class * {
@com.mopub.* <methods>;
}
-keepclasseswithmembers class * {
@com.google.android.gms.* <methods>;
}
##STOP Pubguard rules
```
