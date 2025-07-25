## Configuring values.yaml file

1. Build the docker images and upload them to a docker registry.
   - If you are using a private registry, ensure that the images are accessible from your Kubernetes cluster.
   - If you are using Docker Hub, ensure that the images are tagged correctly.

2. Create a docker pull secret.

3. Add details to pull the docker image
   ```
   registry: ""
   repository: ""
   tag: ""
   imagePullSecret: "" 
   ```
4. Create server certificates, add them to the trustores and keystores, and mount them to the containers.
   - Ensure that the certificates are valid and trusted by the clients that will connect to the services.
   - To mount the truststore and keystore, create a secret using the truststore and keystore files and reference it in the `values.yaml` file.
   
   ```
   externalJKS:
      # -- Mount external  keystore and trustores
      enabled: true
      # -- K8s secret name which contains JKS files
      secretName: "keystores"
   ```
5. Configure the port offset for Identity Server

   ```
   server:
      # -- Change default ports(Ref: https://is.docs.wso2.com/en/latest/references/default-ports-of-wso2-products/#:~:text=For%20each%20additional%20WSO2%20product,to%20the%20server%20during%20startup.)
      offset: "3"
   ```
   
6. Configure the Identity Server super admin username and password.

   ```
   superAdmin:
      # -- Carbon console admin account username
      username: "is_admin@wso2.com"
      # -- Carbon console admin account password
      password: "wso2123"
   ```
   
7. Configure database hostname, username and password for all the databases.
8. Configure the financial services configurations as required. You can refer the documentation for more information on the configurations.
   - The configurations can be found in the `values.yaml` file under the `financial_services` section.
   - Ensure that the configurations are valid and match your requirements.