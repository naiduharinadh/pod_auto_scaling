
Deploy the Metrics Server with the following command: <br />
` kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml `
<br />
use autoscale by adding: <br />
` kubectl autoscale deployment nodewebapp --cpu-percent=50 --min=1 --max=10 ` 
<br />
` kubectl get hpa nodewebapp `

Generate Load: <br />
kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://nodewebapp:4623; done"
