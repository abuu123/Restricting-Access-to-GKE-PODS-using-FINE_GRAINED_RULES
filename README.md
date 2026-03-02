# Restricting-Access-to-GKE-PODS-using-FINE_GRAINED_RULES
kubectl get nodes

##Deploy Sample Applications
kubectl apply -f ~/manifests/hello-app/hello-server.yaml
kubectl apply -f ~/manifests/hello-app/hello-client.yaml

##Check pods:
kubectl get pods

##Test Pod Connectivity (Default – No Network Policy)

Inside the client Pod:
kubectl exec -it <hello-client-pod> -- curl http://hello-server

##Apply Fine-Grained Network Policies
Use the namespaced network policy YAML you have:
kubectl apply -f ~/manifests/network-policy-namespaced.yaml

##Verify Network Policy Enforcement
Try connecting again from the client Pod:
kubectl exec -it <hello-client-pod> -- curl http://hello-server

##To see applied network policies:
kubectl get networkpolicies --all-namespaces
kubectl describe networkpolicy <policy-name>


