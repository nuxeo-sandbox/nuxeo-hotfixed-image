# About

Simple example of running the custom container provided in [mp-hotfix](../mp-hotfix/)

This example does *not* require an internet connection.

By default the Nuxeo docker image automatically installs the latest hotfixes. This is disabled by using the [`NUXEO_INSTALL_HOTFIX` flag](https://hub.docker.com/_/nuxeo).

In addition, Nuxeo by default expects to be able to reach connect.nuxeo.com. This is disabled using the [`org.nuxeo.connect.server.reachable` configuration parameter](https://doc.nuxeo.com/nxdoc/configuration-parameters-index-nuxeoconf/#orgnuxeoconnectserverreachable).
