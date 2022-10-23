# Secret
### Local Server
`kubectl create secret generic pgpassword --from-literal PGPASSWORD=123456`
### GCP
`gcloud config set project tier-app-gke`
`gcloud config set compute/zone us-central1-c`
`gcloud container clusters get-credentials fib-cluster`
`kubectl create secret generic pgpassword --from-literal PGPASSWORD=123456`

# Helm
### Install Helm v3:

In your Google Cloud Console run the following:

`curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3`
`chmod 700 get_helm.sh`
`./get_helm.sh`

[https://helm.sh/docs/intro/install/#from-script](https://helm.sh/docs/intro/install/#from-script)

### Install Ingress-Nginx:

In your Google Cloud Console run the following:

`helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx`
`helm install my-release ingress-nginx/ingress-nginx`

Then check the service status:
`kubectl --namespace default get services -o wide -w my-release-ingress-nginx-controller`

IMPORTANT: If you get an error such as chart requires kubeVersion: >=1.16.0-0.....

You may need to manually upgrade your cluster to at least the version specified:

`gcloud container clusters upgrade  YOUR_CLUSTER_NAME --master --cluster-version 1.16`


# Deploy to GKE
### Link Github Repository with Google Cloud Source Repositories 

### Deploy the config files
`kubectl apply -f ~/cloudshell_open/github_yifanbu_3-tier-app-gke/k8s`
