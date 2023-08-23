# Istructions: Connecting Pods over the network with Services

 - Deploy the random number app using the deployment.yaml manifest.
 - Check there is two versions of the app running.
 - Write a service that  will make version 2 available externally on port 8088.


# Solution Steps

Reading the Chapter 03 of the book, allows to understant that the web container calls the api container to generate a random number, thus:
 - First deploy the Pods:
 > kubectl apply -f deployment.yaml
 - Check for the pods:
 > kubectl get pods 
 - We need to create a ClusterIP service to enable communication between the web app and the api.
 - Create a second service of type LoadBalancer to enable communication from external to web app.

 > kubectl apply -f service.yaml

 > kubectl get svc

 > Check the app in browser: localhost:8088  
