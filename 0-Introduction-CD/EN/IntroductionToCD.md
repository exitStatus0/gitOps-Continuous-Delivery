# Introduction to Continuous Delivery

Imagine this: your team just fixed a critical bug. The patch is ready, tested, and approved. But it won't reach users for another two weeks — because that's when the next release window opens. Meanwhile, customers are frustrated, support tickets pile up, and your competitors ship faster. Sound familiar?

This is the problem Continuous Delivery was built to solve.

<p align="center">
  <img src="../ContinuousDelivery.png" alt="Continuous Delivery Overview" width="700"/>
</p>

## What is Continuous Delivery?

Continuous Delivery (CD) represents a fundamental shift in how modern software organizations deliver value to their users. As articulated by Jez Humble on [continuousdelivery.com](https://continuousdelivery.com):

> "Continuous Delivery is the ability to get changes of all types—including new features, configuration changes, bug fixes and experiments—into production, or into the hands of users, safely and quickly in a sustainable way."

Much like DevOps, Continuous Delivery is not merely a set of tools or practices—it represents both a **technological** and **cultural** transformation for an organization. It requires a fundamental shift in mindset, processes, and team collaboration patterns to achieve truly sustainable delivery practices.

## What Problems Does Continuous Delivery Solve?

Continuous Delivery addresses several critical challenges that organizations face when releasing software:

### Automating Error-Prone Manual Processes

CD automates the manual, error-prone process of releasing code into production (or any environment). By removing human error from repetitive deployment tasks, organizations can achieve more reliable and consistent releases.

### Codifying Knowledge

The goal is to **codify** the specialized knowledge from both developers and operators responsible for releasing the software. This frees them from the toil of releases, allowing them to focus on delivering value and solving meaningful business problems. When release processes are automated and documented as code, organizational knowledge becomes transferable and resilient.

### Improving Visibility

Codifying the release process dramatically improves **visibility** into the deployment pipeline. The steps required to go from a build to running in production are clearly laid out and made accessible. This transparency helps identify constraints to developer productivity and encourages a collaborative approach to improving daily work.

### Accelerating Time-to-Market

Automating the release of code changes **speeds up** the delivery of value to customers. Organizations can transition from waiting weeks or months before seeing changes in production to having them in the hands of users within days or even hours. This rapid feedback loop enables faster iteration and learning.

### Enabling Scalability

**Scaling** a release process that depends on human operators requires finding qualified personnel and training them—a time-consuming and expensive proposition. Continuous Delivery can be scaled through improvements to the automated process itself, which persist well into the future without requiring proportional increases in headcount.

### Infrastructure as Code

Continuous Delivery naturally encompasses the underlying infrastructure and configuration for environments. This leads to a deeper understanding of how environments are composed and allows them to be easily reproduced. By keeping lower environments as production-like as possible, organizations can significantly reduce the risk of problems on release due to inconsistencies between environments.

## How Does Continuous Delivery Differ From Continuous Integration?

Continuous Integration (CI) and Continuous Delivery (CD) are commonly found together and often referred to as one unified practice (CI/CD). However, they are distinct concepts, though deeply entangled since **CI is an essential prerequisite for CD**.

### Continuous Integration (CI)

**CI** focuses on regularly merging code into a centralized branch. Its primary goal is detecting issues with the source code early in the development cycle using automated testing and linting. This provides rapid feedback to developers, enabling them to create value faster and fix issues when it's less costly to do so.

### Continuous Delivery (CD)

**CD** takes the changes that have been tested and integrated into the codebase and automates their deployment into an environment.

### The Build Process: CI or CD?

The build process itself can be considered part of either CI or CD, depending on the implementation:

- If automated tests run against the build, it's typically considered **CI**
- If the build is not created until after the code has been integrated into the main branch and becomes part of the deployment pipeline into an environment, then it's **CD**

## What About the Other CD? Continuous Deployment vs. Continuous Delivery

You may have encountered Continuous Deployment, which is often abbreviated as CD just like Continuous Delivery. While both practices are related, they have distinct meanings and implications.

### Continuous Delivery

**Continuous Delivery** automates deploying a build artifact into an environment. Typically, the production release is gated with a requirement for a human to approve it manually. This practice doesn't necessarily account for promotion between environments (e.g., from staging to production) or provide built-in mechanisms for rollback decisions—these remain human-controlled decisions.

### Continuous Deployment

**Continuous Deployment** takes automation further by implementing the practice of automating the entire deployment lifecycle for an application **without any human intervention**. 

For example, once code reaches the repository's main branch, it will automatically:
1. Go through testing
2. Generate a build
3. Release into a staging environment
4. Promote to production

The automated system only stops the progression if tests fail or a problem is detected from telemetry (e.g., too many 500 status codes or errors in the application logs), automatically triggering a rollback.

### Achieving Continuous Deployment

Getting to Continuous Deployment requires complete incorporation of both CI and CD (Continuous Delivery) practices, with sufficient confidence built into the automated testing, monitoring, and rollback mechanisms to remove manual release gates entirely. It represents the pinnacle of deployment automation maturity.

## Key Takeaways

To solidify your understanding of Continuous Delivery, consider these important points:

1. **CD is a transformation**: Continuous Delivery is both a technological and cultural transformation for an organization, not just a set of tools.

2. **Focus is on automation**: CD is a software development practice that focuses on getting changes of all types into production, or the hands of users, safely and quickly in a sustainable way.

3. **Not about eliminating people**: The goal is not to save costs by eliminating staff required to manage releases. Rather, it's to free engineers from the toil of releases so they can focus on generating value and solving business problems.

4. **Automation over manual processes**: CD focuses on automating the release of code changes, not depending on qualified personnel following manual processes.

5. **CI is essential**: Continuous Integration is not unrelated to Continuous Delivery—CI is an essential prerequisite for implementing CD successfully.

6. **Continuous Deployment is optional**: While Continuous Deployment represents an advanced evolution of CD practices, it is not an essential part of Continuous Delivery. Many successful organizations practice CD with manual approval gates for production releases.

## Benefits of Implementing Continuous Delivery

Organizations that successfully adopt CD gain significant advantages:

- **Faster time-to-market** — changes reach users in hours instead of weeks
- **Reduced risk** — smaller, more frequent releases mean a smaller blast radius for potential issues
- **Improved quality** — automated testing and standardized processes raise the quality bar
- **Better collaboration** — teams work more cohesively through shared goals and transparency
- **Higher productivity** — engineers are freed from repetitive tasks to focus on meaningful work
- **Cost savings** — automation reduces manual effort and the cost of fixing errors caught late

---

## Further Learning

To deepen your knowledge of Continuous Delivery:

- Visit [continuousdelivery.com](https://continuousdelivery.com) for authoritative resources
- Read "Continuous Delivery" by Jez Humble and David Farley
- Explore GitOps practices as a modern implementation pattern for CD
- Investigate tools that support CD pipelines in your technology stack

Remember: The journey to Continuous Delivery is iterative. Start small, automate incrementally, and continuously improve your processes based on feedback and metrics.

---

[Back to Course Overview](../../README.md) | [Next: Introduction to GitOps](../../1-Intrduction-GitOps/EN/IntroductionToGitOps.md)

