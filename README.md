# Java Check Styles
Contains check styles and Findbugs configurations to be used in Java projects.

## Usage
To use in your Java project, just add the following repositories to your project's pom.xml file's repositories section:

```
<repository>
     <id>emergya-check-style</id>
     <url>http://nexus.emergya.es/nexus/content/repositories/emergya-check-style</url>
 </repository>
 <repository>
     <id>emergya-check-style-snapshots</id>
     <url>http://nexus.emergya.es/nexus/content/repositories/emergya-check-style-snapshots</url>
 </repository>
```

and then the java-common-checks artifact as parent of the project (note that maven will complain somewhat):

```
<parent>
    <groupId>com.emergya</groupId>
    <artifactId>java-common-checks</artifactId>
    <version>0.1-SNAPSHOT</version>
</parent>
```

Doing that will make your project inherit the build plugins defined in java-common-checks so you don't have to configure that manually. If your project is composed of several maven projects, please set the parent configuration to your parent project so all submodules inherit the config.

## Configurations applied
### Findbugs
Configuration for Findbugs can be found in java-common-checks' pom.xml file.

### Checkstyle:
For Checkstyle a rules file exists in java-common-checks-config subproject. This file inherits most rules from Sun's ruleset, but disables some and changes other. An incomplete list of changes
- Line lenght of 132 chars instead of just 80.
- Removed DesignForExtension (Spring's Java config doesn't like final methods annotated as @Bean)
