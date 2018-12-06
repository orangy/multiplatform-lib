# Kotlin Multiplatform Library 

This project contains a no-op multiplatform library targeting JVM, JS and Native, along with tests and publishing
set up. It has a common module with `expect` declarations and common tests, platform-specific `actual` implementations 
and tests and corresponding Gradle build files.  

You can use it as a reference for how one can do some tasks that are not ready out of the box with Kotlin 
Multiplatform Technology, namely:

* Run JavaScript tests with Mocha
* Publish multiplatform libraries to Bintray

Not implemented yet:

* Integrate with dokka to produce JavaDoc artifacts for JVM
* Publish sources jar

# Using in your library project

Add dependencies and repositories to the buildscript section:

```groovy
buildscript {
    repositories {
        mavenCentral()
        jcenter()
        maven { url "https://dl.bintray.com/jetbrains/kotlin-native-dependencies" }
    }
    dependencies {
        classpath "com.moowork.gradle:gradle-node-plugin:$gradle_node_version"
        classpath "com.jfrog.bintray.gradle:gradle-bintray-plugin:$bintray_plugin_version"
    }
}
```

Apply `maven-publish` plugin

```groovy
apply plugin: 'maven-publish'
```

Copy these files from `gradle` directory of this project to your project

  * node-js.gradle – installs `node` and sets up `node_modules` directory
  * pom.gradle – configures `pom.xml` for publishing
  * publish.gradle – creates publishing tasks
  * test-mocha-js.gradle – creates tasks for running JS tests with Mocha


Import these files into your Gradle file *after* the `kotlin` section with targets and source sets:

```groovy
apply from: rootProject.file("gradle/publish.gradle")
apply from: rootProject.file('gradle/node-js.gradle')
apply from: rootProject.file('gradle/test-mocha-js.gradle')
```

Enable Gradle Metadata (experimental feature) in `settings.gradle`:

```groovy
enableFeaturePreview('GRADLE_METADATA')
```

Consult `gradle.properties` file in this project for what you need to configure for testing and publishing.
Pay special attention to a section about `local.properties` at the end of it. 