# Istructions: Running Containers in K8s with Pods and Deployments

- Write a Kubernetes YAML file to create a deployment to run an application in a Pod. the Pod runs the container using the image 'kiamol/cha02-whoami'.
-  Forward the traffic from the port 80 to 8080. 

# Solution Steps
kubectl apply -f deployment.yaml

kubectl port-forward deploy/whoami 8080:80

curl http://localhost:8080

> "I'm whoami-6f57ff87df-cq6s6 running on Linux 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2"

kubectl get pods -o custom-columns=NAME:metadata.name

> whoami-6f57ff87df-cq6s6

kubectl exec deploy/whoami -- sh -c 'hostname'

> whoami-6f57ff87df-cq6s6
