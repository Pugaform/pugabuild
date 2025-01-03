1. Have a domain registered in Route 53 to be able to access ArgoCD and for ExternalDNS operations.

After the infrastructure provisioning step you'll be able to access your ArgoCD through the URL argocd.your-domain.com

2. Create an SSH Key for your GitOps Git repository with read/write access, this will be required in the post-deployment operations.