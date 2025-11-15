# What is Kostumize 
Kustomize is a native kubernetes configuration. think of it like ansible configuration management tool for linux. 

Imagine you have different virtual machine on the cloud provider and you have requirement to install nginx on all the virtual machine, but one of the virtual machine require different version of nginx. With configuration management tool you can install it without login to the machines manually.

Similarly, in Kubernetes, you deal with many types of resources such as ``Deployments``, ``ConfigMaps``, ``StatefulSets``, ``Secrets``, and more.
Across different projects, you might use different namespaces, labels, or slightly different configurations.

Kustomize helps you manage these variations by allowing you to create base configurations and then apply overlays for specific environments or projects (for example, dev, staging, production). This keeps your Kubernetes manifests clean, reusable, and easy to maintain.

Structure folder For Kustomize
```yaml
.
├── base/                  # Your original configuration
│  ├── deployment.yaml     # A basic nginx deployment
│   └── kustomization.yaml # Tells Kustomize what to include
└── overlay/               # Your customizations
   └── kustomization.yaml  # Defines how to modify the base
```

## Understanding the Files
### Base Configuration
The ``base/`` directory contains your original, unchanged 
configuration:

- ``deployment.yaml``: A simple nginx web server deployment
kustomization.yaml: Lists which files to include

### Overlay Configuration
The overlay/ directory shows how to customize the base:

- ``Adds`` a prefix to all resources (dev-)
- ``Updates`` the nginx image version to 1.20
- ``Adds`` environment labels

## List command for Kustomize
View the deployment base
```bash
kubectl kustomize base/
```

View the Kustomize version
```bash

```

Apply to you Cluster
```bash
kubectl apply -k overlay/
```

## Mechanism of Kustomize 

1. Kustomize read the base configuratio
2. It apply the changes spesify in overlay
- Adds "dev-" prefix to names
- Updates the nginx image
- Adds environment labels
3. Generates the final configuration

