# elf4j-jul

The [java.util.logging](https://docs.oracle.com/javase/8/docs/technotes/guides/logging/overview.html) (JUL) service
provider binding for the Easy Logging Facade for Java ([ELF4J](https://github.com/elf4j/elf4j-api)) SPI

## User story

As a service provider of the Easy Logging Facade for Java (ELF4J) SPI, I want to bind the logging capabilities of
java.util.logging to the ELF4J client application via
the [Java Service Provider Interfaces (SPI)](https://docs.oracle.com/javase/tutorial/sound/SPI-intro.html) mechanism, so
that any application using the ELF4J API for logging can opt to use the java.util.logging framework at deployment time
without code change.

## Prerequisite

- Java 8+
- [ELF4J](https://github.com/elf4j/elf4j-api) 5.0.0+

## Get it...

[![Maven Central](https://img.shields.io/maven-central/v/io.github.elf4j/elf4j-jul.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22io.github.elf4j%22%20AND%20a:%22elf4j-jul%22)

## Use it...

If you are using the [ELF4J API](https://github.com/elf4j/elf4j-api#the-client-api) for logging, and wish to select or
change to use java.util.logging as the run-time implementation, then simply pack this binding JAR in the classpath when
the application deploys. No code change needed. At compile time, the client code is unaware of this run-time logging
service provider. Because of the ELF4J API, opting for java.util.logging as the logging implementation is a
deployment-time decision.

The
usual [java.util.logging configuration](https://docs.oracle.com/javase/8/docs/technotes/guides/logging/overview.html#a1.8)
applies.

With Maven, an end-user application would use this provider as a dependency of the `runtime` scope:

```
        <dependency>
            <groupId>io.github.elf4j</groupId>
            <artifactId>elf4j-jul</artifactId>
            <version>grab the latest from maven central</version>
            <scope>runtime</scope>
        </dependency>
```

Note: A library, API, or server/container codebase would use the `test` or `provided` scope; or just use the ELF4J API -
without any SPI provider like this, at all. Only one logging provider should be loaded and working at run-time; the
facilitating codebase should leave the provider choice to the end-user application.

