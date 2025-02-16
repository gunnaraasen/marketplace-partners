# DigitalOcean Marketplace Partner Tools

[![MIT license](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE) [![Pull Requests Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](http://makeapullrequest.com)

This repository contains resources for [DigitalOcean Marketplace](https://marketplace.digitalocean.com/) partners, like documentation on image requirements and creation, tools for image cleanup and validation, and templates for build automation.

## Getting Started

The overall process for creating a Marketplace image is as follows:

1. **Create and configure a build Droplet manually first** to make sure your configuration works. You can create a build Droplet with any method, like the [control panel](https://cloud.digitalocean.com/), the [API](https://developers.digitalocean.com/), or command-line tools like [`doctl`](https://github.com/digitalocean/doctl).

2. **Clean up and validate the build Droplet with the provided scripts**, `cleanup.sh` and `img_check.sh`. The scripts will check for and fix potential security concerns and verify that the image will be compatible with Marketplace.

3. **Take a [snapshot](https://www.digitalocean.com/docs/images/snapshots/) of the build Droplet** after you power it down, then test the resulting image. While there are several ways to create an image, we recommend snapshots as the most simple and consistent option.

4. **Automate your build** for replicable and configurable processes with minimal additional effort. We provide some Fabric and Packer templates to get you started.

5. **Submit your final image** to the Marketplace team for review.

Our [Getting Started documentation](getting-started.md) that includes our image requirements, configuration recommendations, how to run commands on first boot and first login, and details on exactly what our helper scripts do.

We also have a [Fabric template and docs](fabric) and a [Packer template and docs](packer) that you can use as starting points to automate your build system.

## Supported Operating Systems

To maintain compatibility with Marketplace tools and processes, we support a limited number of Linux distributions and releases for Marketplace images. These options provide either `deb`- or `rpm`-based packaging and will have security patches and updates for a reasonable time period.

We currently support the following OSes:

- Debian 9 (stretch)
- Ubuntu 18.04 (LTS)
- Ubuntu 16.04 (LTS)
- CentOS 7.x
- CentOS 6.x

All supported operating systems are available as base images to build on in the DigitalOcean cloud.

## Software Prerequisites

The following software packages are necessary for the initial configuration of new Droplets and to ensure connectivity:

- `cloud-init` 0.76 or higher (0.79 or higher recommended)
- `openssh-server` (SFTP-enabled configuration recommended)

 All of these packages are provided by default in the default DigitalOcean base images.
