# Build Docker container
    docker build . -t helmplay:v1 

# Run Docker container with some environment variables and port mapping
    docker run -it -e "APPENVIRONMENT=new-env" -e "APPHOST=macbookpro" -p 9000:80 helmplay

# List all available kunbectl contexts
    kubectl config get-contexts

# Change kubectl context to Docker Desktop
    kubectl config use-context docker-desktop

# Deploy helm chart
    helm install helmplayrelease ./chart/  

# Get all deployed resourced for a label
    kubectl get all --selector app=helmplay

# Map service cluster port to machine host port. Host_port:Cluster_port
    kubectl port-forward service/helmplayrelease-service 9999:8888

# Change helm deployment environment
    helm upgrade helmplayrelease ./chart --values ./chart/values-prod.yaml
