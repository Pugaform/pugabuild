# Post-Provisioning Steps for Pugabuild

After provisioning, follow these steps to complete your setup:

---

## 1. Update GitOps Credentials in Secrets Manager

After the provisioning process, a secret named **`pugaform/gitops-credentials`** will be created in AWS Secrets Manager. It contains two fields with dummy values:

- **`url`**: Replace this with your GitOps repository URL.
- **`sshPrivateKey`**: Provide your SSH private key in Base64-encoded format. 

### Why Base64?
The SSH private key does not retain its structure when copy-pasted, which can lead to errors. Base64 encoding ensures the integrity of the key during input. The application will decode the Base64 string during usage.

---

## 2. Create an ArgoCD Certificate in Amazon Certificate Manager (ACM)

1. Open **Amazon Certificate Manager** and click **Create Certificate**.
2. Use the domain name you provided in the provisioning form (e.g., `argocd.your-domain.com`).
3. Select **DNS Validation** and click **Create records in Route 53** to automatically add the TXT records needed for validation.
4. Wait for DNS propagation to complete. This may take a few minutes due to DNS provisioning delays.

---

## 3. Configure Helm Charts or Kubernetes Manifests

Set up your applications in the GitOps repository and path provided in the provisioning form. For example:
- **GitOps Path**: `./dev/applications/example-app-1`, `./dev/applications/example-app-2`

### Using Helm Charts
If working with Helm charts, include the `templates` directory in the path. Example:
- `./dev/applications/templates/pod.yaml`
- `./dev/applications/templates/deployment.yaml`

### Kubernetes Manifests
For Kubernetes manifests, add the necessary YAML files directly under the specified path.

---

Complete these steps to finalize your setup. If you encounter any issues, refer to the documentation or reach out to support.