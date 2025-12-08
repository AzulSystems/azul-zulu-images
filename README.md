# Azul Zulu CA Docker official

This repository contains the Dockerfiles and build definitions used to produce the official **Azul Zulu** images on Docker Hub.

It acts as the canonical source referenced from the [`library/azul-zulu`](https://github.com/docker-library/official-images) metadata, which Docker Hub uses to build and publish the images.

## Purpose

- Provide a single source of truth for all Azul Zulu Dockerfiles.
- Define how official Azul Zulu images are built for different:
  - Java versions (e.g. 8, 11, 17, 21, 25, …)
  - Variations like JDK / JRE / headless etc.
  - Linux distributions (e.g. Alpine, Debian, Rocky Linux, …)
- Ensure that what is built on Docker Hub matches what is defined in this repository.

## Repository Structure

The repository is organized by Java major version and image flavor. Typical layout:

- `8/`, `11/`, `17/`, `21/`, `25/`, … – Java major versions
- Within each version:
  - Directories for different flavors / package types
  - Further subdirectories per base distribution
  - A `Dockerfile` in each leaf directory

Each leaf directory corresponds to one concrete image/tag built on Docker Hub.

## Local Usage

Although the primary consumer of this repo is the Docker Hub build system, you can also build images locally for testing or development.

Example:

```bash
git clone https://github.com/AzulSystems/azul-zulu-images.git
cd azul-zulu-images

# Navigate to the desired version/flavor/distro directory, for example:
cd 21/jdk/alpine3.22

docker build -t azul/zulu21-jdk-alpine:local-test .
docker run --rm azul/zulu21-jdk-alpine:local-test java -version
```