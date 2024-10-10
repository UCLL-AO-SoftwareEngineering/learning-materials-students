# Set up your development environment

## 1. Acceptance Criteria

At the end of this task you should be able to code, build and run Java projects.

## 2. Implementation Details

1. Install [Java JDK 21](https://docs.aws.amazon.com/corretto/latest/corretto-21-ug/downloads-list.html)
    * Running `java -version` should return output similar to:

        ```console
        openjdk version "21.0.2" 2024-01-16 LTS
        OpenJDK Runtime Environment Corretto-21.0.2.13.1 (build 21.0.2+13-LTS)
        OpenJDK 64-Bit Server VM Corretto-21.0.2.13.1 (build 21.0.2+13-LTS, mixed mode, sharing)
        ```
    * If you get wrong output then make sure that your PATH and JAVA_HOME variables are correctly set, if this is not the case, [configure them manually](https://www.baeldung.com/java-home-on-windows-mac-os-x-linux)
1. Install [Apache Maven](https://maven.apache.org/install.html)
    * Running `mvn -v` should return output similar to:
    
        ```console
        Apache Maven 3.9.9 (8e8579a9e76f7d015ee5ec7bfcdc97d260186937)
        Maven home: C:\Users\roel\scoop\apps\maven\current
        Java version: 21.0.2, vendor: Amazon.com Inc., runtime: C:\Program Files\Amazon Corretto\jdk21.0.2_13
        Default locale: en_US, platform encoding: UTF-8
        OS name: "windows 11", version: "10.0", arch: "amd64", family: "windows"
        ```

1. Install and configure an IDE of your choice
    * A good option is VS Code, you can check [this link](https://code.visualstudio.com/docs/java/java-spring-boot) for a recommended extension setup
    * Another good option is IntelliJ IDEA
        * If you want to work with IntelliJ, make sure that you use the _Ultimate Edition_, a license is free for students
        * Only the Ultimate Edition has built-in Spring tooling, the free community edition only has built-in Java tooling