# Kotlin Android Setup As of May 2017


#### Top Level Gradle File 
```sh
 // Top-level build file where you can add configuration options common to all sub-projects/modules.

buildscript {
    ext.kotlin_version = '1.1.1' // kotlin version
    ext.gradle_version = '2.3.1'
    repositories {
        jcenter()
    }
    dependencies {
        classpath "com.android.tools.build:gradle:$gradle_version"
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}

```

#### App Level Gradle File 
```sh
 apply plugin: 'com.android.application'
apply plugin: 'kotlin-android'  //Plugin for kotlin coding in android
apply plugin: 'kotlin-android-extensions' //Plugin for kotlin coding in android
apply plugin: 'kotlin-kapt' // kotlin Anotation processing plugin

android {
    compileSdkVersion 25
    buildToolsVersion "25.0.2"
    defaultConfig {
        applicationId "com.okhttptest.codbase.okhttptest"
        minSdkVersion 19
        targetSdkVersion 25
        versionCode 1
        versionName "1.0"
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])

    compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
    compile "org.jetbrains.kotlin:kotlin-reflect:$kotlin_version"
    kapt "com.android.databinding:compiler:$gradle_version"
}


// From Kotlin 1.0.4 the following is no longer required
//kapt {
//    generateStubs = true
//}

```
