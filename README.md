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
    
# POM.XML 

for more about the POM.XML refer this link

[POM.XML](https://github.com/Cloud-NInja-snaatak/Documentation/blob/shrey_scrum28/commonstack/applications/java/pom/documentation.md)


## **2. Dependency Management**

Maven simplifies dependency management by automating the downloading, versioning, and resolution of third-party libraries. Dependencies are specified in the pom.xml file.

 - **How Dependency Management Works:**

    -  Dependencies are listed under the <dependencies> section in the pom.xml file.

    -  Maven retrieves these dependencies from remote repositories like Maven Central or custom repositories you define.

    -  It resolves conflicts between different versions of the same dependency using a strategy called "nearest definition" or "first declaration wins."



- **Version Ranges:** Maven supports version ranges to specify flexible versions for dependencies.

## **3.Introduction to the Build Lifecycle**


Maven is based around the central concept of a build lifecycle. What this means is that the process for building and distributing a particular artifact (project) is clearly defined.

For the person building a project, this means that it is only necessary to learn a small set of commands to build any Maven project, and the POM will ensure they get the results they desired.


## A Build Lifecycle is Made Up of Phases

![image](https://github.com/user-attachments/assets/82e2691c-5832-46c1-811b-e123ddb707b0)

 - **Validate:** This step validates if the project structure is correct. For example – It checks if all the dependencies have been downloaded and are available in the local repository.
- **Compile:** It compiles the source code, converts the .java files to .class, and stores the classes in the target/classes folder.
- **Test:** It runs unit tests for the project.
- **Package:** This step packages the compiled code in a distributable format like JAR or WAR.
- **Integration test:** It runs the integration tests for the project.
- **Verify:** This step runs checks to verify that the project is valid and meets the quality standards.
- **Install:** This step installs the packaged code to the local Maven repository.
- **Deploy:** It copies the packaged code to the remote repository for sharing it with other developers.

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




#   Repositories in Maven

Repositories are locations where Maven stores and retrieves project dependencies.

## **Types of Maven Repositories**

  - Local Repository

  - Central Repository

  - Remote (Custom) Repository



##  Local Repository

### What is it?

A local repository is a cache of downloaded dependencies stored on your machine. It helps avoid downloading the same dependency repeatedly, improving efficiency during builds.


- **How Maven Uses the Local Repository:** When you build a project and request a dependency (e.g., commons-lang3), Maven first checks the local repository. If the artifact is already there (i.e., cached), it will be used directly. If not, Maven will download it from the remote repositories (such as Maven Central) and store it in the local repository for future use.



##  Central Repository

**What is the Central Repository?**

The central repository (also known as Maven Central) is the default remote repository that Maven uses to retrieve dependencies and plugins. It is hosted by the Apache Maven community and contains millions of widely-used Java libraries and frameworks.


- **Why is it Important?**

Maven Central is the default source for resolving dependencies, and it contains most of the popular open-source libraries in Java. You don’t need to configure it explicitly in your pom.xml because Maven automatically tries to download dependencies from it if they are not available in the local repository.



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


#  How Maven Works 

You run a command: mvn clean install

![image](https://github.com/user-attachments/assets/7008cc31-a518-401f-8fda-d6c4d4f8c110)


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
| [Maven Build Life Cycle](https://maven.apache.org/install.html) | Documentation followed for Maven Build Life Cycle |
