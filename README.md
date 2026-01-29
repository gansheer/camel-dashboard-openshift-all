# Camel Dashboard All-in-One Helm Chart

This is an umbrella Helm chart that deploys the complete Camel Dashboard solution, including:
- **Camel Dashboard Operator**: Manages Camel Dashboard instances
- **Camel Dashboard Console**: OpenShift Console plugin for Camel Dashboard
- **Hawtio Online Console Plugin**: Management and monitoring console for Java applications

## Prerequisites

- Kubernetes
- Helm
- OpenShift 4.19+

## Installation

### 1. Add the Helm Repository

```bash
helm repo add camel-dashboard https://camel-tooling.github.io/camel-dashboard/charts
helm repo update
```

### 2. Install the Chart

```bash
helm install camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard --create-namespace
```
### 2. Install the Chart

```bash
helm install camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard --create-namespace
```

### 3. Customizing Installation

You can customize the installation by providing your own values:

```bash
helm install camel-dashboard-openshift-all camel-dashboard/camel-dashboard-openshift-all -n camel-dashboard --create-namespace -f my-values.yaml
```

## Uninstalling

```bash
helm uninstall camel-dashboard-openshift-all -n camel-dashboard
```


## More Information

- [Camel Dashboard Documentation](https://camel-tooling.github.io/camel-dashboard/)
- [Camel Dashboard Repository](https://github.com/camel-tooling/camel-dashboard)
- [Camel Dashboard Operator](https://github.com/camel-tooling/camel-dashboard-operator)
- [Camel Dashboard Console](https://github.com/camel-tooling/camel-dashboard-console)
- [Hawtio Console Plugin](https://github.com/hawtio/hawtio-online)
- [Apache Camel](https://camel.apache.org/)