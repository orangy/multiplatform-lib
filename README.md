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

# Points of interest

* Extra files in [gradle](gradle) folder:
** node-js.gradle – installs `node` and sets up `node_modules` directory
** pom.gradle – configures `pom.xml` for publishing
** publish.gradle – creates publishing tasks
** test-mocha-js.gradle – creates tasks for running JS tests with Mocha


