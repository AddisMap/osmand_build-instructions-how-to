# osmand_build-instructions-how-to

This is for beginners ...

Source:
https://code.google.com/archive/p/osmand/wikis/GradleCommandLineBuildEnvironment.wiki

What didn't work:
I expected ` git clone https://github.com/osmandapp/Osmand.git` would suffice to build the project, but files where missing, because that's not the whole project.

----

What works (tested with `4fe4e42c9264908c8d16100553d1a168bc992dce` on 5th May 2017):
```mkdir osmandapp
cd osmandapp
```
--------------------
best way is to install "repo" and do ...
```repo init -u https://github.com/osmandapp/OsmAnd-manifest.git -m android_build.xml
repo sync -d
```
------------
alternatively... 
```git clone https://github.com/osmandapp/OsmAnd-resources.git
git clone https://github.com/osmandapp/Osmand.git
git clone https://github.com/osmandapp/OsmAnd-core.git
git clone https://github.com/osmandapp/osmandapp.github.io
mv Osmand/ android
mv OsmAnd-resources/ resources
mv OsmAnd-core/ core-legacy
mv osmandapp.github.io/ help
```
------------
```cd android/OsmAnd
../gradlew --refresh-dependencies clean assembleFullLegacyFatDebug
```
in AS:

install android sdk and tools version 23
Tools -> Android -> Sdk Manager
Android Platform "Android 6 Marshmallow"
Sdk Tools -> check "Show Package Details" -> 23.0.x

Android Studio
Import project ...

always click update

Add the following line (to find correct gradle version) left pane under: Project (dropdown android) -> Gradle Scripts click build-gradle (Project: Osmand)

------------------------------
```xml
buildscript {
    repositories {
        mavenCentral()
        jcenter() // add this
    }
...
```
------------------------------

it should compile now!
