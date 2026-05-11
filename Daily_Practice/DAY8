Maven Basics (One-Page Notes)
What is Maven?

Apache Maven is a build automation and project management tool mainly used for Java projects.

It helps developers:

Manage dependencies (libraries)
Compile code
Run tests
Package applications
Maintain project structure
Why Maven is Used

Without Maven:

Manually download JAR files
Handle versions yourself
Configure build process manually

With Maven:

Dependencies download automatically
Standard project structure
Easy build and deployment
Maven Project Structure
Project
│
├── src
│   ├── main
│   │   └── java
│   └── test
│       └── java
│
├── pom.xml
└── target
Important Folders
src/main/java → Main application code
src/test/java → Test code
target/ → Compiled output files
pom.xml

The heart of Maven project.

pom = Project Object Model

Example:

<project>
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>demo</artifactId>
    <version>1.0</version>
</project>
Important Terms
Term	Meaning
groupId	Company/organization name
artifactId	Project name
version	Project version
Dependency

Libraries required by project.

Example:

<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.13.2</version>
    </dependency>
</dependencies>

Maven downloads it automatically from repository.

Maven Repository

Storage location for dependencies.

Types:

Local Repository → In your system
Central Repository → Online Maven server
Remote Repository → Company/private server
Maven Lifecycle
1. validate

Checks project correctness

2. compile

Compiles source code

3. test

Runs test cases

4. package

Creates JAR/WAR file

5. install

Stores package in local repository

6. deploy

Uploads package to remote repository

Important Maven Commands
Command	Purpose
mvn compile	Compile code
mvn test	Run tests
mvn package	Create JAR/WAR
mvn install	Install locally
mvn clean	Delete target folder
Advantages of Maven
Automatic dependency management
Easy project build
Standard project structure
Better team collaboration
Saves development time
Maven in One Line

“Maven automates building, dependency management, and project lifecycle for Java applications.”
