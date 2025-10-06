#### Commands

```bash
# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# check pods running
kubectl get pod -n argocd

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl get secret argocd-initial-admin-secret -n argocd -o yaml

echo data. password | base64 --decode

#add the application.yaml to the repo and apply the application.yaml

git add .
kubectl apply -f application.yaml
```
![image alt](https://github.com/Ezekiel200483/argocd-config/blob/e32efa81b8dc60ba86d54751045691e6cc8dbaa0/Screenshot%202025-10-06%20at%2009.22.03.png)

#Now, test the setup by updating deployment.yaml file (update the image version)
![image alt](https://github.com/Ezekiel200483/argocd-config/blob/3ad7793634cdab86068a6329e619384874514e39/version.png)


#Test Prunning, rename metadata: name: myapp-deployment to myapp
![image alt](https://github.com/Ezekiel200483/argocd-config/blob/8455689e07201eac8b5d94deb806d09abf545e16/deployment.png)

![image alt](https://github.com/Ezekiel200483/argocd-config/blob/77fc589dcb9fc3cdd3fc22a3e4fdce519a27445d/deployment%202.png)


# Test selfheal by changing replicas to 4 from 2
kubectl edit deployment -n myapp myapp


# you can change and delete init password

```
</br>

#### Links

* Config repo: [https://gitlab.com/nanuchi/argocd-app-config](https://gitlab.com/nanuchi/argocd-app-config)

* Docker repo: [https://hub.docker.com/repository/docker/nanajanashia/argocd-app](https://hub.docker.com/repository/docker/nanajanashia/argocd-app)

* Install ArgoCD: [https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd](https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd)

* Login to ArgoCD: [https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli](https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli)

* ArgoCD Configuration: [https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/)
