# Build JDBC Driver images

This repository provides a common repository for building JDBC Driver images to extend existing JBoss EAP Openshift images using S2I.

### Download the drivers from Oracle website

place the JDBC driver inside the directory of the image you want do build, example?

```bash
$ cp ~/Downloads/ojdbc8.jar oracle-driver-image/modules
$ docker build -f oracle-driver-image/Dockerfile -t kie-server-oracle-ext:7.8.1 .
```


