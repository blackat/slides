## Maven

- Address both how software is built and dependencies.
- Conventions: 
    - `src/main/java`, `src/main/resources`
    - `src/test/java`, `src/test/resources`
- POM (Project Object Model)


## Build Lifecycles

It is a list of **pre-defined phases** to give order to **goal** execution.

```bash
 1  validate
 2  generate-sources
 3  process-sources
 4  generate-resources
 5  process-resources
 6  compile
 7  process-test-sources
 8  process-test-resources
 9  test-compile
10  test
11  package
12  install
13  deploy
```


## Lifecycle Examples

```bash
mvn clean install
```

```bash
mvn clean package -Pprofile-ambulance
```

```bash
mvn test -Pjacoco-coverage
```


## Plug-ins

- Primary way to extend Maven:
    - `org.apache.maven.plugin.AbstractMojo`
- Plugin provides a set of goals:
    - `mvn [plugin-name]:[goal-name]`
- Goals can be associated with phases of the lifecycle:

```bash
<execution>
    <id>jacoco-site</id>
    <phase>package</phase>
    <goals>
        <goal>report</goal>
    </goals>
</execution>
```


## Repositories

- `.m2` local repo
- remote repo (Nexus)
- both store artifacts: `groupId:artifactId:version`
- Snapshot
    - instable version, nighly built, under development, **latest build**, **not release yet**
    - not allowed in a release, can get frequent updates
        - `maven-metadata-local.xml` tells which is the latest snapshot
        - `<updatePolicy>`: always, daily, never


## SNAPSHOT vs. Stable

When an application is built:
- **stable:** maven searches for dependencies in the local repo, if stable version not found, it searches in the remote one and copies it into the local one.
- **-SNAPSHOT:** version is not stable, maven searches a newer version in the remote repo once a day
    - `foo-1.0-20110506.110000-1.jar` artifact of the 06/05/2011 at 11:00:00



## SNAPSHOT Configuration

```bash
<repository>
    <id>foo-repository</id>
    <url>...</url>
    <snapshots>
        <enabled>true</enabled>
        <updatePolicy>always/daily/xxx min/never</updatePolicy>
    </snapshots>
</repository>
```


## Continuos Integration (CI)

> practice of merging all developer working copies to a shared mainline several times a day