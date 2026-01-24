# nifi_flows (local Docker stack)

## Overview

Reusable local infrastructure for Apache NiFi development.

Designed to:

- prototype and test data pipelines locally
- develop flows before deploying to production clusters
- integrate NiFi with Kafka and databases
- version flows via NiFi Registry
- reproduce real-world data engineering environments

Useful for rapid experimentation without touching production systems.

Here is the local stack for developing, testing, and prototyping Apache NiFi data pipelines
Minimal local environment for developing and testing Apache NiFi flows.

This stack runs:

NiFi → Kafka → PostgreSQL  
NiFi Registry for versioned flows  
All services run locally via Docker Compose

Provides a reproducible Docker environment that mirrors real-world NiFi + Kafka + PostgreSQL setups.

## Tech Stack

- Apache NiFi 2.5
- NiFi Registry
- Apache Kafka
- PostgreSQL
- Docker / Docker Compose

## Requirements

- Docker
- Docker Compose (v2+)

Tested on macOS (Apple Silicon / M2).

## How to run

From the **repository root**:

```bash
docker compose -f docker/docker-compose.yml up -d
```

## How to stop

From the **repository root**:

```bash
docker compose -f docker/docker-compose.yml stop
```

## How to remove everything

From the **repository root**:

```bash
docker compose -f docker/docker-compose.yml down -v
```

## UI access

``` https://localhost:8443/nifi```

username: admin

password: adminadminadmin

## Import NiFi Flows from GitHub

1. In NiFi UI → **Controller Settings** → **Registry Clients** → **+**.
2. Select **GitHubFlowRegistryClient** and set:
   - **API URL**: `https://api.github.com`
   - **Repository Owner**: `Ilia2704`
   - **Repository Name**: `nifi_flows`
   - **Default Branch**: `main`
   - **Repository Path**: ``
   - **Auth**: None (public repo)
3. Apply → on canvas **Add** → **Import from Registry** → pick your flow.

![alt text](image.png)

## Flow description:

### RemotePG 
### Remote Process Group & MiNiFi integration

**Purpose**  
Demonstrates how to build destination flows that receive data from external NiFi clusters and MiNiFi agents using Remote Process Groups (RPG).

**Key concepts covered**
- Remote Input / Output Ports
- Receiving data from:
  - another NiFi cluster
  - MiNiFi agents
- Attribute enrichment using `UpdateAttribute`
- Centralized entry point for distributed data ingestion

**Typical use cases**
- Edge → Core NiFi ingestion
- MiNiFi → NiFi pipelines
- Cross-cluster flow routing

Shows how NiFi is used in distributed environments and how remote connectivity is organized.


### Reusable example pipelines (core data engineering patterns)

**Purpose**  
A collection of flows to practice building real-world Apache NiFi pipelines.

**Key concepts covered**
- General data pipeline construction
- Record-oriented processing:
  - `ConvertRecord`
  - `MergeRecord`
  - `SplitRecord`
- JSON processing:
  - `EvaluateJsonPath`
  - `FlattenJson`
- Data enrichment and joins
- Flow routing and prioritization
- Writing data to local storage using `PutFile`
- HTTP-based integrations with `InvokeHTTP`
- SQL / database-oriented pipeline patterns (conceptual)

**Typical use cases**
- Hands-on exercises during the course
- Learning how processors connect into complete pipelines
- Practicing data transformation and enrichment
- Understanding backpressure and flow control

Provides an isolated local environment for experimentation with NiFi fundamentals and common data engineering patterns.


### Feature demonstrations & advanced examples

**Purpose**  
A set of compact demo flows illustrating specific Apache NiFi features and best practices.

**Key concepts covered**
- NiFi Expression Language (EL)
- Dynamic attributes and metadata manipulation
- JSON transformations using `JoltTransformJSON`
- Flow optimization techniques
- Process Group (PG) configuration:
  - batching
  - scheduling
  - layout orientation
- Kafka integration:
  - `PublishKafka`
  - `ConsumeKafka`
- Script-based processing examples (conceptual)

**Typical use cases**
- Reference pipelines for common data engineering patterns
- Explaining processor behavior and configuration
- Reference examples for building optimized flows
- Quick experimentation with advanced features

Helps practitioners understand advanced NiFi capabilities and internal mechanics.

## Scope & limitations

This repository is intended for:
- local development
- experimentation

It does not cover:
- production security
- HA NiFi clusters
- secrets management


# Related Projects

**Custom Python Processor for Apache NiFi**  
  Repository containing a custom Apache NiFi processor implemented in Python.  
  Demonstrates how to extend NiFi with Python-based logic for custom data processing use cases.  
     https://github.com/Ilia2704/nifi-extentions-python
