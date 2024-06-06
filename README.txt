Welcome to the ArcGIS Runtime SDK for Android!

v100.14.1

----------------------------
Overview
----------------------------
The ArcGIS Runtime SDK for Android provides you with the API libraries required to build ArcGIS apps for the Android platform. Please reference the install and setup doc on the ArcGIS Runtime SDK for Android developers site for the most up to date setup guide https://developers.arcgis.com/android/install-and-set-up/

----------------------------
Release Notes
----------------------------
Please reference the release notes on the ArcGIS Runtime SDK for Android developers site for the most up to date release notes https://developers.arcgis.com/android/reference/release-notes/

----------------------------
SDK Contents
----------------------------
The ArcGIS Runtime SDK for Android contains everything you need to develop ArcGIS Android apps.
The contents of the SDK are provided below:

 + doc > API reference doc for arcgis android api.
 + legal > All the SDK license information.
 + libs > The arcgis-android aar library module.

----------------------------
Requirements
----------------------------
Please reference the system requirements notes on the ArcGIS Runtime SDK for Android developers site for the most up to date requirements https://developers.arcgis.com/android/reference/system-requirements/

----------------------------
Set up the ArcGIS Android SDK to work with local Maven repository (disconnected from the internet)
----------------------------
The following setup steps assume that you are working in a development environment that is disconnected from the internet, for example behind a firewall that doesn't allow access to Maven repositories that are hosted on the internet. If you are developing with internet access, please follow these setup steps instead:
https://developers.arcgis.com/android/install-and-set-up/
The following steps describe the setup with a Maven repository that is on your local machine, however they can be applied in a similar way if you have a Maven server set up on your network.

1. Download the arcgis-runtime-sdk-android-100.14.1.zip file.
2. Extract the contents of the archive to a location on disk.
3. From the extracted location, copy the contents of the libs/aar directory to the following location on your disk:
    mac: /Users/[user-name]/.m2/repository/com/esri/arcgisruntime/arcgis-android/100.14.1/
    Windows: %USERPROFILE%\.m2\repository\com\esri\arcgisruntime\arcgis-android\100.14.1\
4. Your full directory path should resemble the following:
    mac (2 files):
      /Users/[user-name]/.m2/repository/com/esri/arcgisruntime/arcgis-android/100.14.1/arcgis-android-100.14.1.aar
      /Users/[user-name]/.m2/repository/com/esri/arcgisruntime/arcgis-android/100.14.1/arcgis-android-100.14.1.pom
    Windows (2 files):
      %USERPROFILE%\.m2\repository\com\esri\arcgisruntime\arcgis-android\100.14.1\arcgis-android-100.14.1.aar
      %USERPROFILE%\.m2\repository\com\esri\arcgisruntime\arcgis-android\100.14.1\arcgis-android-100.14.1.pom
5. If you are working with an internet connection, you may skip this step and step 6 below.
   If you are working offline, deploy all dependencies listed in the arcgis runtime SDK's pom file to your local Maven repo. A list of these dependencies and URLs from where they may be downloaded is below.
   - gson 2.8.8: https://search.maven.org/artifact/com.google.code.gson/gson/2.8.8/jar
   - androidx.browser 1.3.0: https://maven.google.com/web/index.html?q=browser#androidx.browser:browser:1.3.0
   - androidx.localbroadcastmanager 1.0.0: https://maven.google.com/web/index.html?q=localbroadcastmanager#androidx.localbroadcastmanager:localbroadcastmanager:1.0.0
   - httpcore5 5.0.4: https://search.maven.org/artifact/org.apache.httpcomponents.core5/httpcore5/5.0.4/jar
   - httpcore5-h2 5.0.4: https://search.maven.org/artifact/org.apache.httpcomponents.core5/httpcore5-h2/5.0.4/jar
   - slf4j-api 1.7.32: https://search.maven.org/artifact/org.slf4j/slf4j-api/1.7.32/jar
   - commons-codec 1.15: https://search.maven.org/artifact/commons-codec/commons-codec/1.15/jar
   - conscrypt-openjdk-uber 2.2.1 https://search.maven.org/artifact/org.conscrypt/conscrypt-openjdk-uber/2.2.1/jar
   - spymemcached 2.12.3 https://search.maven.org/artifact/net.spy/spymemcached/2.12.3/jar
   - ehcache-api 3.4.0 https://search.maven.org/artifact/org.ehcache.modules/ehcache-api/3.4.0/jar

6. If you are working offline, use maven to install the dependencies downloaded in step 5 above.

Install the mvn maven tool.
    mac: brew install mvn
    windows: see https://maven.apache.org/guides/getting-started/windows-prerequisites.html

For androidx dependencies (browser and localbroadcastmanager), run

mvn install:install-file -Dfile=<relative path to aar> -DgroupId=<group ID> -DartifactId=<artifact id> -Dversion=<version> -Dpackaging=aar -DgeneratePom=true

For all other dependencies, run

mvn install:install-file -Dfile=<relative path to aar> -DgroupId=<group ID> -DartifactId=<artifact id> -Dversion=<version> -Dpackaging=jar -DgeneratePom=true

7. Your local Maven repo should be set, we will confirm this in the next step.

----------------------------
Getting Started
----------------------------
1. You should edit your build.gradle file to look at your local Maven repository. To do this, add the following to your project root
   build.gradle file:

allprojects {
    repositories {
        mavenLocal()
    }
}

2. In the app module build.gradle file, within the android block, add the following directive to set compatibility with
   Java 8 language features:

compileOptions {
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
}

3. Add the following dependencies to your app's build.gradle file.

dependencies {
	...
    implementation 'com.esri.arcgisruntime:arcgis-android:100.14.1'
    implementation 'com.google.code.gson:gson:2.8.8'
    implementation 'androidx.browser:browser:1.3.0'
    implementation 'androidx.localbroadcastmanager:localbroadcastmanager:1.0.0'
    implementation 'org.apache.httpcomponents.core5:httpcore5:5.0.4'
    implementation 'org.apache.httpcomponents.core5:httpcore5-h2:5.0.4'
    implementation 'org.slf4j:slf4j-api:1.7.32'
    implementation 'commons-codec:commons-codec:1.15'
    implementation 'org.conscrypt:conscrypt-openjdk-uber:2.2.1'
    implementation 'net.spy:spymemcached:2.12.3'
    implementation 'org.ehcache.modules:ehcache-api:3.4.0'

}
