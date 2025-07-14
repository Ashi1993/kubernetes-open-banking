# WSO2 API Manager Deployment Patterns

This directory contains documentation and sample values for deploying WSO2 API Manager in various deployment patterns using Helm charts. Each subdirectory represents a different deployment pattern with specific configuration options and deployment topologies.

## Overview

WSO2 API Manager is a complete solution for designing and publishing APIs, creating and managing a developer community, and for securing and monetizing APIs. It offers various deployment options to suit different organizational needs, from simple all-in-one deployments to complex distributed architectures.

## Available Deployment Patterns

### Pattern 2: All-in-One with Separate Gateway
- **Directory**: `am-pattern-2-all-in-one_GW`
- **Description**: Deployment with separate gateway nodes and a control plane
- **Use Case**: Environments with higher API traffic needing gateway scalability
- **Components**: API Control Plane, Universal Gateways
- **Resources**: [README](am-pattern-2-all-in-one_GW/README.md), [Sample Control Plane Values](am-pattern-2-all-in-one_GW/default_values.yaml), [Sample Gateway Values](am-pattern-2-all-in-one_GW/default_gw_values.yaml)

## How to Use

Each pattern directory contains:
1. A detailed README.md with deployment instructions
2. Sample values.yaml files for configuring the Helm deployment
3. Documentation on prerequisites and configuration options

### General Steps for Deployment:

1. **Prerequisites**:
   - Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git), [Helm](https://helm.sh/docs/intro/install/), and [Kubernetes client](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
   - Set up a [Kubernetes cluster](https://kubernetes.io/docs/setup)
   - Install [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/deploy/)
   - Add the WSO2 Helm chart repository: `helm repo add wso2 https://helm.wso2.com && helm repo update`

2. **Build Docker Images**:
   - Use WSO2 product Docker images from [DockerHub](https://hub.docker.com/u/wso2/) or [WSO2 Private Docker Registry](https://docker.wso2.com/)
   - Include necessary JDBC drivers and customizations in your Docker images

3. **Configuration**:
   - Configure ingress controller
   - Set up databases
   - Configure keystores and truststores
   - Update Helm chart values

4. **Deployment**:
   - Follow the pattern-specific deployment instructions

## Deploy on Kubernetes

The Helm charts include cloud provider-specific configurations for:
- AWS (EKS, EFS, RDS, Secrets Manager)
- Azure (AKS, Azure Files, Azure Database, Key Vault)
- GCP (GKE, GCS, Cloud SQL, Secret Manager)

## Deploy on OpenShift

- **Note:** Default Helm chart configurations are intended for Kubernetes deployment.  
- If you are deploying on OpenShift, additional configurations are required for both Docker images and the deployment process. For comprehensive instructions, refer to the [OpenShift Deployment Guide](openshift_deployment.md).

## Additional Resources

- [WSO2 API Manager Documentation](https://apim.docs.wso2.com/)
- [WSO2 Helm Charts Repository](https://github.com/wso2/helm-apim/)
- [WSO2 Updates](https://wso2.com/updates/)
- [WSO2 Subscription](https://wso2.com/subscription/)
