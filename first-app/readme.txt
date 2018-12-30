kubectl create -f helloworld.yaml
kubectl get po -w 
// if container running then
kubectl port-forward helloworld 8080:3000

// another method to run
kubectl expose pod helloworld --type=NodePort --name=hello-world-service
minikube service hello-world-service --url

curl $url
// Attach to a process that is already running inside a existing container
kubectl attach hello-world
// execute something inside a container like i want list the app directory
kubectl exec helloworld -- ls /app
// connect to the service 
kubectl run -i --tty busyboxpod --image=busybox --restart=Never -- sh
// open another shell then run
kubectl describe svc hello-world-service
// Now on busybox shell 
telnet $endpoints
