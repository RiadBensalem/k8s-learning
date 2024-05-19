# Instructions: Storing Data with Volumes, Mounts and Claims

 - Deploy the todo-list app manifest.
 - Get the LoadBalancer service URL, and check the logs for investigation.
 - Configure persistant storage for the proxy cache (nginx) and the database in web pod.
 - The goal is to be able to, add an item to a todo-list, delete the pods and see that the data persists. 


# Solution Steps

The solution I chose is to:
 - Use `HostPath` to store the Proxy cache files at the level of the node. config can be found in `proxy.yaml`.
 - Declare a `PersistantVolumeClaim` that the web container will use for the database. This uses a dynamic provisioning that creates a `PersistantVolume` once I run the web Pod.

The `PersistantVolumeClaim` definition:
> kubectl apply -f pvc.yaml 

> kubect get pvc

And then:

> kubectl apply -f todo-list/

> kubectl get pv
