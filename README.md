# k8s-pdb-scaler

# Kubernetes Controller and Webhook for PDB Monitoring and Scaling to Manage Pod Evictions

## Name: Javier Garcia

## Project Overview
This project aims to create a Kubernetes controller with a webhook that monitors Pod Disruption Budgets (PDBs) to ensure that pod eviction constraints are met and automatically scales the associated Deployments or StatefulSets when necessary. The controller will work with a webhook to dynamically adjust resources in response to the constraints imposed by the PDB during disruptions.

## Objectives
1. **Monitor PDBs and Pod Evictions:**
   - **Controller:** Continuously watch PDBs and their associated pods to detect when evictions are blocked. Ensure the controller accurately identifies the disruption state without causing unnecessary scaling actions.
   - **Webhook:** Intercept pod eviction requests to determine if evictions are being blocked due to `DisruptionsAllowed` being zero, and annotate the PDB or pod accordingly.

2. **Automate Scaling:**
   - **Controller:** Automatically scale Deployments or StatefulSets when necessary, specifically when evictions are blocked due to `DisruptionsAllowed` being zero and an actual eviction attempt is detected. Ensure that scaling actions are informed and efficient.
   - **Webhook:** Provide real-time information about eviction attempts, allowing the controller to make immediate and informed scaling decisions.

3. **Generate Events and Update Status:**
   - **Controller:** Produce events or update the status of PDBs to notify cluster administrators about scaling actions taken. Generate events when scaling occurs and update annotations to reflect current states.
   - **Webhook:** Generate events or update the status of PDBs or pods when eviction attempts are blocked, providing valuable information to the controller and administrators.

4. **Efficient Resource Management:**
   - **Controller:** Make informed scaling decisions to maintain resource efficiency, avoiding unnecessary scaling actions that could lead to resource wastage or application downtime.
   - **Webhook:** Provide detailed insights into eviction attempts and PDB statuses, ensuring that the controller only scales resources when truly necessary.
  
### Milestone 1: Project Initialization and Setup
- **Deliverable 1.1: Project Repository Initialization**
  - Set up a Git repository for the project.
  - Configure the development environment with necessary tools (e.g., Kubebuilder, Go, Kubernetes client libraries).
- **Deliverable 1.2: Initial Project Structure**
  - Initialize the Kubebuilder project.
  - Define the basic directory structure for the controller and webhook.
