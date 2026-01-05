# ArgoCD Knowledge Assessment

Test your understanding of ArgoCD concepts, architecture, and best practices!

**Instructions:**
- Answer all questions to the best of your ability
- Record your answers (A, B, C, D, or True/False)
- Check your answers using the `quiz-answers.md` file
- Calculate your score using the grading scale at the end

---

## Section 1: ArgoCD Fundamentals (25 points)

### Question 1 (5 points)
What is ArgoCD?

A) A CI/CD platform for building and testing applications  
B) A declarative, GitOps continuous delivery tool for Kubernetes  
C) A container registry for storing Docker images  
D) A monitoring tool for Kubernetes clusters

**Your answer:** _____

---

### Question 2 (5 points)
Which architectural pattern does ArgoCD follow for multi-cluster management?

A) Microservices architecture  
B) Hub-and-spoke model  
C) Peer-to-peer architecture  
D) Serverless architecture

**Your answer:** _____

---

### Question 3 (5 points)
In the context of GitOps, what role does ArgoCD play?

A) It stores the Git repositories  
B) It acts as the software agent that pulls desired state and reconciles it with live state  
C) It builds container images from source code  
D) It provides the Kubernetes cluster infrastructure

**Your answer:** _____

---

### Question 4 (5 points)
True or False: ArgoCD uses a push-based deployment model where CI/CD pipelines push changes directly to clusters.

**Your answer:** _____

---

### Question 5 (5 points)
How does ArgoCD handle configuration drift?

A) It sends an alert but takes no action  
B) It shuts down the cluster for safety  
C) It automatically reconciles the live state to match the desired state in Git  
D) It requires manual intervention every time

**Your answer:** _____

---

## Section 2: ArgoCD and GitOps (20 points)

### Question 6 (5 points)
What does "continuous reconciliation" mean in the context of ArgoCD?

A) ArgoCD deploys once and never checks the cluster again  
B) ArgoCD periodically syncs on a fixed schedule only  
C) ArgoCD continuously monitors and corrects differences between desired and live state  
D) ArgoCD only reconciles when manually triggered

**Your answer:** _____

---

### Question 7 (5 points)
Which GitOps principle does ArgoCD support by using Git as the source of truth?

A) Imperative configuration management  
B) Declarative configuration with versioning and immutability  
C) Manual deployment processes  
D) Direct cluster modifications

**Your answer:** _____

---

### Question 8 (5 points)
True or False: ArgoCD requires write access credentials to the Kubernetes cluster to be stored in the CI/CD pipeline.

**Your answer:** _____

---

### Question 9 (5 points)
What happens when ArgoCD detects that the live cluster state differs from the desired state in Git?

A) It logs the difference but does nothing  
B) It automatically or manually (based on policy) synchronizes to restore the desired state  
C) It deletes the application  
D) It creates a new cluster

**Your answer:** _____

---

## Section 3: ArgoCD and Continuous Delivery (20 points)

### Question 10 (5 points)
In a CD workflow with ArgoCD, what is the primary responsibility of ArgoCD?

A) Building and compiling application code  
B) Running automated tests  
C) Deploying applications and configurations to Kubernetes  
D) Managing source code repositories

**Your answer:** _____

---

### Question 11 (5 points)
How does the CI pipeline typically interact with ArgoCD in a GitOps workflow?

A) CI pushes directly to the Kubernetes cluster  
B) CI updates manifests in a GitOps repository, which ArgoCD monitors  
C) CI manually triggers ArgoCD via API calls  
D) CI doesn't interact with ArgoCD at all

**Your answer:** _____

---

### Question 12 (5 points)
True or False: ArgoCD handles both the CI (Continuous Integration) and CD (Continuous Delivery) phases of the software delivery pipeline.

**Your answer:** _____

---

### Question 13 (5 points)
What is a key benefit of using ArgoCD for the deployment phase of CD?

A) Faster code compilation  
B) Automatic code review  
C) Declarative deployments with Git-based auditability and rollback  
D) Improved developer laptop performance

**Your answer:** _____

---

## Section 4: ArgoCD and Kubernetes (20 points)

### Question 14 (5 points)
How are ArgoCD applications defined in Kubernetes?

A) As Docker images  
B) As Custom Resource Definitions (CRDs)  
C) As environment variables  
D) As ConfigMaps only

**Your answer:** _____

---

### Question 15 (5 points)
Which configuration management tools does ArgoCD support? (Choose the MOST complete answer)

A) Only plain Kubernetes YAML manifests  
B) Only Helm charts  
C) Kubernetes manifests, Helm, Kustomize, Jsonnet, and custom plugins  
D) Only Terraform files

**Your answer:** _____

---

### Question 16 (5 points)
True or False: ArgoCD configurations are portable between Kubernetes clusters regardless of the underlying infrastructure.

**Your answer:** _____

---

### Question 17 (5 points)
What does the ArgoCD `syncPolicy: automated: {}` configuration enable?

A) Manual approval required for all deployments  
B) Automatic synchronization of changes from Git to the cluster  
C) Automatic cluster scaling  
D) Automatic backup of cluster data

**Your answer:** _____

---

## Section 5: ArgoCD Features and Best Practices (15 points)

### Question 18 (5 points)
What does the ArgoCD web UI enable users to do?

A) Write application code  
B) Visualize and interact with Kubernetes resources, manage applications, and monitor sync/health status  
C) Create Git repositories  
D) Design infrastructure architecture

**Your answer:** _____

---

### Question 19 (5 points)
True or False: In a GitOps workflow with ArgoCD, it is recommended to keep application source code and Kubernetes configuration manifests in the same repository.

**Your answer:** _____

---

### Question 20 (5 points)
What is the "App of Apps" pattern in ArgoCD?

A) Running multiple instances of the same application  
B) Managing multiple applications as a single unit where one ArgoCD Application manages other Applications  
C) Using multiple ArgoCD servers  
D) Deploying applications to multiple regions simultaneously

**Your answer:** _____

---

## Total Score: _____ / 100

---

## Grading Scale

Calculate your percentage and find your level:

- **90-100 points (90-100%)**: **ArgoCD Expert** - Outstanding understanding! You're ready to implement and advocate for ArgoCD in production environments.

- **80-89 points (80-89%)**: **Advanced Practitioner** - Strong grasp of ArgoCD concepts. Review any missed questions to solidify your expertise.

- **70-79 points (70-79%)**: **Intermediate** - Good foundation in ArgoCD principles. Consider deeper study of topics you found challenging.

- **60-69 points (60-69%)**: **Beginner** - You understand the basics. Review the README materials more thoroughly, especially sections related to missed questions.

- **Below 60 points (<60%)**: **Novice** - Take time to carefully review the ArgoCD introduction materials and try the quiz again.

---

**Next Steps:**
1. Check your answers in `quiz-answers.md`
2. Calculate your total score
3. Review any sections where you had incorrect answers
4. Retake the quiz after studying to track your improvement!

**Hands-On Practice:**
- Set up ArgoCD in a test Kubernetes cluster
- Deploy a sample application using GitOps principles
- Experiment with sync policies and drift detection
- Explore the ArgoCD web UI and its features


