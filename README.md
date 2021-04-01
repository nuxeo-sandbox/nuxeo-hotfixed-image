# About nuxeo-hotfixed-image

Examples for building a custom Nuxeo Docker image that has hotfixes pre-installed. The same principle can be used to install other [Nuxeo Packages](https://marketplace.nuxeo.com/) as well.

Tip: any `nuxeoctl` commands executed in the `Dockerfile` need to be executed via [`/docker-entrypoint.sh`](https://github.com/nuxeo/docker-nuxeo/blob/321756e6c8d808b1fc225cfdc9287e2bde8ec319/10.10/docker-entrypoint.sh).

Tip: because of the above, `docker-entrypoint.sh` [sets a flag](https://github.com/nuxeo/docker-nuxeo/blob/321756e6c8d808b1fc225cfdc9287e2bde8ec319/10.10/docker-entrypoint.sh#L42) to indicate that the config has run. It is important to clear this flag so that when the container is launched it will process the config as expected.

# Usage

* The example in the [mp-hotfix](mp-hotfix) folder uses the `mp-hotfix` command from [`nuxeoctl`](https://doc.nuxeo.com/n/is7) to automatically install the latest hotfixes.
* The example in the [mp-install](mp-install) folder uses the `mp-install` command from [`nuxeoctl`](https://doc.nuxeo.com/n/is7) to install a specific hotfix version. Note that dependency resolution will automatically install prior hotfixes as needed.
* The docker-compose example in the [disconnected](disconnected) folder is to test using the custom image in a disconnected environment; i.e. in an environment where the container cannot reach connect.nuxeo.com. This tests two aspects:
  * There is a flag for the Nuxeo Docker container to skip hotfix installation, [`NUXEO_INSTALL_HOTFIX`](https://hub.docker.com/_/nuxeo)
  * There is a `nuxeo.conf` param to indicate that the server is in offline mode, [org.nuxeo.connect.server.reachable](https://doc.nuxeo.com/nxdoc/configuration-parameters-index-nuxeoconf/#orgnuxeoconnectserverreachable)
* The docker-compose example in the [connected](connected) folder is a vanilla config to launch the custom image with full connectivity

To run any of the builds you need to provide your `instance.clid` file. Place it in the same folder as the `Dockerfile`.

To run an instance via `docker-compose` you need to configure a `.env` file with:

```
STUDIO=<your-stufio-project-id>
CLID=<your-clid>
```

# Support

**These features are not part of the Nuxeo Production platform.**

These solutions are provided for inspiration and we encourage customers to use them as code samples and learning resources.

This is a moving project (no API maintenance, no deprecation process, etc.) If any of these solutions are found to be useful for the Nuxeo Platform in general, they will be integrated directly into platform, not maintained here.

# License

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

# About Nuxeo

Nuxeo Platform is an open source Content Services platform, written in Java. Data can be stored in both SQL & NoSQL databases.

The development of the Nuxeo Platform is mostly done by Nuxeo employees with an open development model.

The source code, documentation, roadmap, issue tracker, testing, benchmarks are all public.

Typically, Nuxeo users build different types of information management solutions for [document management](https://www.nuxeo.com/solutions/document-management/), [case management](https://www.nuxeo.com/solutions/case-management/), and [digital asset management](https://www.nuxeo.com/solutions/dam-digital-asset-management/), use cases. It uses schema-flexible metadata & content models that allows content to be repurposed to fulfill future use cases.

More information is available at [www.nuxeo.com](https://www.nuxeo.com).
