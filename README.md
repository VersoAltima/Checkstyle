# Checkstyle

This is the checkstyle used by Altima, based on Google Java styleguide conventions. This is an example Maven configuration:

```xml
<plugin>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>2.17</version>
    <dependencies>
        <dependency>
            <groupId>com.puppycrawl.tools</groupId>
            <artifactId>checkstyle</artifactId>
            <version>7.2</version>
        </dependency>
    </dependencies>
    <configuration>
        <configLocation>https://raw.githubusercontent.com/Altima-Zagreb/Checkstyle/master/checkstyle.xml</configLocation>
        <violationSeverity>warning</violationSeverity>
        <logViolationsToConsole>true</logViolationsToConsole>
        <failOnViolation>true</failOnViolation>
        <failsOnError>true</failsOnError>
        <includeTestSourceDirectory>true</includeTestSourceDirectory>
    </configuration>
    <executions>
        <execution>
            <id>checkstyle</id>
            <goals>
                <goal>check</goal>
            </goals>
            <phase>validate</phase>
        </execution>
    </executions>
</plugin>
```
You can check your code by executing:

```
mvn checkstyle:check
```

You can suppress specific files-checks pairs:

1) Extend checkstyle plugin <configuration> by adding:

```xml
	<!-- Suppress specific file for specific checks -->
    <suppressionsLocation>checkstyle-suppressions.xml</suppressionsLocation>
    <suppressionsFileExpression>checkstyle.suppressions.file</suppressionsFileExpression>
```

2) Create checkstyle-suppressions.xml file with defined suppressions:

```xml
<?xml version="1.0"?>
<!DOCTYPE suppressions PUBLIC
        "-//Puppy Crawl//DTD Suppressions 1.1//EN"
        "http://www.puppycrawl.com/dtds/suppressions_1_1.dtd">

<suppressions>

    <!-- AbbreviationAsWordInName -->
    <suppress checks="AbbreviationAsWordInName" files="SampleClass.java"/>

    <!-- MemberName and ParameterName -->
    <suppress checks="MemberName|ParameterName" files="SampleClass.java"/>

</suppressions>
```