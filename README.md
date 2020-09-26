# Keycloak

Keycloak is an Open Source Identity and Access Management solution for modern Applications and Services.

This repository contains Docker images related to Keycloak.

- [keycloak](https://hub.docker.com/r/jboss/keycloak) Keycloak server
* [gatekeeper](https://hub.docker.com/r/keycloak/keycloak-gatekeeper) Keycloak gatekeeper
- [keycloak-adapter-wildfly](https://hub.docker.com/r/jboss/keycloak-adapter-wildfly) WildFly including Keycloak adapter


## Help and Documentation

* [Keycloak server image documentation](server/README.md)
* [Documentation](https://www.keycloak.org/documentation.html)
* [User Mailing List](https://lists.jboss.org/mailman/listinfo/keycloak-user) - Mailing list for help and general questions about Keycloak
* [JIRA](https://issues.jboss.org/projects/KEYCLOAK) - Issue tracker for bugs and feature requests


## Reporting Security Vulnerabilities

If you've found a security vulnerability, please look at the [instructions on how to properly report it](http://www.keycloak.org/security.html)


## Reporting an issue

If you believe you have discovered a defect in Keycloak please open an issue in our [Issue Tracker](https://issues.jboss.org/projects/KEYCLOAK).
Please remember to provide a good summary, description as well as steps to reproduce the issue.


## Getting started

To run Keycloak, run:

    docker run jboss/keycloak
    
For more details refer to the [Keycloak server image documentation](server/README.md).


## Contributing

Before contributing to Keycloak please read our [contributing guidelines](CONTRIBUTING.md).


## Other Keycloak Projects

* [Keycloak](https://github.com/keycloak/keycloak) - Keycloak Server and Java adapters
* [Keycloak Documentation](https://github.com/keycloak/keycloak-documentation) - Documentation for Keycloak
* [Keycloak QuickStarts](https://github.com/keycloak/keycloak-quickstarts) - QuickStarts for getting started with Keycloak
* [Keycloak Docker](https://github.com/jboss-dockerfiles/keycloak) - Docker images for Keycloak
* [Keycloak Gatekeeper](https://github.com/keycloak/keycloak-gatekeeper) - Proxy service to secure apps and services with Keycloak
* [Keycloak Node.js Connect](https://github.com/keycloak/keycloak-nodejs-connect) - Node.js adapter for Keycloak
* [Keycloak Node.js Admin Client](https://github.com/keycloak/keycloak-nodejs-admin-client) - Node.js library for Keycloak Admin REST API


## License

* [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)

## docker build
<!--
1.  cd ../keycloak
2.  mvn -Pdistribution -pl distribution/server-dist -am -Dmaven.test.skip clean install
3.  cd distribution/server-dist/target
4.  python -m SimpleHTTPServer 8989
5.  cd ../../../keycloak-container/server
6.  docker rmi 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com/keycloak-repository:latest
7.  docker system prune
8.  docker build --no-cache -t 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com/keycloak-repository:latest --build-arg KEYCLOAK_DIST=http://192.168.1.85:8989/keycloak-7.0.0.tar.gz . 
9.  export AWS_PASSWORD=$(aws ecr get-login-password --region ap-northeast-2)
10.  docker login --username AWS --password ${AWS_PASSWORD} 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com
11.  docker push 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com/keycloak-repository:latest
-->
1.  cd server
2.  docker rmi 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com/keycloak-repository:latest
3.  docker build -t 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com/keycloak-repository:latest --build-arg GIT_REPO=jjangyoonjoo/keycloak --build-arg GIT_BRANCH=add-social-provider .
4.  export AWS_PASSWORD=$(aws ecr get-login-password --region ap-northeast-2)
5.  docker login --username AWS --password ${AWS_PASSWORD} 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com
6.  docker push 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com/keycloak-repository:latest

aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 551099732354.dkr.ecr.ap-northeast-2.amazonaws.com