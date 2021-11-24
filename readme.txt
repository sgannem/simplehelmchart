https://ao.ms/how-to-deploy-a-helm-hello-world-app-onto-kubernetes/

docker build -t hello-world .
docker run -p 80:8008 hello-world
http://localhost/
docker login
docker tag hello-world srinitestdocker1/hello-world
docker push srinitestdocker1/hello-world:latest

helm create helloworld-chart
helm lint
helm package helloworld-chart
$ helm install helloworld helloworld-chart-0.1.0.tgz
NAME: helloworld
LAST DEPLOYED: Wed Nov 24 00:35:46 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
1. Get the application URL by running these commands:
     NOTE: It may take a few minutes for the LoadBalancer IP to be available.
           You can watch the status of by running 'kubectl get --namespace default svc -w helloworld-helloworld-chart'
  export SERVICE_IP=$(kubectl get svc --namespace default helloworld-helloworld-chart --template "{{ range (index .status.loadBalancer.ingress 0) }}{{.}}{{ end }}")
  echo http://$SERVICE_IP:80

$helm uninstall helloworld
release "helloworld" uninstalled

