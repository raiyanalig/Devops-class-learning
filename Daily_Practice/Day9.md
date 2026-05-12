DAY 2 — Dependencies + Plugins + Maven Wrapper
1. Dependencies

Dependencies are external libraries required by the project.

Example:

<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.13</version>
    </dependency>
</dependencies>
2. Dependency Scope
Scope	Meaning
compile	Available everywhere
test	Only during testing
provided	Provided by server
runtime	Needed at runtime
3. Transitive Dependencies

When one dependency automatically downloads another dependency.

Example:

Project → Spring Boot
Spring Boot → Logging library
4. Version Conflicts

Sometimes two dependencies use different versions of the same library.

Maven Resolution

Maven usually selects:

Nearest dependency
First declared dependency
5. Dependency Management

Used in parent projects to control versions centrally.

Example:

<dependencyManagement>
    <dependencies>
    </dependencies>
</dependencyManagement>
6. Parent POM

A parent POM shares configurations among multiple projects.

Benefits:

Reusability
Common dependency versions
Common plugins
7. Maven Plugins

Plugins extend Maven functionality.

Compiler Plugin

Used to compile Java code.

Example:

<plugin>
    <artifactId>maven-compiler-plugin</artifactId>
</plugin>
Surefire Plugin

Used for unit testing.

<plugin>
    <artifactId>maven-surefire-plugin</artifactId>
</plugin>
Shade Plugin

Creates an uber/fat JAR containing all dependencies.

<plugin>
    <artifactId>maven-shade-plugin</artifactId>
</plugin>
8. Maven Wrapper (mvnw)

Allows projects to use Maven without installing Maven globally.

Commands:

./mvnw clean install

Benefits:

Same Maven version for all developers
Easier CI/CD integration
9. Local Repository

Dependencies are stored locally in:

.m2/repository
