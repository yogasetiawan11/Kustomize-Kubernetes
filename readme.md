# What is Kostumize 
Kustomize is a native kubernetes configuration. think of it like ansible configuration management tool for linux. 

Imagine you have different virtual machine on the cloud provider and you have requirement to install nginx on all the virtual machine, but one of the virtual machine require different version of nginx. With configuration management tool you can install it without login to the machines manually.

Similarly, in Kubernetes, you deal with many types of resources such as ``Deployments``, ``ConfigMaps``, ``StatefulSets``, ``Secrets``, and more.
Across different projects, you might use different namespaces, labels, or slightly different configurations.

Kustomize helps you manage these variations by allowing you to create base configurations and then apply overlays for specific environments or projects (for example, dev, staging, production). This keeps your Kubernetes manifests clean, reusable, and easy to maintain.