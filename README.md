# Maven Wrapper

The Maven Wrapper is an easy way to ensure a user of your Maven build has everything necessary run your Maven build. Why might this be necessary? Maven to date has been very stable for users, is available on most systems or is easy to procure: but with many of the recent changes in Maven it will be easier for users to have a fully encapsulated build setup provided by the project. With the Maven Wrapper this is very easy to do and it's a great idea borrowed from Gradle.

The easiest way to setup the Maven Wrapper for your project is to use the [Takari Maven Plugin][1] with its provided `wrapper` goal. To add all the necessary Maven Wrapper files to your project execute the following command:

```
mvn -N io.takari:maven:wrapper
```

Normally you instruct user to run the `mvn` command like the following:

```
$ mvn clean install
```

But now, with a Maven Wrapper setup, you can instruct users to run wrapper scripts:

```
$ ./mvnw clean install
```

or

```
$ ./mvnw.cmd clean install
```

A normal Maven build will be executed with the one important change that if the user doesn't have the necessary version of Maven specified in `.mvn/wrapper/maven-wrapper.properties` it will be downloaded for the user first.

## Using a Different Version of Maven

To switch the version of Maven used to build a project you can initialize it using 

```
mvn -N io.takari:maven:wrapper -Dmaven=3.3.3
```

which works for any version except snapshots. Once you have a wrapper you can change its version by setting the `distributionUrl` in `.mvn/wrapper/maven-wrapper.properties`, e.g.

```
distributionUrl=https://repo1.maven.org/maven2/org/apache/maven/apache-maven/3.2.1/apache-maven-3.2.1-bin.zip
```

[1]: https://github.com/takari/takari-maven-plugin
