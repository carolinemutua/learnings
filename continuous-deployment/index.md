---
title: Continuous Deployment (CD)
layout: default
nav_order: 4
has_children: true
---

# Continuous Deployment (CD)

Continuous deployment (CD) is the other half of "CI/CD". Where continuous integration (CI) checks a change before it is allowed in, continuous deployment takes the change that just merged and gets it running in the live environment automatically, with no manual copy-to-server step. CI answers "is this change safe?"; CD answers "now put it where people can use it."

This kit uses a real, working pipeline as its example: an MCP server that deploys to Render, driven by a GitHub Actions workflow. Every idea below points at something that actually runs in that repository.

## CI and CD as one pipeline

```mermaid
mindmap
  root((CI/CD))
    CI checks
      Runs on the pull request
      Install and test
      Green means safe to merge
    Merge to main
      The handoff point
      CI ends, CD begins
    CD deploys
      Runs on push to main
      Builds and ships to the host
      Live without manual steps
    The host
      Render, in this example
      Runs the built service
```

The pipeline is a single conveyor belt. A change rides CI while it is a proposal, crosses into CD the moment it merges, and ends up live.

```mermaid
flowchart LR
    A["Open pull request"] --> B["CI workflow<br/>install + smoke test"]
    B -->|green| C["Merge to main"]
    C --> D["CD workflow<br/>runs on push to main"]
    D --> E["Trigger host deploy hook"]
    E --> F["Host builds and runs<br/>the new version"]
    F --> G["Live service"]
```

## Where Render fits

Render is a cloud host that runs the service. It is the destination of the deployment, not the thing that decides when to deploy. In this pipeline the decision to deploy is owned by a GitHub Actions workflow, which calls a Render deploy hook (a secret URL that tells Render "build and release now"). This is a deliberate design choice: auto-deploy is turned off inside Render so that every deployment is a single tracked event, triggered from one place.

```mermaid
flowchart LR
    subgraph GH["GitHub"]
        A["Merge to main"] --> B["Deploy workflow"]
        B --> C["Record a GitHub Deployment"]
        B --> D["POST to Render deploy hook"]
    end
    subgraph RN["Render"]
        D --> E["Build the Docker image"]
        E --> F["Run the web service"]
    end
    B --> G["Mark deployment<br/>success or failure"]
```

## Pages in this kit

| Page | Purpose |
| --- | --- |
| [CD explained with a real pipeline]({{ site.baseurl }}/continuous-deployment/pipeline/) | The full CI-to-CD flow using the kenya-schools-mcp repository: the two workflows, the Render blueprint, deploy hooks, secrets, and why deployments are recorded as tracked events |
