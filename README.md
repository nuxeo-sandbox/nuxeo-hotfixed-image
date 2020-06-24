# About nuxeo-hotfixed-image

Examples for building a custom Nuxeo Docker image that has hotfixes pre-installed. The same principle can be used to install other [Nuxeo Packages](https://marketplace.nuxeo.com/) as well.

Tip: any `nuxeoctl` commands need to be executed via `/docker-entrypoint.sh`.

# Usage

* The example in the `mp-hotfix` folder uses the `mp-hotfix` command from [`nuxeoctl`](https://doc.nuxeo.com/n/is7) to automatically install the latest hotfixes.
* The example in the `mp-install` folder uses the `mp-install` command from [`nuxeoctl`](https://doc.nuxeo.com/n/is7) to install a specific hotfix version. Note that dependency resolution will automatically install prior hotfixes if needed.

To run the build you need to provide your `instance.clid` file. Place it in the same folder as the `Dockerfile`.

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