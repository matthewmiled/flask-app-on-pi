# flask-app-on-pi
A Flask app deployed to pi cluster


# Helm/Deployment

* Image is built and pushed to DockerHub
* There is a kube secert in the cluster that allows the k8s Deployment resource to authenticate to DockerHub and pull the image
  * https://stackoverflow.com/questions/49032812/how-to-pull-image-from-dockerhub-in-kubernetes

* Is deployed to cluster using Helm

```bash
cd helm/flask-app-on-pi
helm upgrade prod-flask-app-on-pi . --kube-context mmiles-cluster --namespace prod
```

* Can then port forward that pod on port 8080 and access it via localhost

* Might see some timeouts due to readiness/liveness checks failing

# TODO

* Investigate readiness/liveness check timeouts - might need to bump seconds
* Look at ingress/load-balancers/DNS - so it can be accessed externally via a URL


