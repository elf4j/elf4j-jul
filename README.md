[![Maven Central](https://img.shields.io/maven-central/v/io.github.elf4j/elf4j-jul.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22io.github.elf4j%22%20AND%20a:%22elf4j-jul%22)

# elf4j-jul

The [java.util.logging](https://docs.oracle.com/javase/8/docs/technotes/guides/logging/overview.html) (JUL) service
provider binding for the Easy Logging Facade for Java ([ELF4J](https://github.com/elf4j/elf4j)) SPI

## User Story

As a service provider of the [ELF4J](https://github.com/elf4j/elf4j) SPI, I want to bind the logging capabilities of
java.util.logging to the ELF4J client application via the
Java [Service Provider Framework](https://docs.oracle.com/javase/8/docs/api/java/util/ServiceLoader.html), so that any
application using the ELF4J API for logging can opt to use java.util.logging at deployment time without code change.

## Prerequisite

Java 8+

## Get It...

[![Maven Central](https://img.shields.io/maven-central/v/io.github.elf4j/elf4j-jul.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22io.github.elf4j%22%20AND%20a:%22elf4j-jul%22)

## Use It...

If you are using the [ELF4J API](https://github.com/elf4j/elf4j) for logging, and wish to select or change to use
java.util.logging as the run-time implementation, then simply pack this binding JAR in the classpath when the
application deploys. No code change needed. At compile time, the client code is unaware of this run-time logging service
provider. With the ELF4J facade, opting for java.util.logging as the logging implementation is a deployment-time
decision.

The
usual [java.util.logging configuration](https://docs.oracle.com/javase/8/docs/technotes/guides/logging/overview.html#a1.8)
applies.

With Maven, in addition to use compile-scope on the [ELF4J API](https://github.com/elf4j/elf4j) dependency, an end-user
application would use runtime-scope for this provider as a dependency:

```html

<dependency>
    <groupId>io.github.elf4j</groupId>
    <artifactId>elf4j</artifactId>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>io.github.elf4j</groupId>
    <artifactId>elf4j-jul</artifactId>
    <scope>runtime</scope>
</dependency>
```

Note: Only one logging provider such as this should be in effect at run-time. If multiple providers end up in the final
build of an application, somehow, then the `elf4j.logger.factory.fqcn` system property will have to be used to select
the desired provider.
