# H3-Java

[![Build Status](https://travis-ci.com/uber/h3-java.svg?branch=master)](https://travis-ci.com/uber/h3-java)
[![Build status](https://ci.appveyor.com/api/projects/status/pjp4m666p9c24jyd/branch/master?svg=true)](https://ci.appveyor.com/project/Uber/h3-java/branch/master)
[![Coverage Status](https://coveralls.io/repos/github/uber/h3-java/badge.svg?branch=master)](https://coveralls.io/github/uber/h3-java?branch=master)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.uber/h3/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.uber/h3)
[![H3 Version](https://img.shields.io/badge/h3-v3.4.2-blue.svg)](https://github.com/uber/h3/releases/tag/v3.4.2)

This library provides Java bindings for the [H3 Core Library](https://github.com/uber/h3). For API reference, please see the [H3 Documentation](https://uber.github.io/h3/).

# Usage

Add it to your pom.xml:

```xml
<dependency>
    <groupId>com.uber</groupId>
    <artifactId>h3</artifactId>
    <version>3.4.0</version>
</dependency>
```

Or, using Gradle:

```gradle
compile("com.uber:h3:3.4.0")
```

Encode a location into a hexagon address:

```java
H3Core h3 = H3Core.newInstance();

double lat = 37.775938728915946;
double lng = -122.41795063018799;
int res = 9;

String hexAddr = h3.geoToH3Address(lat, lng, res);
```

Decode a hexagon address into coordinates:

```java
List<GeoCoord> geoCoords = h3.h3ToGeoBoundary(hexAddr);
```

## Supported Operating Systems

H3-Java provides bindings to the H3 library, which is written in C. The built artifact supports the following:

| Operating System | Architectures
| ---------------- | -------------
| Linux            | x64, x86, ARM64, ARMv5, ARMv7, MIPS, MIPSEL, PPC64LE, s390x
| Windows          | x64, x86
| Darwin (Mac OSX) | x64
| Android          | ARM, ARM64

You may be able to build H3-Java locally if you need to use an operating system or architecture not listed above.

# Development

Building the library requires a JDK, Maven, CMake, and a C compiler. To install to your local Maven cache, run:

```sh
mvn install
```

To build the library, run:

```sh
mvn package
```

Additional information on how the build process works is available in the [build process documentaiton](docs/library-build.md).

## Javadocs

To build Javadocs documentation:

```sh
mvn site
```

Then open the file `target/site/apidocs/index.html`.

## Benchmarking

To run benchmarks, either execute them from IntelliJ or run the following from shell: (Replace the class name as needed)

```sh
mvn exec:exec -Dexec.executable="java" -Dexec.args="-classpath %classpath com.uber.h3core.benchmarking.H3CoreBenchmark" -Dexec.classpathScope="test"
```

## Contributing

Pull requests and Github issues are welcome. Please see our [contributing guide](./CONTRIBUTING.md) for more information.

Before we can merge your changes, you must agree to the [Uber Contributor License Agreement](http://cla-assistant.io/uber/h3-java).

## Legal and Licensing

H3-Java is licensed under the [Apache 2.0 License](./LICENSE).

DGGRID
Copyright (c) 2015 Southern Oregon University
