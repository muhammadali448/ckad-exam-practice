// create a deployment
kubectl run helloworld-dp1 --image=muhammadali448/nodejsappkuber --replicas=3 --port=3000 --dry-run -o yaml > dp1.yaml
kubectl create -f dp1.yaml

// check deployment
kubectl get deployments
// check pods
kubectl get po -w
//check replicaset
kubectl get rs
// check labels on pods
kubectl get po --show-labels
// check the status of deployment
kubectl rollout status deployment helloworld-dp1
// create a service 
kubectl expose deployment helloworld-dp1 --type=NodePort --dry-run -o yaml > serviceForDeployment.yaml
kubectl create -f serviceForDeployment.yaml
// check the service 
kubectl get svc
// hit the service
minikube service helloworld-dp1 --url
// set the image of container in deployment
kubectl set image deployment/helloworld-dp1 helloworld-dp1=muhammadali448/nodejsappkuber:v2
// check the image changes
kubectl describe deploy helloworld-dp1 | grep -i image
// check the history
kubectl rollout history deployment/helloworld-dp1
// undo the version which change to previous image
kubectl rollout undo deployment/helloworld-dp1
kubectl describe deploy helloworld-dp1 | grep -i image 
kubectl rollout status deployment helloworld-dp1
// undo to a previous version
kubectl rollout undo deployment helloworld-dp1 --to-revision=2
