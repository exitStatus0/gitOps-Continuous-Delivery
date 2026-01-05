# GitOps Knowledge Assessment

Test your understanding of GitOps principles, practices, and implementation strategies!

**Instructions:**
- Answer all questions honestly without referring to the materials
- Write down your answers (A, B, C, D or True/False)
- Check your responses using the `quiz-answers.md` file
- Calculate your final score using the rating system provided

---

## Section 1: Core GitOps Principles (25 points)

### Question 1 (5 points)
Which principle states that the desired system state must be expressed declaratively?

A) Pulled Automatically  
B) Declarative  
C) Continuously Reconciled  
D) Versioned and Immutable

**Your answer:** _____

---

### Question 2 (5 points)
What does the "Versioned and Immutable" principle ensure in GitOps?

A) Faster deployments to production  
B) Automatic scaling of applications  
C) Complete version history with immutable records of all changes  
D) Reduced infrastructure costs

**Your answer:** _____

---

### Question 3 (5 points)
In GitOps, how do software agents obtain the desired state declarations?

A) They push changes from CI/CD pipelines  
B) They automatically pull from the source repository  
C) System administrators manually configure them  
D) They generate the desired state dynamically

**Your answer:** _____

---

### Question 4 (5 points)
What does "Continuously Reconciled" mean in the context of GitOps?

A) Regular team meetings to discuss infrastructure  
B) Periodic manual checks of system configuration  
C) Software agents observe actual state and continuously apply desired state  
D) Automated billing reconciliation for cloud resources

**Your answer:** _____

---

### Question 5 (5 points)
True or False: In GitOps, Git serves as the single source of truth for both infrastructure and application definitions.

**Your answer:** _____

---

## Section 2: Push vs. Pull Models (20 points)

### Question 6 (5 points)
What is a key characteristic of the traditional push deployment model?

A) GitOps operator pulls changes automatically  
B) CI/CD pipeline directly applies manifests to the Kubernetes API  
C) No credentials are required for deployments  
D) The system self-heals automatically

**Your answer:** _____

---

### Question 7 (5 points)
Which statement best describes the pull model used in GitOps?

A) CI/CD pushes changes directly to the cluster  
B) Developers manually deploy changes  
C) A GitOps operator monitors Git and pulls changes to apply them  
D) Changes are deployed through kubectl commands

**Your answer:** _____

---

### Question 8 (5 points)
What security advantage does the pull model provide over the push model?

A) Faster deployment speeds  
B) No write credentials or direct cluster access needed in CI/CD pipeline  
C) Automatic security scanning of containers  
D) Built-in encryption of all data

**Your answer:** _____

---

### Question 9 (5 points)
True or False: The push model is considered "declarative" because it defines the exact steps to achieve deployment.

**Your answer:** _____

---

## Section 3: GitOps and Continuous Delivery (20 points)

### Question 10 (5 points)
How does GitOps relate to Continuous Delivery?

A) They are competing practices that cannot be used together  
B) GitOps manages environment state while CD automates the flow of changes  
C) GitOps has replaced the need for Continuous Delivery  
D) They are identical practices with different names

**Your answer:** _____

---

### Question 11 (5 points)
True or False: GitOps and Continuous Delivery are unrelated methodologies that serve different purposes.

**Your answer:** _____

---

### Question 12 (5 points)
In a combined CD and GitOps workflow, what triggers the GitOps operator to act?

A) Manual approval from operations team  
B) Changes detected in the GitOps configuration repository  
C) Direct commands from CI/CD pipeline  
D) Scheduled cron jobs

**Your answer:** _____

---

### Question 13 (5 points)
What is the primary focus of Continuous Delivery in the CD/GitOps relationship?

A) Managing infrastructure state  
B) Monitoring application performance  
C) Automating the software release pipeline  
D) Configuring network policies

**Your answer:** _____

---

## Section 4: Benefits and Implementation (20 points)

### Question 14 (5 points)
Which benefit does GitOps provide for disaster recovery?

A) Automatic backups to multiple clouds  
B) Environments can be easily recreated from Git repository  
C) Reduced hardware costs  
D) Faster network speeds

**Your answer:** _____

---

### Question 15 (5 points)
How does GitOps improve collaboration among team members?

A) By eliminating the need for communication  
B) Through automated meeting scheduling  
C) Via Pull Requests that enable review similar to code changes  
D) By assigning tasks automatically

**Your answer:** _____

---

### Question 16 (5 points)
True or False: GitOps is only suitable for large enterprises with complex infrastructure needs.

**Your answer:** _____

---

### Question 17 (5 points)
What advantage does declarative configuration provide in GitOps?

A) Faster execution time  
B) Lower licensing costs  
C) Deployments become repeatable and environments easily recreated  
D) Automatic scaling decisions

**Your answer:** _____

---

## Section 5: Advanced Concepts (15 points)

### Question 18 (5 points)
In Kubernetes context, what does a GitOps operator do?

A) Creates new container images  
B) Monitors Git repo and applies Kubernetes manifests to the cluster  
C) Writes application code  
D) Manages developer access permissions

**Your answer:** _____

---

### Question 19 (5 points)
What happens when drift is detected in a GitOps-managed system?

A) An alert is sent but no action is taken  
B) The system shuts down for safety  
C) The operator automatically reconciles to match the desired state in Git  
D) Manual intervention is always required

**Your answer:** _____

---

### Question 20 (5 points)
True or False: The system's desired state with immutable versions must be stored declaratively, and a software agent reconciles the actual state with this desired state.

**Your answer:** _____

---

## Total Score: _____ / 100

---

## Rating Scale

Evaluate your GitOps expertise based on your score:

- **90-100 points (90-100%)**: **GitOps Expert** - Exceptional understanding! You're ready to lead GitOps initiatives and mentor others in implementation strategies.

- **80-89 points (80-89%)**: **Advanced Practitioner** - Strong grasp of GitOps concepts. Review any missed questions to perfect your expertise.

- **70-79 points (70-79%)**: **Intermediate** - Solid foundation in GitOps principles. Deepen your knowledge in areas where you struggled.

- **60-69 points (60-69%)**: **Novice** - You understand the basics. Study the README materials more thoroughly, especially sections related to missed questions.

- **Below 60 points (<60%)**: **Beginner** - Take time to carefully review the GitOps introduction materials. GitOps concepts take practice to fully grasp.

---

**Next Steps:**
1. Check your answers in `quiz_answers.md`
2. Calculate your total score
3. Review sections where you had incorrect answers
4. Retake the quiz after studying to track your improvement!

**Additional Practice:**
- Set up a GitOps operator in a test environment
- Practice creating declarative Kubernetes manifests
- Experiment with different repository structures
- Explore real-world GitOps implementations

