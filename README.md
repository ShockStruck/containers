<!---
NOTE: AUTO-GENERATED FILE
to edit this file, instead edit its template at: ./github/scripts/templates/README.md.j2
-->
<div align="center">


## Containers

_An opinionated collection of container images_

</div>

<div align="center">

![GitHub Repo stars](https://img.shields.io/github/stars/ShockStruck/containers?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/ShockStruck/containers?style=for-the-badge)
![GitHub Workflow Status (with event)](https://img.shields.io/github/actions/workflow/status/ShockStruck/containers/release-scheduled.yaml?style=for-the-badge&label=Scheduled%20Release)

</div>

Welcome to our container images, if looking for a container start by [browsing the GitHub Packages page for this repo's packages](https://github.com/ShockStruck?tab=packages&repo_name=containers).

## Mission statement

The goal of this project is to support [semantically versioned](https://semver.org/), [rootless](https://rootlesscontaine.rs/), and [multiple architecture](https://www.docker.com/blog/multi-arch-build-and-images-the-simple-way/) containers for various applications.

We also try to adhere to a [KISS principle](https://en.wikipedia.org/wiki/KISS_principle), logging to stdout, [one process per container](https://testdriven.io/tips/59de3279-4a2d-4556-9cd0-b444249ed31e/), no [s6-overlay](https://github.com/just-containers/s6-overlay) and all images are built on top of [Alpine](https://hub.docker.com/_/alpine) or [Ubuntu](https://hub.docker.com/_/ubuntu).

## Tag immutability

The containers built here do not use immutable tags, as least not in the more common way you have seen from [linuxserver.io](https://fleet.linuxserver.io/) or [Bitnami](https://bitnami.com/stacks/containers).

We do take a similar approach but instead of appending a `-ls69` or `-r420` prefix to the tag we instead insist on pinning to the sha256 digest of the image, while this is not as pretty it is just as functional in making the images immutable.

| Container                                          | Immutable |
|----------------------------------------------------|-----------|
| `ghcr.io/ShockStruck/sonarr:latest`                   | ❌         |
| `ghcr.io/ShockStruck/sonarr:3.0.8.1507`                | ❌         |
| `ghcr.io/ShockStruck/sonarr:latest@sha256:8053...`    | ✅         |
| `ghcr.io/ShockStruck/sonarr:3.0.8.1507@sha256:8053...` | ✅         |

_If pinning an image to the sha256 digest, tools like [Renovate](https://github.com/renovatebot/renovate) support updating the container on a digest or application version change._

## Passing arguments to a application

Some applications do not support defining configuration via environment variables and instead only allow certain config to be set in the command line arguments for the app. To circumvent this, for applications that have an `entrypoint.sh` read below.

1. First read the Kubernetes docs on [defining command and arguments for a Container](https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/).
2. Look up the documentation for the application and find a argument you would like to set.
3. Set the argument in the `args` section, be sure to include `entrypoint.sh` as the first arg and any application specific arguments thereafter.

    ```yaml
    args:
      - /entrypoint.sh
      - --port
      - "8080"
    ```

## Configuration volume

For applications that need to have persistent configuration data the config volume is hardcoded to `/config` inside the container. This is not able to be changed in most cases.

## Available Images

Each Image will be built with a `latest` tag, along with tags specific to it's version. Available Images Below

Container | Channel | Image | Latest Tags
--- | --- | --- | ---
[actions-runner]() | stable | ghcr.io/ShockStruck/actions-runner |
[autoscan]() | stable | ghcr.io/ShockStruck/autoscan |
[cdpgvector]() | stable | ghcr.io/ShockStruck/cdpgvector |
[cni-plugins]() | stable | ghcr.io/ShockStruck/cni-plugins |
[getmail]() | stable | ghcr.io/ShockStruck/getmail |
[home-assistant](https://github.com/ShockStruck/containers/pkgs/container/home-assistant) | stable | ghcr.io/ShockStruck/home-assistant |![2024.7.4](https://img.shields.io/badge/2024.7.4-blue?style=flat-square) ![latest](https://img.shields.io/badge/latest-green?style=flat-square)
[kms]() | master | ghcr.io/ShockStruck/kms |
[kubernetes-kubectl]() | kubectl | ghcr.io/ShockStruck/kubernetes-kubectl |
[lidarr]() | master | ghcr.io/ShockStruck/lidarr |
[lidarr-develop]() | develop | ghcr.io/ShockStruck/lidarr-develop |
[lidarr-nightly]() | nightly | ghcr.io/ShockStruck/lidarr-nightly |
[par2cmdline-turbo]() | stable | ghcr.io/ShockStruck/par2cmdline-turbo |
[plex]() | stable | ghcr.io/ShockStruck/plex |
[plex-beta]() | beta | ghcr.io/ShockStruck/plex-beta |
[postgres-init]() | stable | ghcr.io/ShockStruck/postgres-init |
[prowlarr]() | master | ghcr.io/ShockStruck/prowlarr |
[prowlarr-develop]() | develop | ghcr.io/ShockStruck/prowlarr-develop |
[prowlarr-nightly]() | nightly | ghcr.io/ShockStruck/prowlarr-nightly |
[radarr]() | master | ghcr.io/ShockStruck/radarr |
[radarr-develop]() | develop | ghcr.io/ShockStruck/radarr-develop |
[radarr-nightly]() | nightly | ghcr.io/ShockStruck/radarr-nightly |
[radicale]() | stable | ghcr.io/ShockStruck/radicale |
[readarr-develop]() | develop | ghcr.io/ShockStruck/readarr-develop |
[readarr-nightly]() | nightly | ghcr.io/ShockStruck/readarr-nightly |
[sabnzbd]() | stable | ghcr.io/ShockStruck/sabnzbd |
[socks5]() | stable | ghcr.io/ShockStruck/socks5 |
[sonarr]() | main | ghcr.io/ShockStruck/sonarr |
[sonarr-develop]() | develop | ghcr.io/ShockStruck/sonarr-develop |
[theme-park]() | stable | ghcr.io/ShockStruck/theme-park |
[volsync]() | stable | ghcr.io/ShockStruck/volsync |


## Contributing

1. Install [Docker](https://docs.docker.com/get-docker/), [Taskfile](https://taskfile.dev/) & [Cuelang](https://cuelang.org/)
2. Get familiar with the structure of the repositroy
3. Find a similar application in the apps directory
4. Copy & Paste an application and update the directory name
5. Update `metadata.json`, `Dockerfile`, `ci/latest.sh`, `ci/goss.yaml` and make it suit the application build
6. Include any additional files if required
7. Use Taskfile to build and test your image

    ```ruby
    task APP=sonarr CHANNEL=main test
    ```

### Automated tags

Here's an example of how tags are created in the GitHub workflows, be careful with `metadata.json` as it does affect the outcome of how the tags will be created when the application is built.

| Application | Channel   | Stable  | Base    | Generated Tag               |
|-------------|-----------|---------|---------|-----------------------------|
| `sonarr`    | `develop` | `false` | `false` | `sonarr-develop:3.0.8.1538` |
| `sonarr`    | `develop` | `false` | `false` | `sonarr-develop:latest`     |
| `sonarr`    | `main`    | `true`  | `false` | `sonarr:3.0.8.1507`         |
| `sonarr`    | `main`    | `true`  | `false` | `sonarr:latest`             |

## Deprecations

Containers here can be **deprecated** at any point, this could be for any reason described below.

1. The upstream application is **no longer actively developed**
2. The upstream application has an **official upstream container** that follows closely to the mission statement described here
3. The upstream application has been **replaced with a better alternative**
4. The **maintenance burden** of keeping the container here **is too bothersome**

**Note**: Deprecated containers will remained published to this repo for 6 months after which they will be pruned.
## Credits

A lot of inspiration and ideas are thanks to the hard work of [hotio.dev](https://hotio.dev/) and [linuxserver.io](https://www.linuxserver.io/) contributors, and [onedr0p](https://github.com/onedr0p).


