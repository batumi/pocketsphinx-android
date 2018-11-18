About
=====

This project is a wrapper for Pocketsphinx for Android providing
high-level interface for recognizing the microphone input.

### Install

You can manually download the `.aar` and include it in your project from this url: https://bintray.com/fielddb/maven/edu.cmu.pocketsphinx

To install it in your project via maven, add the maven repository to your Android build.gradle:

```groovy
repositories {
    maven {
        url  "https://dl.bintray.com/fielddb/maven"
    }
}
```

Build
=====

You will need SWIG, Gradle and Android NDK to build a distributable
archive of pocketsphinx for Android. It is better to use recent versions.

You need to checkout sphinxbase, pocketsphinx and pocketsphinx-android
and put them in the same folder.

```
Root folder
 \_pocketsphinx
 \_sphinxbase
 \_pocketsphinx-android
```

Older versions might be incompatible with the latest pocketsphinx-android,
so you need to make sure you are using latest versions. You can use
the following command to checkout from repository:

```
git clone https://github.com/cmusphinx/sphinxbase
git clone https://github.com/cmusphinx/pocketsphinx
git clone https://github.com/cmusphinx/pocketsphinx-android
export POCKETSPHINX_HOME=`pwd`/pocketsphinx
export SPINXBASE_HOME=`pwd`/sphinxbase
```

After checkout you need to update the file 'local.properties' in the
project root and define the following properties:

  * sdk.dir - path to Android SDK
  * ndk.dir - path to Android NDK

For example:

```
sdk.dir=/Users/User/Library/Android/sdk
ndk.dir=/Users/User/Library/Android/sdk/ndk-bundle
```

After everything is set, run `./gradlew build`. It will create
pocketsphinx-android-5prealpha-release.aar and
pocketsphinx-android-5prealpha-debug.aar in build/output.

Using the library
=================

Library is distributed as android archive AAR. You can add it to your project
as usual with Android Studio or directly in gradle

    dependencies {
        compile (name:'pocketsphinx-android-debug', ext:'aar')
    }

    repositories {
        flatDir {
                dirs 'libs'
        }
    }

For further information on usage please see the wiki page:

http://cmusphinx.sourceforge.net/wiki/tutorialandroid




### Release

To publish a new release of this library, edit the `version` in `build.gradle' and set the ENV variables for `BINTRAY_USER` and `BINTRAY_API_KEY`

```bash
./gradlew tasks
./gradlew install
./gradlew clean
./gradlew build
./gradlew assembleRelease
ls -alt build/outputs/aar/
./gradlew generateSourcesJar
./gradlew generateJavadocs
./gradlew generateJavadocsJar
./gradlew bintrayUpload
```


[travis-url]: https://travis-ci.org/batumi/pocketsphinx-android
[travis-image]: https://travis-ci.org/batumi/pocketsphinx-android.svg?branch=master
