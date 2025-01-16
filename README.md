# Tool Artifact of Kieker Observability Framework Version 2

This is a tool artifact of the [Kieker Observability Framework Version
2](https://github.com/kieker-monitoring/kieker), submitted to [ICPE
2025](https://icpe2025.spec.org/).

![DemoArchitecture_v4_nofonts](https://github.com/user-attachments/assets/c8bdc7e0-cd3a-41ec-b701-ee8b27eba89b)

## Overview

The Docker compose file configures all required software components as Docker
containers and launches the[TeaStore
microservices](https://github.com/DescartesResearch/TeaStore) (with the Kieker
agents), Kieker OpenTelemetry Transformer, [the ExplorViz software
visualization framework](https://github.com/ExplorViz/frontend/), and the
[JMeter load testing tool](https://github.com/apache/jmeter).

First, JMeter sends HTTP requests to TeaStore. Then, the Kieker agents attached
to each TeaStore microservice send traces to Kieker OpenTelemetry Transformer.
It translates all received Kieker traces into OpenTelemetry spans and sends
them to ExplorViz. Finally, ExplorViz visualizes TeaStore using the received
span data.

## Requirements

* An operating system with [Docker Desktop](https://docs.docker.com/desktop/) and Git.
* Launching the tool artifact requires two TCP ports: ``8080`` and ``8082``

## Installation

You can [download the repository files](https://github.com/kieker-monitoring/kieker-demo/archive/refs/heads/main.zip) directly without git.

```bash
git clone https://github.com/kieker-monitoring/kieker-demo.git
```

## Start the System

Launching all Docker containers will take 2 to 3 minutes.

```bash
cd kieker-demo
docker compose up -d
```

## Browsing TeaStore and ExplorViz WebUIs

After launching the containers, you will be able to browse the WebUIs of TeaStore and ExplorViz.

* TeaStore uses the TCP port 8080. On localhost the url is [http://localhost:8080](http://localhost:8080).
* ExplorViz uses the TCP port 8082. The url is [http://localhost:8082](http://localhost:8082).

## Stop the System

```bash
docker compose down -v
```

## Prior works

* This tool artifact began as an artifact for the
  [SSP2024](https://www.performance-symposium.org/ssp-2024/) paper,
  [*Interoperability From Kieker to OpenTelemetry: Demonstrated as Export to
  ExplorViz*](https://arxiv.org/abs/2411.07982).
* The provided Docker compose files are based on the [ExplorViz Docker compose
  deployment scripts](https://github.com/ExplorViz/deployment).
