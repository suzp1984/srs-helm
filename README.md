[![](https://badgen.net/discord/members/yZ4BnPmHAd)](https://discord.gg/yZ4BnPmHAd)

Helm Charts for the [SRS](https://github.com/ossrs/srs) media server.

## Usage

First, you need to install [helm](https://helm.sh/docs/intro/install/). For example, on MacOS:

```bash
brew install helm
helm version --short
#v3.12.0+gc9f554d
```

Next, add the helm repository:

```bash
helm repo add srs http://helm.ossrs.io/stable
```

> Note: If you are in China, use the mirror repository [http://helm.ossrs.net/stable](http://helm.ossrs.net/stable) instead.

To install the SRS origin server, run:

```bash
helm install srs srs/srs-server
```

Visit [http://localhost:8080](http://localhost:8080) to access the SRS console.

For detailed information on using SRS, please refer to [https://ossrs.io](https://ossrs.io).

> Note: If you are in China, please refer to [https://ossrs.net](https://ossrs.net).

## Local Repository

You can also set up the local HELM repository by executing the following command:

```bash
docker run --rm -it -p 3000:80 ossrs/helm:latest
```

Next, add the local repository with this command:

```bash
helm repo add srs http://localhost:3000/stable
```

Now, you can utilize SRS HELM. For more information, refer to the [Usage](#usage) section.

## Test Repository

You can build a test HELM repository by executing the following command:

```bash
docker build -t test -f Dockerfile .
```

Start the local test docker image:

```bash
docker run --rm -it -p 3000:80 test
```

Next, add the local repository with this command:

```bash
helm repo add srs http://localhost:3000/stable
```

Now, you can utilize SRS HELM. For more information, refer to the [Usage](#usage) section.

## Develop Repository

Serve current directory in Nginx or other HTTP server, for example:

```bash
docker run --rm -it -p 3000:80 -v $(pwd):/usr/share/nginx/html \
  -v $(pwd)/conf/nginx.conf:/etc/nginx/nginx.conf \
  -v $(pwd)/conf/conf.d/default.conf:/etc/nginx/conf.d/default.conf \
  nginx:stable
```

Next, add the local repository with this command:

```bash
helm repo add srs http://localhost:3000/stable
```

Now, you can utilize SRS HELM. For more information, refer to the [Usage](#usage) section.

## Features

Note all features of SRS are supported by the HELM charts, however, we're working to migrate them to HELM.

- [x] v1.0.0: Support RTMP origin server, listen at 1935/tcp.
- [x] v1.0.1: Support HTTP origin server, for HTTP-FLV, listen at 8080/tcp.
- [x] v1.0.1: Support HTTP static server, for HLS and players, listen at 8080/tcp.
- [x] v1.0.2: Upgrade SRS to SRS v5.0-b2, 5.0 beta2, v5.0.166.
- [x] v1.0.2: Support config SRS by env, enable HTTP-API, listen at 1985/tcp.
- [x] v1.0.3: Support SRT stream server, listen at 10080/udp.
