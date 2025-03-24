# Docker Swarm

## Introduction to Docker Swarm
Docker Swarm allows you to combine multiple Docker hosts into a single cluster for **high availability** and **load balancing**. It provides native **container orchestration** in Docker, enabling easier management of distributed applications.

---

## Setting Up a Docker Swarm Cluster
### **1. Prepare Docker Hosts**
- Install Docker on multiple hosts.
- Designate one host as the **Swarm Manager** and others as **Worker Nodes**.

### **2. Initialize the Swarm Manager**
Run the following command on the manager node:
```sh
docker swarm init
```
This command initializes the Swarm Manager and provides a token to join worker nodes.

### **3. Join Worker Nodes**
On each worker node, run the command provided by the `docker swarm init` output:
```sh
docker swarm join --token <TOKEN> <MANAGER-IP>:2377
```
Once joined, worker nodes become **Swarm Nodes**, ready to run containerized services.

---

## Running Services in Docker Swarm
Unlike standalone containers, Docker Swarm uses **services** to deploy applications.

### **Creating a Service**
To deploy multiple instances of a web server, run:
```sh
docker service create --name my-web-server --replicas 3 -p 80:80 nginx
```
This command:
- Creates a service named **my-web-server**.
- Runs **3 replicas** of the `nginx` container.
- Distributes them across available worker nodes.

### **Key Differences: `docker run` vs. `docker service create`**
| Feature         | `docker run` | `docker service create` |
|---------------|-------------|------------------|
| Runs a single container | ✅ | ❌ |
| Deploys across multiple nodes | ❌ | ✅ |
| Provides load balancing | ❌ | ✅ |
| Auto-restarts failed containers | ❌ | ✅ |

---

## High-Level Swarm Features
- **Automated Load Balancing**: Distributes traffic between containers.
- **Self-Healing**: Automatically restarts failed containers.
- **Scaling**: Easily scale services up or down with:
  ```sh
  docker service scale my-web-server=5
  ```
- **Rolling Updates**: Deploy new versions with minimal downtime.

---

## Summary
- **Docker Swarm turns multiple hosts into a container cluster.**
- **Swarm Manager coordinates worker nodes.**
- **Docker Services run and scale applications across nodes.**
- **Built-in load balancing and self-healing for high availability.**

Docker Swarm is an easy-to-use orchestration tool, but for more advanced deployments, Kubernetes is often preferred. Next, we will explore Kubernetes at a high level!
