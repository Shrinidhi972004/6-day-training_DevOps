Kubernetes Commands & Concepts (Day 6) 🧑‍💻
Managing Namespaces 🌐
Kubernetes allows you to partition a cluster into multiple isolated environments using Namespaces.

🔹 List namespaces:
kubectl get namespace
🔹 Show all resources in kube-system namespace:
kubectl get all -n kube-system
🔹 Create a custom namespace:
kubectl create ns shrinidhi
🔹 List all namespaces:
kubectl get ns
Running Pods in a Namespace 🚀
🔹 Run a pod in the custom namespace shrinidhi using the nginx image:
kubectl run test-pod --image=nginx --port=80 -n shrinidhi
🔹 Check if the pod was created in the shrinidhi namespace:
kubectl get pods -n shrinidhi
🔹 Delete the pod:
kubectl delete pod test-pod -n shrinidhi
Replica Set (rs.yaml) 🔄
🔹 Clone the repository to get rs.yaml:
git clone https://github.com/Shrinidhi972004/Shrinidhi-k8s-manifests.git
🔹 Apply the ReplicaSet configuration:
kubectl apply -f rs.yaml
🔹 Check the status of Pods and ReplicaSets:
kubectl get pods -n shrinidhi
kubectl get rs -n shrinidhi
🔹 If a Pod is pending, check the detailed description:
kubectl describe pod -n shrinidhi <pod-name>
🔹 Delete the ReplicaSet:
kubectl delete rs cart-page-rs -n shrinidhi
Deployments 🚀
🔹 Deploy using a deployment.yaml file:
kubectl apply -f deployment.yaml -n shrinidhi
🔹 Check the deployment and pod status:
kubectl get deployments -n shrinidhi
kubectl get pods -o wide -n shrinidhi
Services 🌐
🔹 Create a Service to expose the application:
kubectl apply -f service.yaml
🔹 If you face issues with resources, specify the namespace:
kubectl apply -f name.yaml -n shrinidhi
🔹 Get the URL to access the service (use with port number):
kubectl get svc -n shrinidhi


Kubernetes Core Concepts 📚
🔸 What is a Namespace? 🌏
A Namespace is a way to divide your cluster into isolated environments. It's useful when deploying multiple projects, ensuring they do not interfere with each other.
⚠️ Never deploy applications in the default namespace for production environments.
Pod Failure Management ⚠️
Problems & Solutions:
Application Downtime: Attach controllers like ReplicaSets or Deployments to maintain high availability.

IP Address Changes: Use Kubernetes Services for stable access.

Data Loss: Attach persistent volumes to pods to ensure data durability.

ReplicaSet 🔄
Ensures that a specified number of pod replicas are always running.

✅ Good for maintaining pod count

❌ Not ideal for rollouts or rollbacks → use Deployments instead

Deployments 🎯
Higher-level abstraction over ReplicaSet

Supports rolling updates, rollbacks, and complete lifecycle management

Kubernetes Services 🛠️
Types:

ClusterIP – Internal-only exposure within the cluster

NodePort – External access via static port on each node

LoadBalancer – Exposes externally using a cloud provider’s load balancer

Monitoring Kubernetes Applications 📊
Prometheus:

Collects and stores time-series metrics

Grafana:

Visualizes metrics in dashboard format

Shows CPU, memory, and node health insights

Configuration Management 🔧
Ansible:

Automates Kubernetes resource setup, config, and deployment tasks.


