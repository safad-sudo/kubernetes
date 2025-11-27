# How to Create a Namespace

### First create a namespace manifest file

```bash
vim namespace.yml
```

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: my-app
```

# Next Creating Deployment yaml file

```bash
vim deployment.yml
```
### Past This Code

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deploy
  namespace: my-app
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: my-nginx
        image: nginx:alpine
        ports:
          - containerPort: 80
```

# Next Creating ReplicaSet Yaml File

```bash
vim replicas.yml
```

### Past This Code

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-rep
  namespace: my-app
  labels:
    app: niginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: my-nginx
        image: nginx:alpine
        ports:
          - containerPort: 80
```

# Next Creating DaemonSety aml file

```bash
vim daemons.yml
```

### Past This Code

```yml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: nginx-daemon
  namespace: my-app
spec: 
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: my-nginx
        image: nginx:alpine
        ports:
          - containerPort: 80
```
