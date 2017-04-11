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

# Developers section

## Deploying a snapshot:

`mvn clean deploy -Popenshiftio`
  
## Release process
  
1. `mvn release:prepare -Popenshiftio`
2. `git checkout $TAG`
3. export GPG_TTY=$(tty)  # <---- required on mac with gpg2
4. `mvn clean deploy -Prelease -Popenshiftio`