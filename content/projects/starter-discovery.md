+++
title = "CoffeeNet - Starter Discovery"
weight = 1
githubUrl = "https://github.com/coffeenet/coffeenet-starter"
+++


# CoffeeNet Starter - Discovery

This CoffeeNet starter configures the service discovery for your application,
provides your application as client to the discovery service and offers already
known clients to you by the `coffee.synyx.autoconfigure.discovery.service.CoffeeNetAppService`.


## Getting started

This is a module in the starter set, so you first need to declare your project
as a child of the starter `parent` by editing the `pom.xml` file.

```xml
<parent>
    <groupId>coffee.synyx</groupId>
    <artifactId>coffeenet-starter-parent</artifactId>
    <version>${parent.version}</version>
    <relativePath />
</parent>
```

and adding the repository to receive the dependencies

```xml
<repositories>
  <repository>
    <id>releases.public.nexus.synyx.de</id>
    <url>http://nexus.synyx.de/content/repositories/public-releases</url>
  </repository>
</repositories>
```

Now you can enable service discovery in your project, by first adding the dependency:

```xml
<dependency>
    <groupId>coffee.synyx</groupId>
    <artifactId>starter-discovery</artifactId>
</dependency>
```

In order to get everything up and running there are some requirements that
your project must fulfill.


## Configuration

```yaml
coffeenet:
  application-name:
  allowed-authorities:
  profile: development
  discovery:
    enabled: true
    client:
      service-url:
        defaultZone: http://localhost:8761/eureka/
    instance:
      hostname: localhost
      non-secure-port: 8080
      home-page-url:
```

The configuration with their default values.

`coffeenet.allowed-authorities` is a comma separated list that filters the application
from the navigation bar if the user does not have the required roles.

The service discovery tries to communicate with the discovery service, if the configuration
```yaml
coffeenet:
  profile: integration
```
is activated. If it is on `development` a mock service will be used.