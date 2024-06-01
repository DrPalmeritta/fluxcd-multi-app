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

`apps/` - Directory for applications.<br />
`(space)(space)` `production-app/, keycloak/, monitoring-app/` - Directories for each application.<br />
`(space)(space)` `base/` - Contains common manifests and customizations applied to all environments.<br />
`(space)(space)(space)(space)`- `kustomization.yaml` - A Kustomize file describing the resources to be enabled.<br />
`(space)(space)(space)(space)`- `deployment.yaml` - A sample deployment manifest.<br />
`(space)(space)` `overlays/` - Contains environment-specific customizations.<br />
`(space)(space)` `dev/ and prod/` - Directories for different environments.<br />
`(space)(space)(space)(space)` - `kustomization.yaml` - The Kustomize file for the given environment.<br />
`(space)(space)(space)(space)` - `patch.yaml` - A patch to change the configuration specific to this environment.<br />

`clusters/` - The directory for the clusters.<br />
`(space)(space)` `dev/ and prod/` - Directories for the various clusters.<br />
`(space)(space)(space)(space)` - `kustomization.yaml` - Kustomize file to apply applications to this cluster.<br />
`(space)(space)(space)(space)` - `apps.yaml` - Application manifests for this cluster.<br />

`flux/` - The directory for installing FluxCD.<br />
`(space)(space)` - `gotk-components.yaml` - Flux components.<br />
`(space)(space)` - `gotk-sync.yaml` - Flux synchronization configuration with the repository.<br />
`(space)(space)` - `kustomization.yaml` - Kustomize file for Flux installation.<br />

## Authors

* **Nikita Evdokimov** - *Initial work* - [DrPalmeritta](https://github.com/DrPalmeritta)
