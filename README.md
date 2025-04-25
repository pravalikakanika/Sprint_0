![image](https://github.com/user-attachments/assets/caaa1b47-4765-4040-89d5-e799dfe86bed)



| Author        | Date       | Version | Review Level   | Reviewer Name        |
|---------------|------------|---------|----------------|----------------------|
| pravalika Kanikarapu  | April 20   | v1.1    | Pre-Reviewer   | Priyanshu            |
| pravalika Kanikarapu  | April 24   | v2.1    | L0             | Khushi Malothra      |
| pravalika Kanikarapu  |            |         | L1             | Rishabh Sharma       |
| pravalika Kanikarapu  |            |         | L2             | piyush Upadhyay      |





# Table of Contents 

1. [Introduction](#Introduction)
2. [What is Maven?](#what-is-maven)
3. [Why Use Maven?](#why-use-maven)
4. [ Purpose of Maven](#purpose-of-maven)
5. [ Key Features of Maven](#key-features-of-maven)
6. [ Commonly Used Plugins](#commonly-used-plugins)
7. [ Repositories in Maven](#repositories-in-maven)
8. [Conclusion](#Conclusion)
9. [ Contact Information](#contact-information)
10. [ Reference](#reference)


# Introduction
This document is a comprehensive guide to Apache Maven, covering its role in automating Java project builds, managing dependencies via pom.xml, supporting a structured build lifecycle with plugins, and using local, central, and remote repositories for dependency resolution.




# What is Maven 

Maven is a build automation and dependency management tool used primarily for Java projects. It was developed by the Apache Software Foundation.

Think of Maven as a project manager that:

- Automates compilation, packaging, testing, and deployment.

- Handles dependencies (like libraries) automatically.

- Ensures consistency across builds.



# Why Use Maven?


Maven offers a powerful and standardized way to manage Java projects. Here's why it's widely adopted:

| Reason                           | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
|  **Dependency Management**       | Automatically downloads required libraries from central repositories.       |
|  **Standardization**            | Enforces a consistent project structure and build lifecycle.               |
|  **Build Simplification**       | Handles compilation, packaging, testing, and deployment with a single command. |
|  **Integration with IDEs**      | Works seamlessly with IntelliJ IDEA, Eclipse, NetBeans, and others.        |
|  **Plugins & Extensibility**    | Supports numerous plugins for code quality checks, Docker, deployment, etc. |
|  **Community & Central Repository** | Massive ecosystem with a central repository hosting thousands of libraries. |







#  Purpose of Maven

Maven was designed to streamline and standardize the Java project lifecycle. Here's what it brings to the table:

| Purpose                         | Description                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
|  **Simplify Build Process**    | Automates tasks like compiling code, running tests, and packaging into JAR/WAR files. |
|  **Standardize Project Structure** | Enforces a consistent directory layout and lifecycle for all projects.         |
|  **Handle Dependencies Automatically** | Downloads and manages required libraries from central repositories.          |
|  **Enhance Team Collaboration** | Ensures consistent builds and environments across different machines.        |
|  **Generate Reports**          | Supports generation of test reports, project documentation, and more.        |
|  **Extend with Plugins**        | Add functionality like code quality checks, Docker builds, or custom deployments. |




#  Key Features of Maven



This project is built using Maven, and the configuration is centralized in the `pom.xml` file. Maven helps manage the project's dependencies, build process, and other configuration settings.

## **1. Centralized `pom.xml` File**
The `pom.xml` file is the cornerstone of Maven’s configuration and project structure. It defines the entire configuration of a Maven project, including dependencies, build settings, plugin definitions, project versioning, and more.

-  Basic Structure of `pom.xml`

   - The root element is `<project>`, which contains all the project configurations.

   - Inside the `<project>` element, you'll define:

       - **`modelVersion`**: Specifies the version of the POM model.

       - **`groupId`**: Defines the unique group or organization the project belongs to.

       - **`artifactId`**: The unique identifier for the project within the group.

       - **`version`**: The version of the project.

       - **`packaging`**: Defines the artifact type (e.g., `jar`, `war`).

       - **`dependencies`**: List of all external libraries your project depends on.

       - **`build`**: Defines build configurations such as plugins, resources, and directories.
**Example:**

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>my-project</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>5.2.9.RELEASE</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <!-- Plugins go here -->
        </plugins>
    </build>
</project>
 ```


## **2. Dependency Management**

Maven simplifies dependency management by automating the downloading, versioning, and resolution of third-party libraries. Dependencies are specified in the pom.xml file.

 - **How Dependency Management Works:**

    -  Dependencies are listed under the <dependencies> section in the pom.xml file.

    -  Maven retrieves these dependencies from remote repositories like Maven Central or custom repositories you define.

    -  It resolves conflicts between different versions of the same dependency using a strategy called "nearest definition" or "first declaration wins."

**Example:**
```xml
<dependencies>
    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
        <version>3.11</version>
    </dependency>
</dependencies>
```

- **Version Ranges:** Maven supports version ranges to specify flexible versions for dependencies.
```xml
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>[3.0, 3.1]</version> <!-- Will match any version between 3.0 and 3.1 -->
</dependency>
```

## **3.Introduction to the Build Lifecycle**

## Build Lifecycle Basics

Maven is based around the central concept of a build lifecycle. What this means is that the process for building and distributing a particular artifact (project) is clearly defined.

For the person building a project, this means that it is only necessary to learn a small set of commands to build any Maven project, and the POM will ensure they get the results they desired.

There are three built-in build lifecycles: default, clean and site. The default lifecycle handles your project deployment, the clean lifecycle handles project cleaning, while the site lifecycle handles the creation of your project's web site.

## A Build Lifecycle is Made Up of Phases

![image](https://github.com/user-attachments/assets/49591568-c9cf-411a-8eed-fcbd178c209e)






Each of these build lifecycles is defined by a different list of build phases, wherein a build phase represents a stage in the lifecycle.

For example, the default lifecycle comprises of the following phases (for a complete list of the lifecycle phases, refer to the Lifecycle Reference):

**Validate Phase**

Ensures that the project is correctly configured and all necessary information is available.

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-enforcer-plugin</artifactId>
    <version>3.0.0</version>
    <executions>
        <execution>
            <id>enforce</id>
            <phase>validate</phase>
            <goals>
                <goal>enforce</goal>
            </goals>
            <configuration>
                <rules>
                    <requireMavenVersion>
                        <version>[3.6,)</version>
                    </requireMavenVersion>
                </rules>
            </configuration>
        </execution>
    </executions>
</plugin>
```

**Compile Phase**

Compiles the Java source code. It also compiles TypeScript/ES6 to JavaScript or other build processes.
```xml

<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.10.1</version>
    <configuration>
        <source>11</source>
        <target>11</target>
    </configuration>
</plugin>
```

**Test Phase**

Runs unit tests using frameworks like JUnit or Mockito.
```xml

<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>3.0.0-M7</version>
</plugin>
```

**Package Phase**

Packages the compiled code into a deployable format, such as a .jar or .zip. Example: For AEM, this is typically a .zip package containing the content and configuration.
```xml

<plugin>
    <groupId>com.day.jcr.vault</groupId>
    <artifactId>content-package-maven-plugin</artifactId>
    <version>1.0.2</version>
    <executions>
        <execution>
            <id>package</id>
            <goals>
                <goal>install</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

**Install Phase**

Installs the package into the local Maven repository, making it available to other projects.
```xml
mvn install
```

**Deploy Phase**

Deploys the package to a specified environment, typically using the content-package-maven-plugin for AEM.
```xml

<plugin>
    <groupId>com.day.jcr.vault</groupId>
    <artifactId>content-package-maven-plugin</artifactId>
    <version>1.0.2</version>
    <executions>
        <execution>
            <id>deploy</id>
            <phase>deploy</phase>
            <goals>
                <goal>install</goal>
            </goals>
            <configuration>
                <vaultCliPath>${vault.cli.path}</vaultCliPath>
                <vaultCliUser>${vault.cli.user}</vaultCliUser>
                <vaultCliPassword>${vault.cli.password}</vaultCliPassword>
            </configuration>
        </execution>
    </executions>
</plugin>
```

## **4. Standard Directory Structure**



- `src/main/java/`: Application source code
- `src/test/java/`: Test classes (unit/integration)
- `target/`: Output folder (compiled classes, JARs, etc.)
- `pom.xml`: Project Object Model file (Maven config)


### Explanation

- **`src/main/java/`**: This is where your main application source code lives.
- **`src/test/java/`**: Contains your test code (unit/integration tests).
- **`target/`**: This is the output directory where Maven compiles classes and builds packaged artifacts (like `.jar` files).
- **`pom.xml`**: The core Maven configuration file. It defines the project structure, dependencies, plugins, and build settings.





## **5. Plugin Support**

Maven supports plugins to extend its functionality, such as compiling source code, packaging artifacts, and running tests. Plugins can be configured in the `pom.xml` file to perform specific tasks during the build process.

# Commonly Used Plugins

- **Maven Compiler Plugin**: Compiles your source code.
- **Maven Surefire Plugin**: Runs unit tests.
- **Maven Jar Plugin**: Packages your project into a JAR file.

### Example Plugin Configuration in `pom.xml`

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.8.1</version>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
            </configuration>
        </plugin>

        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>2.22.2</version>
        </plugin>

        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jar-plugin</artifactId>
            <version>3.2.0</version>
        </plugin>
    </plugins>
</build>
```


#   Repositories in Maven

Repositories are locations where Maven stores and retrieves project dependencies.

## **Types of Maven Repositories**

  - Local Repository

  - Central Repository

  - Remote (Custom) Repository



##  Local Repository

### What is it?

A local repository is a cache of downloaded dependencies stored on your machine. It helps avoid downloading the same dependency repeatedly, improving efficiency during builds.

### Default Location

- **Unix/macOS**: `~/.m2/repository`
- **Windows**: `C:\Users\<user>\.m2\repository`

- **Example Structure:**
 ```bash
~/.m2/repository/
    org/
        apache/
            commons/
                commons-lang3/
                    3.11/
                        commons-lang3-3.11.jar
                        commons-lang3-3.11.pom
 ```
- **How Maven Uses the Local Repository:** When you build a project and request a dependency (e.g., commons-lang3), Maven first checks the local repository. If the artifact is already there (i.e., cached), it will be used directly. If not, Maven will download it from the remote repositories (such as Maven Central) and store it in the local repository for future use.

- **Customizing Local Repository Location:** You can change the location of the local repository by specifying the <localRepository> tag in the settings.xml file located in the ~/.m2 folder:
```xml
<settings>
    <localRepository>/path/to/custom/repository</localRepository>
</settings>
```

##  Central Repository

**What is the Central Repository?**

The central repository (also known as Maven Central) is the default remote repository that Maven uses to retrieve dependencies and plugins. It is hosted by the Apache Maven community and contains millions of widely-used Java libraries and frameworks.

- **URL of Maven Central Repository:**
```bash
https://repo.maven.apache.org/maven2
```

- **Why is it Important?**

Maven Central is the default source for resolving dependencies, and it contains most of the popular open-source libraries in Java. You don’t need to configure it explicitly in your pom.xml because Maven automatically tries to download dependencies from it if they are not available in the local repository.

- **Example of a Dependency Using Maven Central:**
```xml
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.11</version>
</dependency>
```
- **Dependency Resolution Flow:**

Maven looks for dependencies in the local repository.

If the dependency is not found locally, Maven checks Maven Central.

If it is not available in Maven Central, Maven looks for it in other remote repositories you may have configured.


##  Remote (Custom) Repositories

**What is a Remote Repository?**

A remote repository is any repository that is not on your local machine but can be accessed over the network. Maven uses remote repositories to download dependencies that are not available in the local repository. These repositories can be hosted by third-party services like Nexus, Artifactory, GitHub Packages, or custom repositories hosted internally.

**How to Use Remote Repositories:**

- **Default Behavior:**
 By default, Maven checks the remote repositories in the order they are defined in the repositories section of your pom.xml file or settings.xml.

- **Multiple Remote Repositories:**
 You can configure multiple remote repositories in your pom.xml file. Maven will look for dependencies in the order they are listed in the repositories section.

**Example with multiple repositories**:
```xml
<repositories>
    <repository>
        <id>central</id>
        <url>https://repo.maven.apache.org/maven2</url>
    </repository>
    <repository>
        <id>internal-repo</id>
        <url>https://internal.repo.com/maven</url>
    </repository>
</repositories>
```

#  How Maven Works 

You run a command: mvn clean install

Maven reads the pom.xml

It checks the local repository for dependencies

If missing, it fetches from a remote repository

It compiles, tests, packages, and installs the artifact

It outputs the final result (e.g., .jar or .war) into the target/ directory




# Conclusion
Maven is not just a build tool — it’s a project management framework that empowers developers to streamline their workflows, reduce manual tasks, and produce consistent, high-quality builds. By automating tasks such as compiling code, managing dependencies, running tests, and packaging artifacts, Maven streamlines the development process and ensures consistent builds across different environments.


#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|

#  Reference

| **Link**                                                                 | **Description**                              |
|--------------------------------------------------------------------------|----------------------------------------------|
| [https://maven.apache.org/install.html](https://maven.apache.org/install.html) | Documentation followed for Maven installation |
