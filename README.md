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
