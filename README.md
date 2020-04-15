# Arena Android SDK
<!-- MarkdownTOC -->

- [Introduction](#introduction)
- [Requirements](#requirements)
- [Sample](#sample)
- [LiveBlog](#liveblog)
- [Streaming](#streaming)
- [Getting Help](#gettinghelp)
- [License](#license)

<!-- /MarkdownTOC -->

<a name="introduction"></a>
# Introduction

Integrate live blog, analytics and streaming services into your Android client applications with speed and efficiency. Our Android SDK helps you focus on the client's implementation of booting, configuring live blog and sending events.

<a name="requirements"></a>
# Requirements
 - **Minimum Android SDK**: Arena Sdk requires a minimum API level of 21.
 - **Compile Android SDK**: Arena Sdk requires you to compile against API 29 or later.


<a name="sample"></a>
# Sample
A [sample](sample) application is available that showcases the majority of the features offered by
the Arena SDK.


<a name="liveblog"></a>
# Liveblog

Integrate the live blog in real time into your Android client applications with speed and efficiency.  Our SDK helps you focus on the client's implementation of initializing, configuring and displaying the live blog.
Displays all card types in live blog format. We currently support the following cards:

##### Card Title
![Title](showcase/Title.png)

##### Card Description
![Description](showcase/Description.png)

##### Card Title And Description
![Complete](showcase/TitleAndDescrption.png)

##### Publisher
![Publisher](showcase/Publisher.png)

##### Card Pinned
![Pinned](showcase/Pinned.png)

##### Card Player Only
![PlayerOnly](showcase/PlayerOnly.png)

##### Card Player And Team
![PlayerAndTeam](showcase/PlayerAndTeam.png)


#### Step 1: Create a live blog from your dashboard


#### Step 2: Install the Live Blog SDK

Installing the Chat SDK is simple if you’re familiar with using external libraries or SDKs. To install the Chat SDK using `Gradle`, add the following lines to a `build.gradle` file at the app level.

```groovy
repositories {
    maven { url "" }
}

dependencies {
    implementation 'com.arena:liveblog:1.0.0'
}
````

#### Step 3: Configure ProGuard to shrink code and resources
When you build your APK with minifyEnabled true, add the following line to the module's ProGuard rules file.
```gradle
-keep class com.arena.liveblog.** { *; }
-keep class com.arena.streaming.** { *; }
```


#### Step 4: Setup SDK
Initialization links the SDK to the Android context, allowing you to respond to connection and status changes.
The LiveBlog.setup() method must be called once across your Android client app. It is recommended to initialize the in the onCreate() method of the Application instance.

```kotlin
LiveBlog.setup(APPLICATION, APPLICATION_ID, ENVIRONMENT)
```
*  `APPLICATION`: Base class for maintaining global application state.
*  `APPLICATION_ID`: Application identifier
*  `ENVIROMENT`: Execution environment of sdk, `PRODUCTION` being the default


#### Step 5: Start SDK
To initialize the sdk it is necessary to add the LiveBlog in the xml:

```xml
<com.arena.liveblog.LiveBlog 
        android:id="@+id/live_blog"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
```

And start the event watcher by passing the following parameters:
```kotlin
live_blog.start(PUBLISH_SLUG, EVENT_SLUG, LIFECYCLE_OWNER, CLICK_LISTENER)
```

*  `PUBLISH`: The publisher slug will be provided by Arena.
*  `EVENT_SLUG`: Live blog identifier
*  `LIFECYCLE_OWNER`: A class that has an Android lifecycle. These events can be used by custom components to handle lifecycle changes without implementing any code inside the Activity or the Fragment.
*  `CLICK_LISTENER`: Interface definition for a callback to be invoked when a view is clicked.


<a name="streaming"></a>
# Streaming

Using this mode you're controlling how the date will be displayed entirely on your side, we will provide a data stream with all information.


# Changelog

see [Releases](CHANGELOG.md)

# Getting Help
We use [GitHub Issues][1] as our bug and feature tracker both for code and for other aspects of the library (documentation, the wiki, etc.).  
Labels on issues are managed by contributors, you don't have to worry about them. Here's a list of what they mean:

 * **bug**: feature that should work, but doesn't
 * **enhancement**: minor tweak/addition to existing behavior
 * **feature**: new behavior, bigger than enhancement, it gives more bang
 * **question**: no need to modify sdk to fix the issue, usually a usage problem
 * **duplicate**: there's another issue which already covers/tracks this
 * **wontfix**: working as intended, or won't be fixed due to compatibility or other reasons
 * **non-library**: issue is not in the core library code, but rather in documentation, samples, build process, releases


# License

Arena Android SDK is proprietary software, all rights reserved. See the LICENSE file for more info.

Copyright (c) 2020  Arena Im.


[1]: https://github.com/stationfy/Arena-SDK-Android-demo/issues
