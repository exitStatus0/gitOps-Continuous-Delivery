# ArgoCD Application CRD Knowledge Assessment

Test your understanding of ArgoCD Application CRD, its structure, sync policies, and best practices!

**Instructions:**
- Answer all questions to the best of your ability
- Record your answers (A, B, C, D, or True/False)
- Check your answers using the `quiz-answers.md` file
- Calculate your score using the grading scale at the end

---

## Section 1: Application CRD Fundamentals (25 points)

### Question 1 (5 points)
What is an ArgoCD Application CRD?

A) A Docker image for deploying applications  
B) A Kubernetes Custom Resource that represents a deployed application  
C) A command-line tool for managing ArgoCD  
D) A monitoring service for Kubernetes clusters

**Your answer:** _____

---

### Question 2 (5 points)
Which field in the Application CRD is mandatory and defines where the manifests are sourced from?

A) `spec.destination`  
B) `spec.syncPolicy`  
C) `spec.source`  
D) `spec.project`

**Your answer:** _____

---

### Question 3 (5 points)
True or False: The Application CRD can only deploy plain YAML manifests.

**Your answer:** _____

---

### Question 4 (5 points)
How does ArgoCD track resources deployed by an Application?

A) By storing them in a database  
B) By adding labels or annotations to the resources  
C) By creating a ConfigMap with resource lists  
D) By querying the Kubernetes API every time

**Your answer:** _____

---

### Question 5 (5 points)
Which of the following is NOT a supported config management tool in ArgoCD Applications?

A) Helm  
B) Kustomize  
C) Terraform  
D) Jsonnet

**Your answer:** _____

---

## Section 2: Source Configuration (20 points)

### Question 6 (5 points)
In the `source` field, what does the `targetRevision` specify?

A) The Kubernetes API version  
B) The Git branch, tag, or commit to track  
C) The ArgoCD version requirement  
D) The manifest file version

**Your answer:** _____

---

### Question 7 (5 points)
True or False: ArgoCD can automatically detect which config management tool to use based on the files in the repository.

**Your answer:** _____

---

### Question 8 (5 points)
If a repository contains a `Chart.yaml` file, which tool will ArgoCD automatically detect?

A) Kustomize  
B) Plain YAML  
C) Helm  
D) Jsonnet

**Your answer:** _____

---

### Question 9 (5 points)
What is the purpose of specifying `valueFiles` in the Helm source configuration?

A) To list all Helm charts in the repository  
B) To specify which values files to use for rendering the Helm chart  
C) To define the Helm version  
D) To configure Helm repository credentials

**Your answer:** _____

---

## Section 3: Destination Configuration (15 points)

### Question 10 (5 points)
How can you specify the target cluster in the `destination` field?

A) Only by cluster name  
B) Only by server URL  
C) Either by cluster name or server URL  
D) By namespace only

**Your answer:** _____

---

### Question 11 (5 points)
What server URL should be used to deploy to the same cluster where ArgoCD is running?

A) `localhost:8080`  
B) `https://kubernetes.default.svc`  
C) `http://argocd-server`  
D) `https://127.0.0.1:6443`

**Your answer:** _____

---

### Question 12 (5 points)
True or False: Cluster-scoped resources like ClusterRoles ignore the namespace specified in the destination field.

**Your answer:** _____

---

## Section 4: Sync Policies and Behavior (25 points)

### Question 13 (5 points)
What does it mean to "sync" an Application?

A) Create a backup of the application  
B) Reconcile the live cluster state with the desired state from Git  
C) Update the ArgoCD version  
D) Synchronize multiple clusters together

**Your answer:** _____

---

### Question 14 (5 points)
Which sync policy configuration enables automatic synchronization when changes are detected in Git?

A) `syncPolicy: manual: {}`  
B) `syncPolicy: automated: {}`  
C) `syncPolicy: scheduled: {}`  
D) `syncPolicy: continuous: {}`

**Your answer:** _____

---

### Question 15 (5 points)
What does the `selfHeal: true` option do?

A) Automatically restarts failed pods  
B) Automatically reverts manual changes made directly to the cluster  
C) Heals network connectivity issues  
D) Repairs corrupted manifests in Git

**Your answer:** _____

---

### Question 16 (5 points)
True or False: The `prune: true` option will automatically delete resources from the cluster when they are removed from Git.

**Your answer:** _____

---

### Question 17 (5 points)
What does the `CreateNamespace=true` sync option do?

A) Creates a new Kubernetes cluster  
B) Creates the destination namespace if it doesn't exist  
C) Creates a namespace for ArgoCD itself  
D) Creates backup namespaces for disaster recovery

**Your answer:** _____

---

## Section 5: Application Lifecycle and States (15 points)

### Question 18 (5 points)
What does the "OutOfSync" status mean?

A) The Application is not running  
B) The live state differs from the desired state in Git  
C) The sync operation failed  
D) The Application is waiting for manual approval

**Your answer:** _____

---

### Question 19 (5 points)
Which health status indicates that all resources are running properly?

A) Synced  
B) Progressing  
C) Healthy  
D) Active

**Your answer:** _____

---

### Question 20 (5 points)
True or False: An Application can be "Synced" but still be "Degraded" in health status.

**Your answer:** _____

---

## Total Score: _____ / 100

---

## Grading Scale

Calculate your percentage and find your level:

- **90-100 points (90-100%)**: **ArgoCD Application Expert** - Outstanding! You have mastered ArgoCD Application CRDs and are ready to design complex deployment strategies.

- **80-89 points (80-89%)**: **Advanced Practitioner** - Excellent knowledge of Applications. Review any missed concepts to perfect your expertise.

- **70-79 points (70-79%)**: **Intermediate** - Good understanding of Application fundamentals. Study the areas where you had difficulties.

- **60-69 points (60-69%)**: **Beginner** - You grasp the basics. Review the README materials more thoroughly, especially sync policies and lifecycle management.

- **Below 60 points (<60%)**: **Novice** - Take time to carefully study the ArgoCD Application CRD materials and try the quiz again.

---

**Next Steps:**
1. Check your answers in `quiz-answers.md`
2. Calculate your total score
3. Review any sections where you had incorrect answers
4. Create a test Application to practice what you've learned!

**Hands-On Practice:**
- Create a simple Application CRD for a demo app
- Experiment with different sync policies
- Test self-heal by manually modifying a deployed resource
- Try deploying with Helm, Kustomize, and plain YAML
- Observe Application states in the ArgoCD UI


