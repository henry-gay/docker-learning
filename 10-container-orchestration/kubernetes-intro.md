# Introduction to Kubernetes

## What is Kubernetes?
Kubernetes is an open-source container orchestration system that allows you to deploy, scale, and manage containerized applications efficiently.

With **Docker**, you can run a single instance of an application using:
```sh
docker run my-app
```
With **Kubernetes**, you can run **1,000 instances** of the same application with a single command. You can then:
- **Scale up or down** automatically based on load.
- **Perform rolling upgrades** to update instances without downtime.
- **Roll back updates** if something goes wrong.
- **Conduct A/B testing** by upgrading a percentage of instances.
- **Integrate with multiple networking and storage providers.**

All major cloud providers support Kubernetes natively, making it a highly flexible and scalable solution for managing containers.

---

## Kubernetes and Docker
Kubernetes uses **Docker hosts** to run applications inside **Docker containers**. However, Kubernetes also supports other container runtimes like **Rocket (rkt)** and **CRI-O**.

---

## Kubernetes Architecture
A **Kubernetes Cluster** consists of multiple components that work together to manage containers.

### **Nodes**
A **node** is a machine (physical or virtual) that runs Kubernetes. Nodes are responsible for hosting and running containers.
- If a **node fails**, the containers running on it become unavailable.
- To ensure **high availability**, multiple nodes are grouped into a **cluster**.

### **Master Node (Control Plane)**
The **master node** is responsible for managing the cluster. It contains:

#### **1. API Server**
- Acts as the **front-end** for Kubernetes.
- CLI tools and other management applications interact with Kubernetes through the API server.

#### **2. etcd (Key-Value Store)**
- A **distributed database** that stores all cluster state information.
- Ensures consistency across multiple nodes and masters.
- Handles **locking mechanisms** to prevent conflicts.

#### **3. Scheduler**
- Assigns containers to available nodes based on resource availability.
- Ensures **balanced workloads** across the cluster.

#### **4. Controllers**
- The **brain** behind orchestration.
- Detects failures (nodes, containers, services) and **restarts workloads** automatically.

#### **5. Kubelet (Agent on Each Node)**
- Ensures that the expected containers are running on each node.
- Reports node and container health back to the master.

#### **6. Container Runtime (e.g., Docker)**
- Runs and manages containers inside Kubernetes.

---

## Managing Kubernetes with `kubectl`
The **kubectl** command-line tool is used to deploy and manage applications in Kubernetes.

### Common `kubectl` Commands:
- Deploy an application:
  ```sh
  kubectl run my-app --image=my-image
  ```
- View cluster information:
  ```sh
  kubectl cluster-info
  ```
- List all nodes in the cluster:
  ```sh
  kubectl get nodes
  ```

---

## Summary
- **Kubernetes automates deployment, scaling, and management** of containerized applications.
- **Clusters consist of multiple worker nodes**, managed by a **master node**.
- **API Server, etcd, Scheduler, and Controllers** manage the cluster.
- **kubectl** is the CLI tool for interacting with Kubernetes.

Kubernetes is a powerful orchestration tool with extensive capabilities. Next, we will explore Kubernetes deeper and learn how to deploy applications efficiently!