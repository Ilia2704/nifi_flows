# nifi_flows
Here is the flows were built in nifi 2.x for BigDataSchool course

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

