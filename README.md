# About nuxeo-hotfixed-image

Examples for building a custom Nuxeo Docker image that has hotfixes pre-installed. The same principle can be used to install other [Nuxeo Packages](https://marketplace.nuxeo.com/) as well.

Tip: any `nuxeoctl` commands executed in the `Dockerfile` need to be executed via [`/docker-entrypoint.sh`](https://github.com/nuxeo/docker-nuxeo/blob/321756e6c8d808b1fc225cfdc9287e2bde8ec319/10.10/docker-entrypoint.sh).

Tip: because of the above, `docker-entrypoint.sh` [sets a flag](https://github.com/nuxeo/docker-nuxeo/blob/321756e6c8d808b1fc225cfdc9287e2bde8ec319/10.10/docker-entrypoint.sh#L42) to indicate that the config has run. It is important to clear this flag so that when the container is launched it will process the config as expected.

# Usage

* The example in the `mp-hotfix` folder uses the `mp-hotfix` command from [`nuxeoctl`](https://doc.nuxeo.com/n/is7) to automatically install the latest hotfixes.
* The example in the `mp-install` folder uses the `mp-install` command from [`nuxeoctl`](https://doc.nuxeo.com/n/is7) to install a specific hotfix version. Note that dependency resolution will automatically install prior hotfixes as needed.
* The docker-compose example in the `disconnected` folder is to test using the custom image in a disconnected environment; i.e. in an environment where the container cannot reach connect.nuxeo.com. This tests two aspects:
  * There is a flag for the Nuxeo Docker container to skip hotfix installation, [`NUXEO_INSTALL_HOTFIX`](https://hub.docker.com/_/nuxeo)
  * There is a `nuxeo.conf` param to indicate that the server is in offline mode, [org.nuxeo.connect.server.reachable](https://doc.nuxeo.com/nxdoc/configuration-parameters-index-nuxeoconf/#orgnuxeoconnectserverreachable)
* The docker-compose example in the `connected` folder is a vanilla config to launch the custom image with full connectivity

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

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)

# About Nuxeo

[Nuxeo](www.nuxeo.com), developer of the leading Content Services Platform, is reinventing enterprise content management (ECM) and digital asset management (DAM). Nuxeo is fundamentally changing how people work with data and content to realize new value from digital information. Its cloud-native platform has been deployed by large enterprises, mid-sized businesses and government agencies worldwide. Founded in 2008, the company is based in New York with offices across the United States, Europe, and Asia. Learn more at www.nuxeo.com.