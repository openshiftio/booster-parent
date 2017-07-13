# Parent pom.xml for booster projects

Contains the necessary dependencies and the required versions for the booster projects.


## Extending the parent

You may want to override:

* project name -  `OpenShift.io Boosters`
* project description - `Strap in; we're going to production. Now.`
* project url - `https://github.com/openshiftio`
* SCM metadata (mandatory for release)

```xml
<scm>
  <url>https://github.com/openshiftio</url>
  <connection>https://github.com/openshiftio/booster-parent.git</connection>
  <developerConnection>scm:git:git:@github.com:openshiftio/booster-parent.git</developerConnection>
  <tag>HEAD</tag>
</scm>
```

## Generating license.xml

To generate the license.xml in your child project use:

```
mvn clean compile -Plicenses
```

Licenses are generated into `src/licenses`. It must be committed to the code repository. You must update the content (using the same command line) every time you update a dependency in your project.

Also be careful of the execution output. You may notice connection / read timeouts. Check that the content is correct and all files are there.

The license processing requires two files that need to be located into the `.openshiftio` directory:

* `licenses-fix.xsl` from https://raw.githubusercontent.com/openshiftio-vertx-boosters/vertx-http-booster/master/.openshiftio/licenses-fix.xsl
* `licenses.xml` from https://raw.githubusercontent.com/openshiftio-vertx-boosters/vertx-http-booster/master/.openshiftio/licenses.xsl

# Developers section

## Deploying a snapshot:

`mvn clean deploy -Popenshiftio`
  
## Release process
  
1. `mvn release:prepare -Popenshiftio`
2. `git checkout $TAG`
3. export GPG_TTY=$(tty)  # <---- required on mac with gpg2
4. `mvn clean deploy -Prelease -Popenshiftio`