# k8s-pdb-scaler

# Kubernetes Controller and Webhook for PDB Monitoring and Scaling to Manage Pod Evictions

## Name: Javier Garcia

## Project Overview
This project aims to create a Kubernetes controller with a webhook that monitors Pod Disruption Budgets (PDBs) to ensure that pod eviction constraints are met and automatically scales the associated Deployments or StatefulSets when necessary. The controller will work with a webhook to dynamically adjust resources in response to the constraints imposed by the PDB during disruptions.
