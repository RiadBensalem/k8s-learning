# Instructions: Scaling Application Across Multiple Pods With Controllers

We have two componant WEB and API, used in an app that generates random numbers. Two services are also provided: a clusterIP for the API and a LoadBalancer for the WEB.
 - Add a controller that supports high load for the web componant. (basically asking to use a Deployment)
 - Insure high avalability for the API (a DeamonSet will make it available in every node in the k8s cluster). This componant works only on specific nodes with special hardware(we mimic this scenario by adding the label `rng=hw` to a node). 



# Solution Steps

The solution steps are:
 - Change the provided web.yaml manifest from a `ReplicationController` to a `Deployment`.
 - Change the provided api.yaml manifest from a `Pod` to a `DeamonSet` with a condition to run only on node with the label `rng=hw`.
 - Add label `rng=hw` to node(s).

Adding label to node:
> kubectl label nodes NODE-NAME rng=hw


> kubectl get nodes --show-labels

And then:

> kubectl apply -f numbers

To test the result:

> kubectl get svc numbers-web -o jsonpath='http://{.status.loadBalancer.ingress[0].*}:8086'

And browse to the prompted URL.

To clean up:

> kubectl delete all -l kiamol=ch06-lab

> kubectl label --overwrite nodes NODE-NAME rng-
