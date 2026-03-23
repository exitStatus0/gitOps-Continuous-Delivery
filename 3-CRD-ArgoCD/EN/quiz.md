# ArgoCD Application CRD Knowledge Assessment

Use this quiz to check how well you understand the ArgoCD Application CRD, its structure, sync policies, and best practices.

**How to use this quiz:**
- Answer all questions to the best of your ability
- Record your answers (A, B, C, D, or True/False)
- Reveal the answer only after you commit to a choice, then compare it with the explanation
- Calculate your score using the grading scale at the end

---

## Section 1: Application CRD Fundamentals (25 points)

### Question 1 (5 points)
What is an ArgoCD Application CRD?

A) A Docker image for deploying applications  
B) A Kubernetes Custom Resource that represents a deployed application  
C) A command-line tool for managing ArgoCD  
D) A monitoring service for Kubernetes clusters
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - A Kubernetes Custom Resource that represents a deployed application

**Explanation:** An ArgoCD Application is a Kubernetes Custom Resource (CR) defined by a Custom Resource Definition (CRD). It represents a deployed application in your cluster and contains all the information ArgoCD needs to deploy and manage that application. It's not a Docker image (A), CLI tool (C), or monitoring service (D).

</details>

---
### Question 2 (5 points)
Which field in the Application CRD is mandatory and defines where the manifests are sourced from?

A) `spec.destination`  
B) `spec.syncPolicy`  
C) `spec.source`  
D) `spec.project`
<details>
<summary>Reveal answer</summary>

**Correct Answer: C** - `spec.source`

**Explanation:** The `spec.source` field is mandatory and defines where ArgoCD should get the manifests from (Git repository, Helm repository, etc.). While `spec.destination` (A) and `spec.project` (D) are also required, the question specifically asks about where manifests are *sourced from*. The `spec.syncPolicy` (B) is optional.

</details>

---
### Question 3 (5 points)
True or False: The Application CRD can only deploy plain YAML manifests.
<details>
<summary>Reveal answer</summary>

**Correct Answer: False**

**Explanation:** ArgoCD Applications support multiple config management tools including Helm, Kustomize, Jsonnet, plain YAML/JSON, and custom plugins. This flexibility allows teams to use their preferred tools for defining Kubernetes resources.

</details>

---
### Question 4 (5 points)
How does ArgoCD track resources deployed by an Application?

A) By storing them in a database  
B) By adding labels or annotations to the resources  
C) By creating a ConfigMap with resource lists  
D) By querying the Kubernetes API every time
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - By adding labels or annotations to the resources

**Explanation:** ArgoCD adds labels or annotations (depending on the tracking method configured) to all resources deployed by an Application. This allows ArgoCD to monitor health status, detect drift, perform cleanup, and show relationships in the UI. It doesn't use a database (A), ConfigMaps (C), or constant API queries (D).

</details>

---
### Question 5 (5 points)
Which of the following is NOT a supported config management tool in ArgoCD Applications?

A) Helm
B) Kustomize
C) Terraform
D) Jsonnet
<details>
<summary>Reveal answer</summary>

**Correct Answer: C** - Terraform

**Explanation:** While ArgoCD natively supports Helm (A), Kustomize (B), Jsonnet (D), and plain YAML, it does not natively support Terraform. However, you could potentially integrate Terraform using a custom Config Management Plugin (CMP), but it's not a built-in supported tool.

</details>

---

## Section 2: Source Configuration (20 points)

---
### Question 6 (5 points)
In the `source` field, what does the `targetRevision` specify?

A) The Kubernetes API version  
B) The Git branch, tag, or commit to track  
C) The ArgoCD version requirement  
D) The manifest file version
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - The Git branch, tag, or commit to track

**Explanation:** The `targetRevision` field specifies which version of the source to use. For Git repositories, this can be a branch name (e.g., `main`), a tag (e.g., `v1.0.0`), or a specific commit SHA. For Helm chart repositories, it specifies the chart version. It has nothing to do with Kubernetes API version (A), ArgoCD version (C), or manifest file version (D).

</details>

---
### Question 7 (5 points)
True or False: ArgoCD can automatically detect which config management tool to use based on the files in the repository.
<details>
<summary>Reveal answer</summary>

**Correct Answer: True**

**Explanation:** ArgoCD performs automatic tool detection based on the files found in the repository path. For example, if it finds `Chart.yaml`, it uses Helm; if it finds `kustomization.yaml`, it uses Kustomize; if it finds `*.jsonnet` files, it uses Jsonnet; otherwise, it treats files as plain YAML.

</details>

---
### Question 8 (5 points)
If a repository contains a `Chart.yaml` file, which tool will ArgoCD automatically detect?

A) Kustomize  
B) Plain YAML  
C) Helm  
D) Jsonnet
<details>
<summary>Reveal answer</summary>

**Correct Answer: C** - Helm

**Explanation:** The presence of a `Chart.yaml` file is the standard indicator of a Helm chart. ArgoCD will automatically detect this and use Helm to render the manifests. `kustomization.yaml` would indicate Kustomize (A), `*.jsonnet` would indicate Jsonnet (D), and standalone `*.yaml` files would be treated as plain YAML (B).

</details>

---
### Question 9 (5 points)
What is the purpose of specifying `valueFiles` in the Helm source configuration?

A) To list all Helm charts in the repository
B) To specify which values files to use for rendering the Helm chart
C) To define the Helm version
D) To configure Helm repository credentials
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - To specify which values files to use for rendering the Helm chart

**Explanation:** The `valueFiles` field in the Helm source configuration specifies which values files from the repository should be used to override the default values when rendering the Helm chart. This allows you to have different configurations for different environments (e.g., `values-production.yaml`, `values-staging.yaml`).

</details>

---

## Section 3: Destination Configuration (15 points)

---
### Question 10 (5 points)
How can you specify the target cluster in the `destination` field?

A) Only by cluster name  
B) Only by server URL  
C) Either by cluster name or server URL  
D) By namespace only
<details>
<summary>Reveal answer</summary>

**Correct Answer: C** - Either by cluster name or server URL

**Explanation:** ArgoCD provides flexibility in specifying the target cluster. You can use either the cluster name (e.g., `name: 'production'`) or the server URL (e.g., `server: 'https://prod-cluster.example.com'`). Both methods are valid and can be used based on your preference. The namespace must also be specified separately.

</details>

---
### Question 11 (5 points)
What server URL should be used to deploy to the same cluster where ArgoCD is running?

A) `localhost:8080`  
B) `https://kubernetes.default.svc`  
C) `http://argocd-server`  
D) `https://127.0.0.1:6443`
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - `https://kubernetes.default.svc`

**Explanation:** `https://kubernetes.default.svc` is the standard in-cluster Kubernetes API server address. When ArgoCD is deployed in a cluster and you want to deploy applications to that same cluster, use this URL. The other options (A, C, D) are not standard in-cluster addresses.

</details>

---
### Question 12 (5 points)
True or False: Cluster-scoped resources like ClusterRoles ignore the namespace specified in the destination field.
<details>
<summary>Reveal answer</summary>

**Correct Answer: True**

**Explanation:** Cluster-scoped resources (such as ClusterRoles, ClusterRoleBindings, CustomResourceDefinitions, etc.) exist at the cluster level and are not confined to a namespace. Therefore, the `namespace` field in the destination configuration is ignored for these resources. Only namespace-scoped resources (like Deployments, Services, ConfigMaps) are created in the specified namespace.

</details>

---

## Section 4: Sync Policies and Behavior (25 points)

---
### Question 13 (5 points)
What does it mean to "sync" an Application?

A) Create a backup of the application  
B) Reconcile the live cluster state with the desired state from Git  
C) Update the ArgoCD version  
D) Synchronize multiple clusters together
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - Reconcile the live cluster state with the desired state from Git

**Explanation:** Syncing an Application means reconciling the actual state of resources in the cluster with the desired state defined in the Git repository. ArgoCD fetches the manifests from Git, renders them, compares with the live cluster state, and applies any necessary changes to make them match. It's not about backups (A), ArgoCD updates (C), or multi-cluster synchronization (D).

</details>

---
### Question 14 (5 points)
Which sync policy configuration enables automatic synchronization when changes are detected in Git?

A) `syncPolicy: manual: {}`  
B) `syncPolicy: automated: {}`  
C) `syncPolicy: scheduled: {}`  
D) `syncPolicy: continuous: {}`
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - `syncPolicy: automated: {}`

**Explanation:** Setting `syncPolicy.automated` to an empty object `{}` enables automatic synchronization. ArgoCD will continuously poll the Git repository and automatically deploy changes without manual intervention. There is no `manual` (A), `scheduled` (C), or `continuous` (D) sync policy type in ArgoCD.

</details>

---
### Question 15 (5 points)
What does the `selfHeal: true` option do?

A) Automatically restarts failed pods  
B) Automatically reverts manual changes made directly to the cluster  
C) Heals network connectivity issues  
D) Repairs corrupted manifests in Git
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - Automatically reverts manual changes made directly to the cluster

**Explanation:** The `selfHeal: true` option enables automatic drift correction. If someone manually changes a resource in the cluster (e.g., `kubectl edit deployment`), ArgoCD will detect the drift and automatically revert the change to match the desired state in Git. It doesn't restart pods (A), fix network issues (C), or repair Git manifests (D).

</details>

---
### Question 16 (5 points)
True or False: The `prune: true` option will automatically delete resources from the cluster when they are removed from Git.
<details>
<summary>Reveal answer</summary>

**Correct Answer: True**

**Explanation:** When `prune: true` is set in the automated sync policy, ArgoCD will automatically delete resources from the cluster when they are removed from the Git repository. This ensures the cluster stays in sync with Git by removing resources that are no longer defined in the source.

</details>

---
### Question 17 (5 points)
What does the `CreateNamespace=true` sync option do?

A) Creates a new Kubernetes cluster
B) Creates the destination namespace if it doesn't exist
C) Creates a namespace for ArgoCD itself
D) Creates backup namespaces for disaster recovery
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - Creates the destination namespace if it doesn't exist

**Explanation:** The `CreateNamespace=true` sync option automatically creates the destination namespace in the target cluster if it doesn't already exist. This is useful for first-time deployments where the namespace hasn't been manually created yet. It doesn't create clusters (A), ArgoCD namespaces (C), or backup namespaces (D).

</details>

---

## Section 5: Application Lifecycle and States (15 points)

---
### Question 18 (5 points)
What does the "OutOfSync" status mean?

A) The Application is not running  
B) The live state differs from the desired state in Git  
C) The sync operation failed  
D) The Application is waiting for manual approval
<details>
<summary>Reveal answer</summary>

**Correct Answer: B** - The live state differs from the desired state in Git

**Explanation:** "OutOfSync" status indicates that the live state of resources in the cluster doesn't match the desired state defined in Git. This could be due to recent Git changes that haven't been synced yet, or manual changes made directly to the cluster. It's a sync status indicator, not a running status (A), failure status (C), or approval status (D).

</details>

---
### Question 19 (5 points)
Which health status indicates that all resources are running properly?

A) Synced  
B) Progressing  
C) Healthy  
D) Active
<details>
<summary>Reveal answer</summary>

**Correct Answer: C** - Healthy

**Explanation:** "Healthy" is the health status that indicates all resources are running properly and functioning as expected. "Synced" (A) is a sync status, not a health status. "Progressing" (B) means resources are being created/updated. "Active" (D) is not a valid ArgoCD health status.

</details>

---
### Question 20 (5 points)
True or False: An Application can be "Synced" but still be "Degraded" in health status.
<details>
<summary>Reveal answer</summary>

**Correct Answer: True**

**Explanation:** Sync status and health status are independent. An Application can be "Synced" (meaning the live state matches the desired state in Git) but "Degraded" in health (meaning some resources are failing, like pods in CrashLoopBackOff). For example, if Git defines a Deployment with a broken container image, ArgoCD will successfully sync it (Synced status) but the pods will fail (Degraded health).

</details>

---

## Scoring

- Section 1 (Fundamentals): _____ / 25 points
- Section 2 (Source Configuration): _____ / 20 points
- Section 3 (Destination Configuration): _____ / 15 points
- Section 4 (Sync Policies): _____ / 25 points
- Section 5 (Lifecycle & States): _____ / 15 points

**Total Score: _____ / 100 points**

---

## Grading Scale

- **90-100 points**: **ArgoCD Application Expert** - Outstanding! Ready to design complex deployment strategies.
- **80-89 points**: **Advanced Practitioner** - Excellent knowledge. Review missed concepts to perfect expertise.
- **70-79 points**: **Intermediate** - Good foundation. Study areas where you had difficulties.
- **60-69 points**: **Beginner** - You grasp the basics. Review sync policies and lifecycle management.
- **Below 60 points**: **Novice** - Re-read the Application CRD materials and try again.

---

**Next Steps:**
- Review sections where you missed questions
- Try the [Interactive Quiz](quiz.html) for instant feedback
- Create a test Application CRD and experiment with sync policies
- Move on to [Module 4 — Practice](../../4-Practice/PrerequisitesInstallation.md)

---
