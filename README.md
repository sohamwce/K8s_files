# Kubernetes Configuration Files

## 1. Pod Configuration
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

## 2. Deployment Configuration
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
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
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

## 3. Amazon Books Service Configuration
```yaml
apiVersion: v1
kind: Service
metadata:
  name: amazon-books-service
spec:
  type: LoadBalancer
  selector:
    app: amazon-books
  ports:
    - protocol: TCP
      port: 80       # External port
      targetPort: 80  # Port inside the Pod.
```

## 4. Backend Service Configuration
```yaml
apiVersion: v1
kind: Service
metadata:
  name: backend-service
spec:
  selector:
    app: backend
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
  type: ClusterIP
```

