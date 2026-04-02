# Biren Device Plugin

## Deployment

### Label the Node with `birentech.com=gpu`
```bash
kubectl label node {biren-node} birentech.com=gpu
```

### Deploy `biren-device-plugin`


```bash
kubectl apply -f deploy/biren-device-plugin.yaml
```

### Usage

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod1
spec:
  restartPolicy: OnFailure
  containers:
    - image: ubuntu
      name: pod1-ctr
      command: ["sleep"]
      args: ["infinity"]
      resources:
        limits:
          birentech.com/gpu: 1
```