
======================How to create Docker Image===================================
- Enable Docker Support while creating  Asp.NET Core Project
- Deploy in Release Mode
- Build with Docker in VS or Run docker build -t myimage -f Dockerfile . on Terminal

======================Checking All Docker Images===================================
- Run Docker Images

======================Changing Tag for Deployment===================================
- Run docker image tag edutechdocker:latest edutechdocker:1.0

======================Deployment and Service Extension===================================
- Download Kubernetes Extension on VS Code
- Download YAML Extension on VS Code

======================Deployment.Yaml File===================================

apiVersion: apps/v1
kind: Deployment
metadata:
  name: joshdarkmode-deployment
spec:
  selector:
    matchLabels:
      app: joshdarkmode-pod
  template:
    metadata:
      labels:
        app: joshdarkmode-pod
    spec:
      containers:
      - name: joshdarkmode-container
        image: joshdarkmode:latest
        resources:
          limits:
            memory: "128Mi"
            cpu: "500m"
        ports:
        - containerPort: 80
       
  - Run kubectl apply -f  deployment.yaml
  - Run kubectl get deployments
  
  ======================Service.Yaml File===================================
  apiVersion: v1
kind: Service
metadata:
  name: joshdarkmode-service
spec:
  selector:
    app: joshdarkmode-pod
  ports:
  - port: 8080
    targetPort: 80
  type: LoadBalancer
  
  - Run kubectl apply -f  service.yaml
  - Run kubectl get services
  
  Finally Your App is Ready on Kubernetes
