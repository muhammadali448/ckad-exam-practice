// Create a replication controller
kubectl run rc1 --image=muhammadali448/nodejsappkuber --port=3000 --generator=run/v1 --replicas=2 --dry-run -o yaml > rc1.yaml
 
// Check 2 pods replicas
kubectl get po -w
// Check replicas
kubectl get rc
// Delete any of rc pod it will create a new pod again
kubectl delete po rc-$ --force --grace-period=0
kubectl get po 
// Scale upto 4 replicas 
kubectl scale rc/rc --replicas=4
// if you specify --replicase=3
kubectl scale rc/rc --replicas=3 // other pods will terminated
