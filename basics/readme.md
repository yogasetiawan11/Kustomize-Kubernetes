## Kustomize Basics
This section is the fundamental concepts of Kustomize:

- How to organize your Kubernetes configurations
- How to make simple changes without touching the original files
- Understanding base and overlay structure
Directory Structure
.
├── base/                  # Your original configuration
│   ├── deployment.yaml    # A basic nginx deployment
│   └── kustomization.yaml # Tells Kustomize what to include
└── overlay/              # Your customizations
    └── kustomization.yaml # Defines how to modify the base

## Understanding the Files
### Base Configuration
The base/ directory contains your original, unchanged - configuration:

- deployment.yaml: A simple nginx web server deployment
- kustomization.yaml: Lists which files to include
### Overlay Configuration
The overlay/ directory shows how to customize the base:

Adds a prefix to all resources (dev-)
Updates the nginx image version to 1.20
Adds environment labels

## Try the commands
View the base deployment:
```sh
kubectl kustomize base/
```
View the customized version:
```sh
kubectl kustomize overlay/
```
Apply to your cluster:
```sh
kubectl apply -k overlay/
```
What's Happening?
1. Kustomize reads the base configuration
2. It applies the changes specified in the overlay:
- Adds "dev-" prefix to names
- Updates the nginx image
- Adds environment labels
- Generates the final configuration

### Key Concepts
- Base: Your original configuration
- Overlay: Your customizations
- kustomization.yaml: Tells Kustomize what to do
- Resources: The Kubernetes files you want to modify