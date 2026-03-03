# Helm Testing Guide

## Running Tests

### Basic Test Execution

```bash
# Install the chart
helm install camel-dashboard camel-dashboard/camel-dashboard-openshift-all \
  -n camel-dashboard --create-namespace

# Run all tests
helm test camel-dashboard -n camel-dashboard
```

### Test Dry-Run

```bash
helm install  camel-dashboard camel-dashboard/camel-dashboard-openshift-all \
  -n camel-dashboard --create-namespace --set "hawtio-online-console-plugin.mockProxySecret"=true --dry-run
```

## Viewing Test Results

### List Test Pods

```bash
kubectl get pods -n camel-dashboard -l "helm.sh/hook=test"
```

### View Individual Test Logs

```bash
# Helm release test (always runs)
kubectl logs -n camel-dashboard <release-name>-test-helm-release

# Operator test (if enabled)
kubectl logs -n camel-dashboard <release-name>-test-operator

# Console test (if enabled)
kubectl logs -n camel-dashboard <release-name>-test-console

# Hawtio test (if enabled)
kubectl logs -n camel-dashboard <release-name>-test-hawtio

# Integration test
kubectl logs -n camel-dashboard <release-name>-test-integration
```

### View All Test Logs

```bash
# View logs from all test pods
for pod in $(kubectl get pods -n camel-dashboard -l "helm.sh/hook=test" -o name); do
  echo "=== $pod ==="
  kubectl logs -n camel-dashboard $pod
  echo ""
done
```

## Troubleshooting

### Test Pod Fails to Start

Check if image can be pulled:
```bash
kubectl describe pod <release-name>-test-operator -n camel-dashboard
```

### Manually Run a Test

```bash
# Delete existing test pod
kubectl delete pod <release-name>-test-operator -n camel-dashboard

# Helm will recreate and run it
helm test <release-name> -n camel-dashboard
```
