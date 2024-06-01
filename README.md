[![Docs badge](https://img.shields.io/badge/docs-latest-brightgreen.svg)](https://fluxcd.io/)

# FluxCD multi-app

This repository contains the code and resources for my personal project. The project aims to [implement any interested features for local use]. It is designed to [overwrite helm charts contributed over private chart repository]. Feel free to explore the code and contribute if you're interested!

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

## Installing

To get started with this project, follow these steps:

Clone this repository to your local machine using git clone

```
git clone git@github.com:DrPalmeritta/fluxcd-multi-app.git
```

## Deployment

Example structure for typical fluxcd multi-app deployment:

```bash
fluxcd-repo-name/
├── apps/
│   ├── production-app/
│   │   ├── base/
│   │   │   ├── kustomization.yml
│   │   │   └── deployment.yml
│   │   └── overlays/
│   │       ├── dev/
│   │       │   ├── kustomization.yml
│   │       │   └── patch.yml
│   │       └── prod/
│   │           ├── kustomization.yml
│   │           └── patch.yml
│   ├── keycloak/
│   │   ├── base/
│   │   │   ├── kustomization.yml
│   │   │   └── deployment.yml
│   │   └── overlays/
│   │       ├── dev/
│   │       │   ├── kustomization.yml
│   │       │   └── patch.yml
│   │       └── prod/
│   │           ├── kustomization.yml
│   │           └── patch.yml
│   └── monitoring-app/
│       ├── base/
│       │   ├── kustomization.yml
│       │   └── deployment.yml
│       └── overlays/
│           ├── dev/
│           │   ├── kustomization.yml
│           │   └── patch.yml
│           └── prod/
│               ├── kustomization.yml
│               └── patch.yml
├── clusters/
│   ├── dev/
│   │   ├── kustomization.yml
│   │   └── apps.yml
│   └── prod/
│       ├── kustomization.yml
│       └── apps.yml
└── flux-system/
    ├── gotk-components.yaml
    ├── gotk-sync.yaml
    └── kustomization.yaml

```

`apps/` - Directory for applications.
<ul>
  <li>`production-app/, keycloak/, monitoring-app/` - Directories for each application.</li>
  <li>`base/` - Contains common manifests and customizations applied to all environments.</li>
    <ul>
      <li>`kustomization.yaml` - A Kustomize file describing the resources to be enabled.</li>
      <li>`deployment.yaml` - A sample deployment manifest.</li>
    </ul>
  <li>`overlays/` - Contains environment-specific customizations.</li>
  <li>`dev/ and prod/` - Directories for different environments.</li>
    <ul>
      <li>`kustomization.yaml` - The Kustomize file for the given environment.</li>
      <li>`patch.yaml` - A patch to change the configuration specific to this environment.</li>
    </ul>
</ul>

`clusters/` - The directory for the clusters.
<ul>
  <li>`dev/ and prod/` - Directories for the various clusters.</li>
    <ul>
      <li>`kustomization.yaml` - Kustomize file to apply applications to this cluster.</li>
      <li>`apps.yaml` - Application manifests for this cluster.</li>
    </ul>
</ul>

`flux/` - The directory for installing FluxCD.
<ul>
  <li>`gotk-components.yaml` - Flux components.</li>
  <li>`gotk-sync.yaml` - Flux synchronization configuration with the repository.</li>
  <li>`kustomization.yaml` - Kustomize file for Flux installation.</li>
</ul>

## Authors

* **Nikita Evdokimov** - *Initial work* - [DrPalmeritta](https://github.com/DrPalmeritta)
