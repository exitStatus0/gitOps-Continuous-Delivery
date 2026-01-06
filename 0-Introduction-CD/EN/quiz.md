# Continuous Delivery Quiz

Test your knowledge of Continuous Delivery concepts and practices!

**Instructions:**
- Answer all questions to the best of your ability
- Click "Click to see answer" below each question to reveal the correct answer and explanation
- Calculate your score using the rating scale at the end

---

## Section 1: Understanding Continuous Delivery (20 points)

### Question 1 (5 points)
What is Continuous Delivery?

A) A tool for automating deployments  
B) The ability to get changes of all types into production safely and quickly in a sustainable way  
C) A practice focused only on deploying to production environments  
D) A replacement for manual testing

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - The ability to get changes of all types into production safely and quickly in a sustainable way

**Explanation:** This is the definition provided by Jez Humble on continuousdelivery.com. CD is not just a tool or practice, but a comprehensive approach to software delivery.

</details>

---
### Question 2 (5 points)
Continuous Delivery is best described as:

A) Only a technological transformation  
B) Only a cultural transformation  
C) Both a technological and cultural transformation  
D) A set of deployment tools

<details>
<summary>Click to see answer</summary>

**Correct Answer: C** - Both a technological and cultural transformation

**Explanation:** Like DevOps, CD requires changes to both technology (tools, automation, processes) and culture (mindset, collaboration, ways of working).

</details>

---
### Question 3 (5 points)
According to Jez Humble, Continuous Delivery includes which types of changes?

A) Only new features  
B) Only bug fixes  
C) New features, configuration changes, bug fixes, and experiments  
D) Only configuration changes

<details>
<summary>Click to see answer</summary>

**Correct Answer: C** - New features, configuration changes, bug fixes, and experiments

**Explanation:** CD encompasses ALL types of changes, not just one category. This comprehensive approach ensures consistent and reliable delivery regardless of change type.

</details>

---
### Question 4 (5 points)
True or False: Continuous Delivery is similar to DevOps in that both require organizational transformation, not just technical changes.

<details>
<summary>Click to see answer</summary>

**Correct Answer: True**

**Explanation:** Both CD and DevOps require fundamental shifts in how organizations think about and approach software delivery, involving people, processes, and technology.

</details>

---

## Section 2: Problems CD Solves (25 points)
<details>
<summary>Click to see answer</summary>

**Correct Answer: True**

**Explanation:** Both CD and DevOps require fundamental shifts in how organizations think about and approach software delivery, involving people, processes, and technology.

---

## Section 2: Problems CD Solves (25 points)

</details>

---
### Question 5 (5 points)
What is the primary goal of codifying the release process?

A) To eliminate all developers from the release process  
B) To free developers and operators from the toil of releases so they can focus on delivering value  
C) To reduce the cost of software licenses  
D) To make the code more complex

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - To free developers and operators from the toil of releases so they can focus on delivering value

**Explanation:** The goal is not to eliminate people, but to free them from repetitive, low-value work so they can focus on solving business problems and creating value.

</details>

---
### Question 6 (5 points)
True or False: Continuous Delivery saves costs by eliminating the staff required to manage releases.

<details>
<summary>Click to see answer</summary>

**Correct Answer: False**

**Explanation:** This is a common misconception. The goal is NOT to eliminate staff but to free engineers from the toil of releases to focus on generating value and solving business problems.

</details>

---
### Question 7 (5 points)
How does Continuous Delivery improve visibility?

A) By adding more monitoring tools  
B) By making the steps from build to production clear and accessible  
C) By creating more documentation  
D) By hiring more project managers

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - By making the steps from build to production clear and accessible

**Explanation:** Codifying the release process makes all steps explicit and visible, helping identify bottlenecks and constraints to developer productivity.

</details>

---
### Question 8 (5 points)
What timeframe improvement can Continuous Delivery provide for getting changes to users?

A) From weeks/months to days/hours  
B) From days to weeks  
C) From hours to months  
D) No significant time improvement

<details>
<summary>Click to see answer</summary>

**Correct Answer: A** - From weeks/months to days/hours

**Explanation:** CD dramatically accelerates delivery by automating manual processes, allowing organizations to go from lengthy release cycles to rapid, frequent deployments.

</details>

---
### Question 9 (5 points)
How does Continuous Delivery help with scaling?

A) By requiring more qualified personnel  
B) Through improvements to the automated process that persist into the future  
C) By making the process more complex  
D) By reducing the number of deployments

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Through improvements to the automated process that persist into the future

**Explanation:** Unlike manual processes that require hiring and training more people, automated CD processes can be scaled through process improvements that remain valuable over time.

</details>

---

## Section 3: CI vs CD (20 points)
<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Through improvements to the automated process that persist into the future

**Explanation:** Unlike manual processes that require hiring and training more people, automated CD processes can be scaled through process improvements that remain valuable over time.

---

## Section 3: CI vs CD (20 points)

</details>

---
### Question 10 (5 points)
What is the relationship between Continuous Integration (CI) and Continuous Delivery (CD)?

A) They are completely unrelated  
B) CI is an essential prerequisite for CD  
C) CD must be implemented before CI  
D) They are the same thing

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - CI is an essential prerequisite for CD

**Explanation:** While CI and CD are distinct practices, CI must be in place before CD can be effectively implemented. They are entangled but CI comes first.

</details>

---
### Question 11 (5 points)
Continuous Integration (CI) primarily focuses on:

A) Deploying to production  
B) Regularly merging code into a centralized branch and detecting issues early  
C) Managing infrastructure  
D) Writing documentation

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Regularly merging code into a centralized branch and detecting issues early

**Explanation:** CI is about frequent integration and early detection of issues through automated testing and linting, providing quick feedback to developers.

</details>

---
### Question 12 (5 points)
What does Continuous Delivery (CD) do with tested and integrated code?

A) Archives it for future use  
B) Sends it back to developers  
C) Automates its deployment into an environment  
D) Deletes it

<details>
<summary>Click to see answer</summary>

**Correct Answer: C** - Automates its deployment into an environment

**Explanation:** CD takes the tested, integrated code from CI and automates the deployment process into various environments.

</details>

---
### Question 13 (5 points)
The build process can be considered CI if:

A) It runs after deployment  
B) Automated tests run against the build  
C) It never creates artifacts  
D) It only runs manually

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Automated tests run against the build

**Explanation:** When automated tests run against a build, it's performing the integration testing function of CI. If the build happens as part of deployment, it's CD.

</details>

---

## Section 4: Continuous Deployment vs Continuous Delivery (20 points)
<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Automated tests run against the build

**Explanation:** When automated tests run against a build, it's performing the integration testing function of CI. If the build happens as part of deployment, it's CD.

---

## Section 4: Continuous Deployment vs Continuous Delivery (20 points)

</details>

---
### Question 14 (5 points)
What is the main difference between Continuous Delivery and Continuous Deployment?

A) Continuous Deployment requires human approval for production releases  
B) Continuous Deployment automates the entire deployment lifecycle without human intervention  
C) They are exactly the same  
D) Continuous Delivery is newer than Continuous Deployment

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Continuous Deployment automates the entire deployment lifecycle without human intervention

**Explanation:** Continuous Delivery typically requires human approval for production, while Continuous Deployment is fully automated end-to-end without manual gates.

</details>

---
### Question 15 (5 points)
True or False: Continuous Deployment is an essential part of Continuous Delivery.

<details>
<summary>Click to see answer</summary>

**Correct Answer: False**

**Explanation:** Continuous Deployment is an advanced evolution of CD practices, but it is NOT essential. Many successful organizations practice CD with manual approval gates for production releases.

</details>

---
### Question 16 (5 points)
In Continuous Delivery, production releases typically:

A) Are fully automated without any gates  
B) Require human approval manually  
C) Never happen  
D) Only occur on weekends

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Require human approval manually

**Explanation:** CD automates the deployment process but typically gates production releases with a manual approval step, unlike Continuous Deployment which is fully automated.

</details>

---
### Question 17 (5 points)
Continuous Deployment stops progression when:

A) A developer requests it  
B) Tests fail or problems are detected from telemetry  
C) It's the end of the day  
D) The code is too complex

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Tests fail or problems are detected from telemetry

**Explanation:** Continuous Deployment relies on automated checks (tests, monitoring, telemetry) to determine if deployment should continue or trigger a rollback.

</details>

---

## Section 5: Key Concepts and Best Practices (15 points)
<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Tests fail or problems are detected from telemetry

**Explanation:** Continuous Deployment relies on automated checks (tests, monitoring, telemetry) to determine if deployment should continue or trigger a rollback.

---

## Section 5: Key Concepts and Best Practices (15 points)

</details>

---
### Question 18 (5 points)
True or False: Continuous Delivery depends heavily on qualified personnel following manual processes to deploy changes.

<details>
<summary>Click to see answer</summary>

**Correct Answer: False**

**Explanation:** This is the opposite of CD! CD focuses on AUTOMATING the release of code changes, not depending on qualified personnel following manual processes.

</details>

---
### Question 19 (5 points)
What does Continuous Delivery help organizations understand better?

A) Programming languages  
B) How environments are composed and how to reproduce them  
C) Employee satisfaction  
D) Marketing strategies

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - How environments are composed and how to reproduce them

**Explanation:** By encompassing infrastructure and configuration, CD leads to better understanding of environments and the ability to easily reproduce them (Infrastructure as Code).

</details>

---
### Question 20 (5 points)
Keeping lower environments as production-like as possible helps to:

A) Increase costs  
B) Reduce the risk of problems on release due to inconsistencies between environments  
C) Make development slower  
D) Confuse developers

<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Reduce the risk of problems on release due to inconsistencies between environments

**Explanation:** Environment parity reduces the "works on my machine" problem and catches environment-specific issues earlier in the pipeline.

</details>

---

## Total Score: _____ / 100

---

## Rating Scale

Calculate your percentage and find your level:

- **90-100 points (90-100%)**: **Expert** - Excellent understanding of Continuous Delivery! You're ready to implement and champion CD practices in your organization.

- **80-89 points (80-89%)**: **Advanced** - Strong grasp of CD concepts. Review the areas where you missed questions to solidify your expertise.

- **70-79 points (70-79%)**: **Intermediate** - Good foundation in CD principles. Consider deeper study of the topics you found challenging.

- **60-69 points (60-69%)**: **Basic** - You understand the fundamentals but need more practice. Review the README materials and retake the quiz.

- **Below 60 points (<60%)**: **Beginner** - Take time to thoroughly read through the Continuous Delivery introduction materials and try the quiz again.

---

**Next Steps:**
1. Calculate your score (each correct answer is worth the points shown)
2. Review any topics where you had incorrect answers
3. Retake the quiz after studying to improve your score!
<details>
<summary>Click to see answer</summary>

**Correct Answer: B** - Reduce the risk of problems on release due to inconsistencies between environments

**Explanation:** Environment parity reduces the "works on my machine" problem and catches environment-specific issues earlier in the pipeline.

---

## Scoring Section

**Calculate Your Score:**

Count the number of correct answers and multiply by the points for each question:
- Section 1: _____ / 20 points
- Section 2: _____ / 25 points
- Section 3: _____ / 20 points
- Section 4: _____ / 20 points
- Section 5: _____ / 15 points

**Total Score: _____ / 100 points**

---

## Rating Scale

**Your Level:**

- **90-100 points (90-100%)**: **Expert** ⭐⭐⭐⭐⭐
  - Outstanding! You have excellent understanding of Continuous Delivery
  - You're ready to implement and champion CD practices in your organization
  - Consider mentoring others or leading CD initiatives

- **80-89 points (80-89%)**: **Advanced** ⭐⭐⭐⭐
  - Strong grasp of CD concepts
  - Review the areas where you missed questions to solidify your expertise
  - You can confidently participate in CD implementation discussions

- **70-79 points (70-79%)**: **Intermediate** ⭐⭐⭐
  - Good foundation in CD principles
  - Consider deeper study of the topics you found challenging
  - Practice applying these concepts to real-world scenarios

- **60-69 points (60-69%)**: **Basic** ⭐⭐
  - You understand the fundamentals but need more practice
  - Review the README materials thoroughly
  - Focus on understanding the "why" behind CD practices

- **Below 60 points (<60%)**: **Beginner** ⭐
  - Take time to thoroughly read through the Continuous Delivery introduction materials
  - Don't be discouraged - CD is a complex topic!
  - Try the quiz again after studying

---

## Areas for Improvement

Based on which sections you struggled with:

- **Section 1 (Understanding CD)**: Review `README_EN.md` - "What is Continuous Delivery?" section
- **Section 2 (Problems CD Solves)**: Review `README_EN.md` - "What Problems Does Continuous Delivery Solve?" section
- **Section 3 (CI vs CD)**: Review `README_EN.md` - "How Does Continuous Delivery Differ From Continuous Integration?" section
- **Section 4 (Deployment vs Delivery)**: Review `README_EN.md` - "What about the other CD?" section
- **Section 5 (Key Concepts)**: Review `README_EN.md` - "Key Takeaways" section

---

## Next Steps

1. **If you scored 80+**: Congratulations! Consider reading more advanced materials on CD implementation strategies and GitOps practices.

2. **If you scored 60-79**: Good progress! Review the sections where you missed questions, then retake the quiz in a few days.

3. **If you scored below 60**: Don't worry! Read through the README materials carefully, take notes, and try the quiz again when you're ready.

**Additional Resources:**
- Visit [continuousdelivery.com](https://continuousdelivery.com)
- Read "Continuous Delivery" by Jez Humble and David Farley
- Explore practical CD implementation guides
- Join DevOps and CD communities online

Keep learning! Continuous Delivery is a journey, not a destination. 🚀

</details>

---
