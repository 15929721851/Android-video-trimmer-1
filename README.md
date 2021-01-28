[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/hyperium/hyper/master/LICENSE)
[![](https://jitpack.io/v/a914-gowtham/Android-video-trimmer.svg)](https://jitpack.io/#a914-gowtham/Android-video-trimmer)
[![](https://jitpack.io/v/a914-gowtham/Android-video-trimmer/month.svg)](https://jitpack.io/#a914-gowtham/Android-video-trimmer)

# Android-video-trimmer

##### Helps to trim local videos with many customizations on Android applications using exoplayer2 and FFmpeg [Demo app](https://play.google.com/store/apps/details?id=com.gowtham.videotrimmerdemo&hl=en_IN). 

![](https://github.com/a914-gowtham/Android-video-trimmer/blob/master/demo.gif)

## How to use
*For a working implementation, please have a look at the Sample Project*

1. Include the library as local library project.

+ Add the dependency to your app `build.gradle` file
 ```gradle
 dependencies {
    implementation 'com.github.a914-gowtham:Android-video-trimmer:1.5.2'
 }   
 ```
 + Add to project's root `build.gradle` file:
```gradle
allprojects {
	repositories {
		maven { url 'https://jitpack.io' }
	}
}
```
2. Add the code for opening Trim Activity.
```java
TrimVideo.activity(String.valueOf(videoUri))
//        .setCompressOption(new CompressOption()) //empty constructor for default compress option
          .setHideSeekBar(true)
          .setDestination("/storage/emulated/0/DCIM/TESTFOLDER")  //default output path /storage/emulated/0/DOWNLOADS
          .start(this);
```
3. Override `onActivityResult` method in your activity to get trim result
```java
@Override
public void onActivityResult(int requestCode, int resultCode, Intent data) {
  if (requestCode == TrimVideo.VIDEO_TRIMMER_REQ_CODE && data != null) {
            Uri uri = Uri.parse(TrimVideo.getTrimmedVideoPath(data));
            Log.d(TAG,"Trimmed path:: "+uri);
        }
}
```
## Customization

#### Video Compress:
```java
.setCompressOption(new CompressOption(bitRate))  //pass empty constructor for default compressoption
```
  * `BitRate`   Bitrate Can be between 1 to 10.Lower bitrate can reduce the quality and size of the video.
   
#### Hide Player Seekbar:
```java
.setHideSeekBar(true) //default value is false 
```

### Custom TrimTypes

#### TrimType Default:
```java
TrimVideo.activity(videoUri)
          .start(this);
```

#### TrimType Fixed Duration:
```java
TrimVideo.activity(videoUri)
          .setTrimType(TrimType.FIXED_DURATION)
          .setFixedDuration(30) //seconds
          .start(this);
```

#### TrimType Minimum Duration:
```java
TrimVideo.activity(videoUri)
          .setTrimType(TrimType.MIN_DURATION)
          .setMinDuration(30) //seconds
          .start(this);
```

#### TrimType Min-Max Duration:
```java
TrimVideo.activity(videoUri)
          .setTrimType(TrimType.MIN_MAX_DURATION)
          .setMinToMax(10, 30)  //seconds
          .start(this);
```

## Proguard Rules
```pro
-dontwarn com.gowtham.library**
-keep class com.gowtham.library** { *; }
-keep interface com.gowtham.library** { *; }
```

## Compatibility
  
  * Library - Android Kitkat 4.4+ (API 19)
  * Sample - Android Kitkat 4.4+ (API 19)
  
## ChangeLog
### Version 1.5.2
  * First version of litr-version
  
## Thanks to 
[LiTr](https://github.com/linkedin/LiTr)

## Support 
Show your support by giving star to this repository.that's how i know the usage of this library so this can keep me motivated to make improvements 
  
## Collaboration
There are many ways of improving and adding more features, so feel free to collaborate with ideas, issues and/or pull requests. 
