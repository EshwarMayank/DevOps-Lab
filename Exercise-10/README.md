# Exercise 10 – Multi-Node Kubernetes Deployment

## Objective

Deploy a Product Catalog service and a Shopping Cart service on a multi-node Kubernetes cluster using Minikube.

## Technologies Used

- Docker
- Kubernetes
- Minikube
- kubectl
- Python
- Flask

## Project Structure

Exercise-10/
├── Dockerfile.product
├── Dockerfile.shopping
├── product_catalog.py
├── shopping_cart.py
├── product_catalog_deployment.yaml
├── shopping_cart_deployment.yaml
├── product_catalog_service.yaml
├── shopping_cart_service.yaml
├── README.md
└── screenshots/

## Kubernetes Cluster

A 3-node Minikube cluster was created with the following nodes:

- devops-multinode
- devops-multinode-m02
- devops-multinode-m03

Cluster name:

devops-multinode

## Namespace

A separate namespace was created:

devops-exercise

## Product Catalog Service

The Product Catalog application is a Flask application that provides a list of products.

### Docker Image

product-catalog:latest

### Deployment

- Replicas: 2
- Container Port: 80
- Image Pull Policy: Never

### API Endpoint

/products

## Shopping Cart Service

The Shopping Cart application is a Flask application that allows items to be added to and retrieved from a shopping cart.

### Docker Image

shopping-cart:latest

### Deployment

- Replicas: 3
- Container Port: 80
- Image Pull Policy: Never

### API Endpoint

/cart

## Kubernetes Services

Both applications were exposed using Kubernetes NodePort Services.

### Product Catalog Service

product-catalog-service

### Shopping Cart Service

shopping-cart-service

## Pod Distribution

Pod anti-affinity was configured so that replicas were distributed across the available Kubernetes nodes.

The Product Catalog had 2 replicas and the Shopping Cart had 3 replicas.

All 5 pods were successfully running across the 3-node Minikube cluster.

## Verification

The following commands were used to verify the deployments:

kubectl get pods -n devops-exercise -o wide

kubectl get services -n devops-exercise

kubectl get deployments -n devops-exercise

## Product Catalog API Test

The Product Catalog service was tested using:

curl http://127.0.0.1:<PORT>/products

The API returned the product list successfully.

## Shopping Cart API Test

The Shopping Cart was initially tested using:

curl http://127.0.0.1:<PORT>/cart

The initial response was:

[]

An item was then added to the cart using:

curl -X POST http://127.0.0.1:<PORT>/cart -H "Content-Type: application/json" -d '{"id":1,"name":"Laptop","price":1200}'

The response confirmed that the Laptop was successfully added to the cart.

## Final Result

- Product Catalog Deployment: 2/2 replicas ready
- Shopping Cart Deployment: 3/3 replicas ready
- Total Pods: 5
- All Pods: Running
- Product Catalog Service: NodePort
- Shopping Cart Service: NodePort
- Services successfully connected to their respective Pods
- Product Catalog API tested successfully
- Shopping Cart GET and POST APIs tested successfully

## Screenshots

Screenshots demonstrating the deployment, service configuration, pod distribution, endpoint verification, API testing, and final Kubernetes status are included in the screenshots folder.