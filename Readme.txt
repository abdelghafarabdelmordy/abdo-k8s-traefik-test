kubectl.exe create namespace keycloak
kubectl.exe create namespace monitoring

Install the AWS Load Balancer Controller:
helm repo add eks https://aws.github.io/eks-charts
helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
  -n kube-system \
  --set clusterName=your-cluster-name

Verify Installation:
kubectl get pods -n kube-system -l app.kubernetes.io/name=aws-load-balancer-controller

Install Traefik using Helm:
helm repo add traefik https://helm.traefik.io/traefik
helm repo update
helm install traefik traefik/traefik -n kube-system

verify:
kubectl get pods -n kube-system -l app.kubernetes.io/name=traefik