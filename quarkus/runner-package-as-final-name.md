---
layout: post
date: 2020-10-18
tags:
- Quarkus
- Development
---

## Runner package as final name

>
> Tested with Quarkus 1.8.1.Final
> 

Quarkus packages the final project with a *-runner* classifier when the ```uberJar``` property is true, so this generates
two packages:

* ```finalName.jar``` package including only the Java classes and resources
* ```finalName-runner.jar``` package as uber jar or executable package

Sometime you need to have the executable package with the original name of the application, for example your CICD pipeline
is expecting that.

At the moment there is not an clear method to set up that, as you can see
in this [GitHub issue](https://github.com/quarkusio/quarkus/issues/2931), but this article describes a
workaround that could help you.

Defined the final name in ```pom.xml``` as:

```xml
  <finalName>${artifactId}</finalName>
```

And declared the following properties in ```application.properties``` file:

```text
quarkus.package.type=uber-jar
quarkus.package.runner-suffix=-${version}
```

That configuration packages the runner package as ```artifactId-version.jar``` file.

### References

* [Quarkus Issue #2931 - [Maven] Don't change finalName with runner classifier](https://github.com/quarkusio/quarkus/issues/2931)

* * *

[Quarkus Knowledge Base](./)
[Knowledge Base](../)
