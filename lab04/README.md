# Istructions: Configuring applications with ConfigMaps and Secrets

 - Deploy a `Postgres` database using the YAML files in the postgres folder.
 - Deploy [Adminer](https://www.adminer.org/) using adminer.yaml.
 - Check that Adminer is running by identifing first the external IP and use the port `8082` in a browser.
 - Use `postgres` as username and database name to check the connection. You need to identify the database server address as well. (To get the password to you need to invesigate a bit)
 - Use the environment variable  `ADMINER_DEFAULT_SERVER` to the default database server. Treat this as sensitive informtion and use `Secret`.
 - To change the UI of Adaminer trefers to the environment variable  `ADMINER_DESIGN`. the value `price` loads a different UI.

# Solution Steps

 > kubectl deploy -f postgres/

 > kubectl apply -f adminer.yaml

- To check the external IP of the Adminer app, we need to look for the service exposing it: a LoadBalancer. The command below will show the services running, look for the one related to Adminer.
 > kubectl get svc

 > Check the app in browser: ExternalIP:8082

 - One way to complete from here, is to create a manifest to define the configMap and the Secret and modify the `adminer.yaml` file to take in consideration the ENV variables.

 > kubectl apply -f adminer-configMap.yaml

 > kubectl apply -f adminer-secrets.yaml

 > kubectl get cm 

 > kubectl get secret

 > kubectl apply -f adminer.yaml

 
 
 __PS__: It is not a good idea to add sensitive information to source control but since this just for learning purposes I kept the values of the secret and postgres password. 