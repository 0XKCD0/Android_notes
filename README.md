# Android_notes
Important notes on Android studio with Kotlin


### What is android studio?
________________________________

Android is a software package and linux based operating system for mobile devices such as tablet computers and smartphones.
It is developed by Google and later the OHA (Open Handset Alliance). 

### OHA
_________________
It's a consortium of 84 companies such as google, samsung, AKM, synaptics, KDDI, Garmin, Teleca, Ebay, Intel etc.

### Features of Android
_____________________________

1) It is open-source.

2) Anyone can customize the Android Platform.

3) There are a lot of mobile applications that can be chosen by the consumer.

4) It provides many interesting features like weather details, opening screen, live RSS (Really Simple Syndication) feeds etc.

5) It provides support for messaging services(SMS and MMS), web browser, storage (SQLite), connectivity (GSM, CDMA, Blue Tooth, Wi-Fi etc.), media, handset layout etc.

### Android Architecture
___________________________________

Android architecture or Android software stack is categorized into five parts:

+ linux kernel
+ native libraries (middleware),
+ Android Runtime
+ Application Framework
+ Applications

  **Android Architecture**

  ![softwarestack](https://github.com/0XKCD0/Android_notes/assets/123825075/4257f78b-45bc-4856-9026-a851609f9101)

### APK file
___________________

An apk file is created by the framework automatically. If you want to run the android application on the mobile, transfer and install it.

### Manifest file
_____________________

Every project in Android includes a Manifest XML file, which is AndroidManifest.xml, located in the root directory of its project hierarchy. The manifest file is an important part of our app because it defines the structure and metadata of our application, its components, and its requirements. This file includes nodes for each of the Activities, Services, Content Providers, and Broadcast Receivers that make the application, and using Intent Filters and Permissions determines how they coordinate with each other and other applications.

### res/values File
______________________

The res/values folder is used to store the values for the resources that are used in many Android projects to include features of color, styles, dimensions etc.
+ colors.xml
+ strings.xml
+ styles.xml
+ dimens.xml

### Gradle file
___________________

Gradle is a build system (open source) that is used to automate building, testing, deployment, etc. “build.gradle” are scripts where one can automate the tasks.
Every Android project needs a Gradle for generating an apk from the .java and .xml files in the project.

1) Top-level build.gradle - It is located in the root project directory and its main function is to define the build configurations that will be applied to all the modules in the project. It supports :
   + buildscripts
   + dependencies
2) Module-level build.gradle - Located in the project/module directory of the project this Gradle script is where all the dependencies are defined and where the SDK versions are declared. This script has many functions in the project which include additional build types and override settings in the main/app manifest or top-level build.gradle file. It supports:

+ android: This block is used for configuring the specific android build options. 
   - compileSdkVersion – This is used to define the API level of the app and the app can use the features of this and lower level. 
+ defaultConfig: 
   - applicationId– This is used for identifying unique id for publishing of the app.
   - minSdkVersion– This defines the minimum API level required to run the application.
   - targetSdkVersion– This defines the API level used to test the app.
   - versionCode– This defines the version code of the app. Every time an update needs to be of the app, the version code needs to be increased by 1 or more.
   - versionName– This defines the version name for the app. this could be increased by much while creating an update.
+ buildTypes(release): 
   - minifyEnabled– this will enable code shrinking for release build.
   - proguardFiles– this will specify the progaurd settings file.
+ dependencies: This specifies the dependencies that are needed to build the project.


# Android Components
_________________________________

### Layouts
______________

   








