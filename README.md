# k8s-pdb-scaler

# Kubernetes Controller and Webhook for PDB Monitoring and Scaling to Manage Pod Evictions

## Name: Javier Garcia

## Project Overview
This project aims to create a Kubernetes controller with a webhook that monitors Pod Disruption Budgets (PDBs) to ensure that pod eviction constraints are met and automatically scales the associated Deployments or StatefulSets when necessary. The controller will work with a webhook to dynamically adjust resources in response to the constraints imposed by the PDB during disruptions.

## Objectives
1. **Monitor PDBs and Pod Evictions:**
   - **Controller:** Continuously watch PDBs and their associated pods to detect when evictions are blocked. Ensure the controller accurately identifies the disruption state without causing unnecessary scaling actions.
   - **Webhook:** Intercept pod eviction requests to determine if evictions are being blocked due to `DisruptionsAllowed` being zero as `DisruptionsAllowed` allowed could be 0 as a desired state, annotate accordingly.

2. **Automate Scaling:**
   - **Controller:** Automatically scale Deployments or StatefulSets when necessary, specifically when evictions are blocked due to `DisruptionsAllowed` being zero and an actual eviction attempt is detected from the webohook.
   - **Webhook:** Provide real-time information about eviction attempts, allowing the controller to make immediate scaling decisions, and to prevent scaling decisions that are against what the author of deployment and pdb is trying to tell you.

3. **Generate Events and Update Status:**
   - **Controller:** Produce events or update the status of PDBs to notify cluster administrators about scaling actions taken. Generate events when scaling occurs and update annotations to reflect current states.
   - **Webhook:** Log events or update the status of PDBs or pods when eviction attempts are blocked.

4. **Efficient Resource Management:**
   - **Controller:** Avoid unnecessary scaling actions that could lead to resource wastage or application downtime.
   - **Webhook:** Provide detailed insights into eviction attempts and PDB statuses, ensuring that the controller only scales resources when truly necessary.
  
