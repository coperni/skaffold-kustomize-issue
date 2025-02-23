# Information

- Skaffold version: v2.14.0
- Operating system: macOS 15.3.1 (24D70)
- Installed via: curl w/ latest stable binary

# Issue


### ✅ Success
This command renders successfully for the profile `dev` and `prod`:

```bash
skaffold render -p prod
```

Result:
```yaml
apiVersion: v1
data:
  foo: bar!
kind: ConfigMap
metadata:
  name: prod-example-map
---
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: myapp
  name: prod-myapp-pod
spec:
  containers:
    - image: nginx:123
      name: nginx
```

### ❌ Failure
If a key-value pair is provided, the command fails:

```bash
skaffold render -p prod --set="a=b"
```

Error:
```bash
read /Users/REDACTED/tmp/kustomize_example/overlays/prod: is a directory
```
