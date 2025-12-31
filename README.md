# nifi_flows (local Docker stack)

Here is the flows were built in nifi 2.x for BigDataSchool course
Minimal local environment for developing and testing Apache NiFi flows.

This stack runs:
- Apache NiFi **2.7.2** (single node, HTTPS)
- NiFi Registry **2.7.2**
- Apache Kafka (single broker)
- PostgreSQL

Designed for **local development**

## Requirements

- Docker
- Docker Compose (v2+)

Tested on macOS (Apple Silicon / M2).

## How to run

From the **repository root**:

```bash
docker compose -f docker/docker-compose.yml up -d
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
   - **Repository Path**: `flows`
   - **Auth**: None (public repo)
3. Apply → on canvas **Add** → **Import from Registry** → pick your flow.

