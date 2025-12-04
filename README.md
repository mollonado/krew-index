# mollonado's krew-index

[Krew] index repository for kubectl plugins

[Krew]: https://github.com/kubernetes-sigs/krew

## Installation

Add this custom krew index:

```bash
kubectl krew index add mollonado https://github.com/mollonado/krew-index
```

## List Available Plugins

```bash
kubectl krew search mollonado
```

## Available Plugins

### kubectl assume-sa

Assume a Kubernetes ServiceAccount identity to test RBAC permissions.

**Install:**
```bash
kubectl krew install mollonado/assume-sa
```

**Usage:**
```bash
# Assume a ServiceAccount in the current namespace
kubectl assume-sa <service-account-name>

# Assume a ServiceAccount in a specific namespace
kubectl assume-sa <service-account-name> -n <namespace>
```

### kubectl whoami

Display your current Kubernetes user identity, groups, and context.

**Install:**
```bash
kubectl krew install mollonado/whoami
```

**Usage:**
```bash
kubectl whoami
```

## Setup Instructions (for maintainers)

If you want to add a new plugin as a git submodule:

1. Add the plugin repository as a submodule:
   ```bash
   git submodule add https://github.com/mollonado/kubectl-<plugin-name> sources/kubectl-<plugin-name>
   ```

2. Create the plugin manifest in `plugins/<plugin-name>.yaml`

3. Update the index using the Makefile:
   ```bash
   make all
   ```
