# kubectl-assume-sa

A kubectl plugin that allows you to assume a Kubernetes ServiceAccount by extracting its token from a running pod and generating a kubeconfig for direct access.

## What does it do?

This script:

1. **Extracts the ServiceAccount token** from a running pod (from `/var/run/secrets/kubernetes.io/serviceaccount/token`)
2. **Retrieves cluster information** including the real API server endpoint and CA certificate
3. **Generates a kubeconfig file** that allows you to authenticate as that ServiceAccount
4. **Optionally launches kubie** for an isolated shell session with the ServiceAccount context

This is useful for:
- Testing ServiceAccount permissions
- Debugging RBAC issues
- Understanding what a pod can/cannot do in the cluster
- Development and troubleshooting

## Prerequisites

### Required
- `kubectl` - Kubernetes command-line tool
- Access to a Kubernetes cluster where you have permissions to:
  - Copy files from pods (`kubectl cp`)
  - Read ConfigMaps in `kube-system` and `kube-public` namespaces
  - Get pod information

### Optional
- [kubie](https://github.com/sbstp/kubie) - For isolated context switching and better namespace management

## Installation

### Install as kubectl plugin (via krew)

```bash
kubectl krew install assume-sa
