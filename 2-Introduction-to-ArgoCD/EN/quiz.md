# ArgoCD Knowledge Assessment

Test your understanding of ArgoCD concepts, architecture, and best practices!

**Instructions:**
- Answer all questions to the best of your ability
- Record your answers (A, B, C, D, or True/False)
- Click on "Натисніть, щоб побачити відповідь" to reveal the correct answer and explanation
- Calculate your score using the grading scale at the end

---

## Section 1: ArgoCD Fundamentals (25 points)

### Question 1 (5 points)
What is ArgoCD?

A) A CI/CD platform for building and testing applications  
B) A declarative, GitOps continuous delivery tool for Kubernetes  
C) A container registry for storing Docker images  
D) A monitoring tool for Kubernetes clusters
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - A declarative, GitOps continuous delivery tool for Kubernetes

**Explanation:** ArgoCD is specifically designed as a declarative, GitOps-based continuous delivery tool for Kubernetes. It's not a CI platform (A), container registry (C), or monitoring tool (D), though it integrates with those components.

</details>

---
### Question 2 (5 points)
Which architectural pattern does ArgoCD follow for multi-cluster management?

A) Microservices architecture  
B) Hub-and-spoke model  
C) Peer-to-peer architecture  
D) Serverless architecture
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - Hub-and-spoke model

**Explanation:** ArgoCD uses a hub-and-spoke architecture where a central control-plane cluster with ArgoCD manages deployments to multiple target clusters. This centralized approach provides a single pane of glass for managing all clusters.

</details>

---
### Question 3 (5 points)
In the context of GitOps, what role does ArgoCD play?

A) It stores the Git repositories  
B) It acts as the software agent that pulls desired state and reconciles it with live state  
C) It builds container images from source code  
D) It provides the Kubernetes cluster infrastructure
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - It acts as the software agent that pulls desired state and reconciles it with live state

**Explanation:** ArgoCD is the automation agent that implements GitOps principles. It continuously pulls the desired state from Git repositories and reconciles it with the live state in Kubernetes clusters, automatically detecting and correcting drift.

</details>

---
### Question 4 (5 points)
True or False: ArgoCD uses a push-based deployment model where CI/CD pipelines push changes directly to clusters.
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: False**

**Explanation:** ArgoCD uses a **pull-based** model, which is fundamental to GitOps. ArgoCD pulls changes from Git repositories rather than having CI/CD pipelines push changes directly to clusters. This improves security and follows the GitOps principle of "pulled automatically."

</details>

---
### Question 5 (5 points)
How does ArgoCD handle configuration drift?

A) It sends an alert but takes no action  
B) It shuts down the cluster for safety  
C) It automatically reconciles the live state to match the desired state in Git  
D) It requires manual intervention every time

---

## Section 2: ArgoCD and GitOps (20 points)
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: C** - It automatically reconciles the live state to match the desired state in Git

**Explanation:** When ArgoCD detects drift (differences between the desired state in Git and the live state in the cluster), it automatically or manually (depending on sync policy) reconciles the live state to match Git. This self-healing capability is a core feature of ArgoCD.

---

## Section 2: ArgoCD and GitOps (20 points)

</details>

---
### Question 6 (5 points)
What does "continuous reconciliation" mean in the context of ArgoCD?

A) ArgoCD deploys once and never checks the cluster again  
B) ArgoCD periodically syncs on a fixed schedule only  
C) ArgoCD continuously monitors and corrects differences between desired and live state  
D) ArgoCD only reconciles when manually triggered
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: C** - ArgoCD continuously monitors and corrects differences between desired and live state

**Explanation:** Continuous reconciliation is the process where ArgoCD constantly compares the desired state (defined in Git) with the live state (in the cluster) and automatically corrects any differences. This ensures the cluster always stays in sync with Git.

</details>

---
### Question 7 (5 points)
Which GitOps principle does ArgoCD support by using Git as the source of truth?

A) Imperative configuration management  
B) Declarative configuration with versioning and immutability  
C) Manual deployment processes  
D) Direct cluster modifications
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - Declarative configuration with versioning and immutability

**Explanation:** By using Git as the single source of truth, ArgoCD supports the GitOps principles of declarative configuration (defining what should exist) with versioning (Git history) and immutability (Git commits are immutable). This contrasts with imperative approaches that define how to achieve a state.

</details>

---
### Question 8 (5 points)
True or False: ArgoCD requires write access credentials to the Kubernetes cluster to be stored in the CI/CD pipeline.
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: False**

**Explanation:** This is a key security benefit of ArgoCD! Since ArgoCD runs inside the cluster and pulls from Git, the CI/CD pipeline doesn't need write access to the cluster. The CI pipeline only needs to update Git, and ArgoCD handles the deployment. This reduces the attack surface and follows the principle of least privilege.

</details>

---
### Question 9 (5 points)
What happens when ArgoCD detects that the live cluster state differs from the desired state in Git?

A) It logs the difference but does nothing  
B) It automatically or manually (based on policy) synchronizes to restore the desired state  
C) It deletes the application  
D) It creates a new cluster

---

## Section 3: ArgoCD and Continuous Delivery (20 points)
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - It automatically or manually (based on policy) synchronizes to restore the desired state

**Explanation:** When drift is detected, ArgoCD's behavior depends on the sync policy. With auto-sync enabled, it immediately reconciles. With manual sync, it alerts users but waits for manual approval. Either way, it can restore the desired state from Git.

---

## Section 3: ArgoCD and Continuous Delivery (20 points)

</details>

---
### Question 10 (5 points)
In a CD workflow with ArgoCD, what is the primary responsibility of ArgoCD?

A) Building and compiling application code  
B) Running automated tests  
C) Deploying applications and configurations to Kubernetes  
D) Managing source code repositories
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: C** - Deploying applications and configurations to Kubernetes

**Explanation:** In a CD workflow, ArgoCD focuses specifically on the deployment phase - taking built, tested applications and deploying them to Kubernetes. The CI pipeline handles building (A) and testing (B), while Git handles source code management (D).

</details>

---
### Question 11 (5 points)
How does the CI pipeline typically interact with ArgoCD in a GitOps workflow?

A) CI pushes directly to the Kubernetes cluster  
B) CI updates manifests in a GitOps repository, which ArgoCD monitors  
C) CI manually triggers ArgoCD via API calls  
D) CI doesn't interact with ArgoCD at all
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - CI updates manifests in a GitOps repository, which ArgoCD monitors

**Explanation:** In a proper GitOps workflow, the CI pipeline doesn't interact directly with the cluster or ArgoCD. Instead, it updates Kubernetes manifests (usually with new image tags) in a Git repository, and ArgoCD automatically detects these changes and deploys them. This separation of concerns is key to GitOps.

</details>

---
### Question 12 (5 points)
True or False: ArgoCD handles both the CI (Continuous Integration) and CD (Continuous Delivery) phases of the software delivery pipeline.
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: False**

**Explanation:** ArgoCD focuses on the CD (Continuous Delivery/Deployment) phase only. It doesn't build code, run tests, or create container images - that's the job of CI tools like Jenkins, GitLab CI, or GitHub Actions. ArgoCD takes the artifacts from CI and deploys them to Kubernetes.

</details>

---
### Question 13 (5 points)
What is a key benefit of using ArgoCD for the deployment phase of CD?

A) Faster code compilation  
B) Automatic code review  
C) Declarative deployments with Git-based auditability and rollback  
D) Improved developer laptop performance

---

## Section 4: ArgoCD and Kubernetes (20 points)
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: C** - Declarative deployments with Git-based auditability and rollback

**Explanation:** ArgoCD enables declarative deployments where you define the desired state rather than writing deployment scripts. Since everything is in Git, you get complete audit history of who deployed what and when, plus easy rollback capabilities using `git revert`. It doesn't improve compilation (A), code review (B), or laptop performance (D).

---

## Section 4: ArgoCD and Kubernetes (20 points)

</details>

---
### Question 14 (5 points)
How are ArgoCD applications defined in Kubernetes?

A) As Docker images  
B) As Custom Resource Definitions (CRDs)  
C) As environment variables  
D) As ConfigMaps only
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - As Custom Resource Definitions (CRDs)

**Explanation:** ArgoCD uses Kubernetes CRDs to define applications. This makes ArgoCD Kubernetes-native, allowing administrators to use familiar tools like `kubectl` and YAML to manage ArgoCD applications just like any other Kubernetes resource.

</details>

---
### Question 15 (5 points)
Which configuration management tools does ArgoCD support? (Choose the MOST complete answer)

A) Only plain Kubernetes YAML manifests  
B) Only Helm charts  
C) Kubernetes manifests, Helm, Kustomize, Jsonnet, and custom plugins  
D) Only Terraform files
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: C** - Kubernetes manifests, Helm, Kustomize, Jsonnet, and custom plugins

**Explanation:** ArgoCD is flexible and supports multiple configuration management tools: plain YAML manifests, Helm charts, Kustomize, Jsonnet, and even custom config management plugins. This flexibility allows teams to use their preferred tools.

</details>

---
### Question 16 (5 points)
True or False: ArgoCD configurations are portable between Kubernetes clusters regardless of the underlying infrastructure.
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: True**

**Explanation:** Since ArgoCD uses Kubernetes-native CRDs and standard Kubernetes manifests, configurations are portable across any Kubernetes cluster - whether it's running on AWS, GCP, Azure, on-premises, or even local development clusters like kind or minikube.

</details>

---
### Question 17 (5 points)
What does the ArgoCD `syncPolicy: automated: {}` configuration enable?

A) Manual approval required for all deployments  
B) Automatic synchronization of changes from Git to the cluster  
C) Automatic cluster scaling  
D) Automatic backup of cluster data

---

## Section 5: ArgoCD Features and Best Practices (15 points)
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - Automatic synchronization of changes from Git to the cluster

**Explanation:** Setting `syncPolicy: automated: {}` enables auto-sync, meaning ArgoCD will automatically deploy changes from Git to the cluster without manual intervention. This doesn't control cluster scaling (C) or backups (D), and it specifically removes the need for manual approval (A).

---

## Section 5: ArgoCD Features and Best Practices (15 points)

</details>

---
### Question 18 (5 points)
What does the ArgoCD web UI enable users to do?

A) Write application code  
B) Visualize and interact with Kubernetes resources, manage applications, and monitor sync/health status  
C) Create Git repositories  
D) Design infrastructure architecture
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - Visualize and interact with Kubernetes resources, manage applications, and monitor sync/health status

**Explanation:** The ArgoCD UI is a powerful interface for visualizing Kubernetes resources and their relationships, managing application lifecycles, viewing sync status, checking health status, accessing logs, and triggering manual syncs. It doesn't provide code editing (A), Git repository creation (C), or architecture design tools (D).

</details>

---
### Question 19 (5 points)
True or False: In a GitOps workflow with ArgoCD, it is recommended to keep application source code and Kubernetes configuration manifests in the same repository.
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: False**

**Explanation:** Best practice is to **separate** application source code and Kubernetes configuration manifests into different repositories. This follows the GitOps principle of separating concerns, provides better security (developers don't need access to production configs), and allows for independent versioning and access control.

</details>

---
### Question 20 (5 points)
What is the "App of Apps" pattern in ArgoCD?

A) Running multiple instances of the same application  
B) Managing multiple applications as a single unit where one ArgoCD Application manages other Applications  
C) Using multiple ArgoCD servers  
D) Deploying applications to multiple regions simultaneously

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
1. Calculate your score (each correct answer is worth the points shown)
2. Calculate your total score
3. Review any sections where you had incorrect answers
4. Retake the quiz after studying to track your improvement!

**Hands-On Practice:**
- Set up ArgoCD in a test Kubernetes cluster
- Deploy a sample application using GitOps principles
- Experiment with sync policies and drift detection
- Explore the ArgoCD web UI and its features
<details>
<summary>Натисніть, щоб побачити відповідь</summary>

**Correct Answer: B** - Managing multiple applications as a single unit where one ArgoCD Application manages other Applications

**Explanation:** The "App of Apps" pattern uses one ArgoCD Application that points to a directory containing definitions for multiple other Applications. This parent application manages child applications, making it easy to deploy entire environments or related application sets as a single unit.

---

## Scoring Section

**Calculate your score:**

Count your correct answers and multiply by the points for each question:
- Section 1: _____ / 25 points
- Section 2: _____ / 20 points
- Section 3: _____ / 20 points
- Section 4: _____ / 20 points
- Section 5: _____ / 15 points

**Total Score: _____ / 100 points**

---

## Grading Scale

**Your Proficiency Level:**

- **90-100 points (90-100%)**: **ArgoCD Expert** ⭐⭐⭐⭐⭐
  - Excellent! You have outstanding understanding of ArgoCD
  - You're ready to implement ArgoCD in production environments
  - Consider mentoring others or leading ArgoCD initiatives

- **80-89 points (80-89%)**: **Advanced Practitioner** ⭐⭐⭐⭐
  - Strong understanding of ArgoCD concepts and practices
  - Review missed questions to reinforce your expertise
  - You can confidently deploy and manage ArgoCD in production

- **70-79 points (70-79%)**: **Intermediate** ⭐⭐⭐
  - Good foundation in ArgoCD principles
  - Deepen your knowledge in areas you found challenging
  - Practice implementing ArgoCD in test environments

- **60-69 points (60-69%)**: **Beginner** ⭐⭐
  - You understand the basics but need more study
  - Thoroughly review the README materials
  - Focus on understanding the "why" behind ArgoCD practices

- **Below 60 points (<60%)**: **Novice** ⭐
  - Take time to carefully read the ArgoCD materials
  - ArgoCD concepts require practice to fully understand
  - Try the quiz again after studying

---

## Areas for Improvement

Based on which sections you struggled with:

- **Section 1 (Fundamentals)**: Review the core concepts of ArgoCD, its architecture, and how it handles drift detection and reconciliation.

- **Section 2 (GitOps)**: Study how ArgoCD implements GitOps principles, especially the pull-based model and continuous reconciliation.

- **Section 3 (Continuous Delivery)**: Understand how ArgoCD fits into the broader CD workflow and its interaction with CI pipelines.

- **Section 4 (Kubernetes Integration)**: Learn about CRDs, supported config management tools, and why ArgoCD is Kubernetes-native.

- **Section 5 (Features & Best Practices)**: Explore the ArgoCD UI, repository structure best practices, and patterns like App of Apps.

---

## Next Steps

1. **If you scored 80+**: Excellent work! Consider:
   - Setting up ArgoCD in a production or production-like environment
   - Exploring advanced features like Argo Rollouts for progressive delivery
   - Implementing multi-cluster management
   - Contributing to ArgoCD community or documentation

2. **If you scored 60-79**: Good progress! Action items:
   - Review sections where you missed questions
   - Practice with hands-on ArgoCD implementations
   - Set up a test cluster and deploy sample applications
   - Retake the quiz after additional study

3. **If you scored below 60**: Don't worry! Learning path:
   - Carefully re-read the README materials
   - Take notes on key concepts
   - Watch ArgoCD tutorials or demos
   - Set up a simple ArgoCD instance and experiment
   - Retake the quiz when ready

**Recommended Resources:**
- Visit [ArgoCD Documentation](https://argo-cd.readthedocs.io/)
- Explore [ArgoCD Examples Repository](https://github.com/argoproj/argocd-example-apps)
- Join [ArgoCD Slack Community](https://argoproj.github.io/community/join-slack)
- Watch [CNCF ArgoCD Presentations](https://www.youtube.com/results?search_query=argocd+cncf)
- Practice with [Hands-on ArgoCD Tutorials](https://argo-cd.readthedocs.io/en/stable/getting_started/)

Keep learning! Mastering ArgoCD comes from understanding the principles and hands-on practice. 🚀

</details>

---
