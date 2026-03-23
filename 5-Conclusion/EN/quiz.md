# Final Assessment: GitOps and ArgoCD Mastery

Use this final assessment as a course-wide self-check. Take your time, commit to an answer first, and then compare your reasoning with the explanation.

---

## Section 1: Continuous Delivery Fundamentals

### Question 1
What is the primary goal of Continuous Delivery?

- A) To eliminate all manual testing
- B) To deploy code to production without any human involvement
- C) To automate getting changes into production safely and quickly in a sustainable way
- D) To reduce the number of developers needed

<details>
<summary>Reveal answer</summary>

**Answer: C**

Continuous Delivery focuses on automating the release process to get changes into production safely, quickly, and sustainably. It doesn't necessarily eliminate human involvement (that's Continuous Deployment) or reduce headcount—it frees engineers from toil to focus on value delivery.
</details>

### Question 2
What is the relationship between Continuous Integration (CI) and Continuous Delivery (CD)?

- A) They are the same thing
- B) CI is an optional enhancement to CD
- C) CI is an essential prerequisite for CD
- D) CD must be implemented before CI

<details>
<summary>Reveal answer</summary>

**Answer: C**

CI is an essential prerequisite for CD. You need to first integrate and test code changes (CI) before you can reliably deliver them (CD). CI focuses on merging and testing code, while CD automates deployment to environments.
</details>

---

## Section 2: GitOps Principles

### Question 3
Which of the following is NOT one of the four GitOps principles?

- A) Declarative
- B) Versioned and Immutable
- C) Pushed Automatically
- D) Continuously Reconciled

<details>
<summary>Reveal answer</summary>

**Answer: C**

The four GitOps principles are: Declarative, Versioned and Immutable, **Pulled** Automatically (not pushed), and Continuously Reconciled. The pull-based model is a key differentiator from traditional push-based deployments.
</details>

### Question 4
What is the main security advantage of the GitOps pull model over the traditional push model?

- A) It uses stronger encryption
- B) The CI/CD system doesn't need write access to the cluster
- C) It requires fewer authentication tokens
- D) It supports more identity providers

<details>
<summary>Reveal answer</summary>

**Answer: B**

In the pull model, a GitOps operator running inside the cluster pulls changes from Git. This means the CI/CD system doesn't need credentials with write access to the cluster's API, significantly reducing the attack surface if the CI/CD system is compromised.
</details>

### Question 5
What happens when drift is detected in a GitOps setup with self-healing enabled?

- A) An alert is sent and manual intervention is required
- B) The system automatically reverts to match the desired state in Git
- C) The Git repository is updated to match the cluster state
- D) The deployment is rolled back to the previous version

<details>
<summary>Reveal answer</summary>

**Answer: B**

With self-healing enabled, the GitOps operator automatically reconciles the cluster state to match the desired state defined in Git. Manual changes to the cluster are automatically reverted.
</details>

---

## Section 3: ArgoCD Architecture and Features

### Question 6
What deployment model does ArgoCD use for managing multiple clusters?

- A) Peer-to-peer model
- B) Distributed mesh model
- C) Hub-and-spoke model
- D) Federation model

<details>
<summary>Reveal answer</summary>

**Answer: C**

ArgoCD uses a hub-and-spoke model where a central control plane cluster (with ArgoCD installed) manages deployments to multiple target clusters. This enables centralized management while maintaining scalability.
</details>

### Question 7
Which of the following is ArgoCD responsible for in a CI/CD pipeline?

- A) Building container images
- B) Running unit tests
- C) Deploying applications to Kubernetes
- D) Code linting and static analysis

<details>
<summary>Reveal answer</summary>

**Answer: C**

ArgoCD focuses on the deployment phase of Continuous Delivery. It's responsible for deploying applications to Kubernetes by syncing the desired state from Git. Building, testing, and scanning are handled by CI tools.
</details>

### Question 8
What does the `selfHeal: true` setting in an ArgoCD Application's sync policy do?

- A) Automatically fixes bugs in the application code
- B) Restarts unhealthy pods
- C) Automatically reverts manual changes made to the cluster
- D) Repairs corrupted Git repositories

<details>
<summary>Reveal answer</summary>

**Answer: C**

When `selfHeal: true` is enabled, ArgoCD automatically reverts any manual changes made directly to the cluster to match the desired state in Git. This prevents configuration drift.
</details>

---

## Section 4: ArgoCD Application CRD

### Question 9
In an ArgoCD Application manifest, what does the `spec.source` field define?

- A) The target cluster and namespace for deployment
- B) The Git repository and path containing the manifests
- C) The sync policy settings
- D) The ArgoCD project the application belongs to

<details>
<summary>Reveal answer</summary>

**Answer: B**

The `spec.source` field defines where ArgoCD should get the application manifests from, including the repository URL, path within the repo, target revision (branch/tag/commit), and config management tool settings.
</details>

### Question 10
What config management tool will ArgoCD detect if it finds a `Chart.yaml` file in the source path?

- A) Kustomize
- B) Plain YAML
- C) Jsonnet
- D) Helm

<details>
<summary>Reveal answer</summary>

**Answer: D**

ArgoCD automatically detects the config management tool based on files in the source path. A `Chart.yaml` file indicates a Helm chart. Similarly, `kustomization.yaml` indicates Kustomize.
</details>

### Question 11
Which sync option should you use to automatically create the target namespace if it doesn't exist?

- A) `AutoCreate=true`
- B) `CreateNamespace=true`
- C) `EnsureNamespace=true`
- D) `InitNamespace=true`

<details>
<summary>Reveal answer</summary>

**Answer: B**

The `CreateNamespace=true` sync option tells ArgoCD to automatically create the destination namespace if it doesn't already exist before deploying resources.
</details>

---

## Section 5: GitOps Prerequisites and Best Practices

### Question 12
Why is automated testing CRITICAL for GitOps success?

- A) It makes deployments faster
- B) It reduces the need for monitoring
- C) Without it, bugs automatically deploy to production
- D) It's required by ArgoCD

<details>
<summary>Reveal answer</summary>

**Answer: C**

In GitOps with auto-sync, deployments are automated. If your tests don't catch bugs, those bugs deploy automatically too. There's no human safety net in a fully automated pipeline, making comprehensive testing essential.
</details>

### Question 13
What should you NEVER store in a Git repository, even in a private one?

- A) Kubernetes manifests
- B) Helm values files
- C) Plain-text secrets and credentials
- D) Docker image tags

<details>
<summary>Reveal answer</summary>

**Answer: C**

Never store plain-text secrets in Git. Even private repositories can be compromised, and Git history is permanent. Use secret management solutions like Sealed Secrets, External Secrets Operator, or HashiCorp Vault instead.
</details>

### Question 14
What is the purpose of branch protection rules in a GitOps workflow?

- A) To prevent merge conflicts
- B) To ensure changes are reviewed before they reach production
- C) To speed up deployments
- D) To reduce Git repository size

<details>
<summary>Reveal answer</summary>

**Answer: B**

In GitOps, merging to the main branch effectively means deploying to production. Branch protection rules ensure all changes go through proper review (PRs, CI checks, approvals) before being deployed.
</details>

### Question 15
Which environment should typically have auto-sync enabled?

- A) Production only
- B) Development and QA, with manual sync for Production
- C) All environments should have auto-sync
- D) No environments should have auto-sync

<details>
<summary>Reveal answer</summary>

**Answer: B**

Best practice is to enable auto-sync for non-production environments (dev, QA) to enable fast iteration, while keeping production with manual sync for additional control and approval gates.
</details>

---

## Section 6: The App of Apps Pattern

### Question 16
What is the main benefit of the App of Apps pattern?

- A) It reduces the number of Git repositories needed
- B) It allows managing Application resources declaratively through GitOps
- C) It speeds up ArgoCD sync operations
- D) It eliminates the need for Helm charts

<details>
<summary>Reveal answer</summary>

**Answer: B**

The App of Apps pattern allows you to manage ArgoCD Application resources declaratively through GitOps, just like any other Kubernetes resource. Instead of manually creating Applications through the UI, you define them in Git.
</details>

### Question 17
Where does the App of Apps Application typically point to?

- A) The Helm chart repository
- B) A folder containing other ArgoCD Application manifests
- C) The Kubernetes API server
- D) The container registry

<details>
<summary>Reveal answer</summary>

**Answer: B**

The App of Apps Application points to a folder in your Git repository that contains other ArgoCD Application manifests. When synced, it creates/manages all the child Applications defined in that folder.
</details>

---

## Section 7: Troubleshooting and Operations

### Question 18
An Application shows "Synced" but "Degraded" health status. What does this mean?

- A) The sync failed
- B) The manifests were applied successfully, but the resources are failing
- C) There's a network connectivity issue
- D) The Git repository is unavailable

<details>
<summary>Reveal answer</summary>

**Answer: B**

"Synced" means the manifests from Git were successfully applied to the cluster. "Degraded" means the resources themselves are failing (e.g., pods can't start due to invalid image tag, resource limits, or configuration errors).
</details>

### Question 19
What is the simplest way to rollback a deployment in GitOps?

- A) Restart the ArgoCD server
- B) Delete and recreate the Application
- C) `git revert` the problematic commit and push
- D) Scale the deployment to zero replicas

<details>
<summary>Reveal answer</summary>

**Answer: C**

In GitOps, rollback is as simple as reverting the Git commit that caused the problem. ArgoCD will automatically sync the reverted state to the cluster.
</details>

### Question 20
What is the primary purpose of monitoring in a GitOps environment?

- A) To generate reports for management
- B) To detect when automated deployments cause problems
- C) To comply with regulations
- D) To track developer productivity

<details>
<summary>Reveal answer</summary>

**Answer: B**

With automated deployments, you need automated detection of problems. Monitoring helps you quickly identify when a deployment causes issues, enabling rapid response and rollback if needed.
</details>

---

## Section 8: Comprehensive Scenarios

### Question 21
Your team is implementing GitOps for the first time. What should be your first step?

- A) Enable auto-sync for all applications in production
- B) Start with a non-production environment and manual sync
- C) Migrate all existing applications to ArgoCD simultaneously
- D) Delete all existing CI/CD pipelines

<details>
<summary>Reveal answer</summary>

**Answer: B**

When starting with GitOps, begin with non-production environments and manual sync. This allows you to learn the workflow, build confidence, and identify issues before applying automation to critical systems.
</details>

### Question 22
A developer manually changed a ConfigMap in production to fix an urgent issue. With GitOps and self-heal enabled, what happens next?

- A) The change persists until the next scheduled sync
- B) ArgoCD automatically reverts the change to match Git
- C) ArgoCD updates Git to reflect the manual change
- D) An alert is sent but no automatic action is taken

<details>
<summary>Reveal answer</summary>

**Answer: B**

With self-heal enabled, ArgoCD continuously reconciles the cluster state with Git. The manual change will be automatically reverted to match the desired state in Git. To make the change permanent, it must be committed to Git.
</details>

### Question 23
Your organization wants to implement GitOps but currently has no automated testing. What should you do?

- A) Implement GitOps anyway; testing can come later
- B) Only enable manual sync until testing is in place
- C) Invest in testing infrastructure before enabling auto-sync
- D) Use ArgoCD's built-in testing features

<details>
<summary>Reveal answer</summary>

**Answer: C**

Automated testing is a critical prerequisite for GitOps success. Without comprehensive tests, enabling auto-sync means bugs automatically deploy to production. Invest in testing before enabling automation.
</details>

---

## Scoring Guide

| Score | Level | Recommendation |
|-------|-------|----------------|
| 20-23 | Expert | You're ready to implement GitOps in production! |
| 16-19 | Proficient | Good understanding! Review the topics you missed. |
| 12-15 | Developing | Review the course materials, especially prerequisites section. |
| 8-11 | Beginner | Consider retaking the course with hands-on practice. |
| 0-7 | Needs Review | Start from Chapter 0 and work through all materials. |

---

## Knowledge Check Complete!

Regardless of your score, remember that learning is a continuous journey. The key concepts to always keep in mind:

1. **GitOps requires foundation**: Testing, PR culture, and monitoring are prerequisites, not optional extras.

2. **Git is the source of truth**: All changes flow through Git, enabling audit trails and easy rollbacks.

3. **Pull over push**: The pull-based model improves security and enables self-healing.

4. **Start simple, grow gradually**: Begin with dev environments and manual sync before enabling full automation.

5. **Tools support culture**: ArgoCD is powerful, but success depends on the practices around it.

**Continue your learning journey and happy GitOps-ing!** 🚀
