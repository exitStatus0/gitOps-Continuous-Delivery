# Sample Files for ArgoCD Practice Lab

This directory contains sample files that you can use to complete the practice lab.

## Directory Structure

```
sample-files/
├── apps/                           # ArgoCD Application manifests
│   ├── cogitator-dev.yaml       # Dev environment Application
│   ├── cogitator-qa.yaml        # QA environment Application
│   └── cogitator-prod.yaml      # Production environment Application
├── charts/                         # Helm charts
│   └── cogitator/               # Notification service chart
│       ├── Chart.yaml              # Chart metadata
│       ├── templates/              # Kubernetes manifest templates
│       │   ├── deployment.yaml
│       │   ├── service.yaml
│       │   ├── _helpers.tpl
│       │   └── NOTES.txt
│       ├── values.yaml             # Default values
│       ├── values-dev.yaml         # Dev environment overrides
│       ├── values-qa.yaml          # QA environment overrides
│       └── values-prod.yaml        # Production environment overrides
├── app-of-apps.yaml                # App of Apps manifest
└── README.md                       # This file
```

## Usage

1. **Copy to your GitOps repository:**
   ```bash
   cp -r sample-files/* /path/to/your/gitops-repo/
   ```

2. **Update the `repoURL` in Application manifests:**
   Replace `https://github.com/your-org/gitops-config-repo` with your actual repository URL.

3. **Commit and push:**
   ```bash
   cd /path/to/your/gitops-repo/
   git add .
   git commit -m "Add cogitator service configuration"
   git push origin main
   ```

4. **Follow the lab instructions** in `EN/PracticeLab.md` or `UA/ПрактичнаРобота.md`

## Customization

Feel free to customize:
- **Image**: The default image is `nginx`. You can change it to any container image.
- **Resources**: Adjust CPU and memory limits based on your cluster capacity.
- **Replicas**: Change replica counts for different environments.
- **Repository URL**: Update to point to your actual Git repository.

## Notes

- The Helm chart uses nginx as the default image for demonstration purposes
- All Applications are configured with `CreateNamespace=true` to automatically create namespaces
- Production Application has `selfHeal: true` enabled for automatic drift correction

Happy GitOps-ing! 🚀


