```
java -version
openjdk version "1.8.0_202-release"
OpenJDK Runtime Environment (build 1.8.0_202-release-1483-b49-5587405)
OpenJDK 64-Bit Server VM (build 25.202-b49-5587405, mixed mode)

javac -version
javac 1.8.0_202-release

mvn -version
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: /usr/local/Cellar/maven/3.6.3_1/libexec
Java version: 1.8.0_202-release, vendor: JetBrains s.r.o, runtime: /Applications/Android Studio.app/Contents/jre/jdk/Contents/Home/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.15.4", arch: "x86_64", family: "mac"
```

What is Groovy used for in Spring.
What is a jar file used for.

Maven course

Postgres
Docker

Springboot

Spring supports both Maven and Gradle for dependency management.

Some terms have specific meaning in Springboot.

POJO (Plain Old Java Object) - Objects that have state as well as behavior (i.e. both properties and methods)
JavaBeans - Has only getters and setters (i.e. only properties)
Spring Beans (aka Beans) - POJOs that have been set up in application context
DTO - Beans (usually JavaBeans) used to move state between layers of application.

Inversion of Control (IOC) - IOC container provides a way of dependency injection.
Application Context - Wrapper for BeanFactory that serves Beans to the runtime of the application.

Embedded Tomcat container
Automatic servlet mappings
Hibernate/JPA dialect
