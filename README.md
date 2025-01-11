# Ansible Project with Cross-Stack CloudFormation and Automation

## Project Overview

This project demonstrates the integration of AWS CloudFormation and Ansible to create and configure an infrastructure that adheres to best practices. It consists of two primary 
CloudFormation templates:

1. **VPC Template**: Defines a Virtual Private Cloud (VPC) with exported subnets and security groups.
2. **Cluster Template**: Imports the VPC resources and launches 5 instances:
   - 2 Amazon Linux nodes.
   - 3 Ubuntu nodes, including 1 controller and 2 worker nodes.

## Key Features

### Cross-Stack References
- Used cross-stack references to link the VPC and Cluster templates.
- Exported VPC subnets and security groups from the VPC template to be imported in the Cluster template.

### Best Practices in CloudFormation
- Parameters, resources, and outputs are defined, avoiding hardcoding values.
- Sensitive data is managed using SSM Parameters.

### Ansible Automation
- Ansible playbook is designed to:
  - Configure Apache on both Ubuntu and Amazon Linux nodes in a single play.
  - Follow best practices by combining tasks efficiently and ensuring idempotency.
- Playbook executes configurations without requiring agent installation on the nodes.

### Tools and Technologies
- **GitHub**: Version control system for storing and managing template and playbook versions.
- **CloudFormation**: Infrastructure as Code (IaC) tool for provisioning AWS resources with minimal manual intervention.
- **AWS CodePipeline**: Orchestrates the deployment process with GitHub as the source and CloudFormation as the target.
- **Ansible**: Configures the infrastructure and ensures it remains consistent and idempotent.

## Upcoming Steps

The next phase of the project involves:
1. **Automating Deployment**:
   - Setting up a 3-stage deployment pipeline using AWS CodePipeline.
   - Storing the source code in GitHub and deploying it to AWS using CloudFormation templates.
2. **Apache Configuration**:
   - Using Ansible to configure Apache on the nodes provisioned by the pipeline.

This combination is effective because:
- **GitHub** allows version control and collaboration.
- **CloudFormation** provides repeatable and reliable infrastructure provisioning.
- **AWS CodePipeline** automates and orchestrates deployments.
- **Ansible** configures and manages infrastructure effortlessly, being agentless and idempotent.
