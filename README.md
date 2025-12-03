# kyndryl_20th_platformEngg


```

Sample MCQs for Platform-Engineering / Cloud-Native Platform Exam Prep
Core Platform Engineering & Infrastructure Concepts

Which of these best describes the concept of “Platform as a Product”?
A) Treating platform infrastructure as a one-time project delivered to developers
B) Continuously evolving internal platforms with APIs and self-service for developers
C) Selling platform services externally to clients
D) Using pre-built PaaS from cloud vendors

Answer: B — “Platform as a Product” means building internal platforms (IDPs — internal developer platforms) that are API-driven, self-service, and continuously maintained for developer teams.

What is a primary goal of a Platform Engineer when designing a deployment platform?
A) Maximize manual control over deployments
B) Eliminate all automation to avoid complexity
C) Provide scalable, repeatable, and self-service infrastructure for developers
D) Build separate infrastructure for every application

Answer: C — The platform should enable repeatable, scalable, self-service infrastructure, reducing cognitive and operational load on developers.

Which of the following is a declarative resource management model?
A) Writing imperative scripts for every deployment step
B) Using a manifest (e.g. YAML) to define desired state, letting the platform reconcile actual state
C) Manually configuring servers for each change request
D) Running interactive shell commands for each deployment

Answer: B — Declarative resource management defines what you want (desired state), and the platform (e.g. orchestration engine) ensures the actual state matches.

What is the “reconciliation loop” in orchestration systems such as Kubernetes?
A) A design pattern to revert changes if deployment fails
B) A manual review cycle before every deployment
C) The continuous process where controller compares desired state vs actual state and makes adjustments
D) A rollback mechanism for failed pods

Answer: C — The reconciliation loop periodically or event-driven compares the desired state (as declared) with running state and reconciles differences.

Continuous Delivery, CI/CD, GitOps & Platform Automation

Which practice aligns best with GitOps in a cloud-native platform?
A) All deployment configuration stored and managed via version control; changes applied automatically to reach declared state
B) Doing deployments manually via SSH and scripts
C) Using a central GUI only for deployments
D) Maintaining configurations in spreadsheets and apply manually

Answer: A — GitOps relies on version-controlled config (e.g. Git), and automation ensures the platform converges to declared state.

Why is CI/CD important in a Platform Engineering context?
A) It allows developers to deploy only once a month
B) It ensures reproducible, automated, and consistent deployments, reducing human error
C) It restricts developers from making frequent changes
D) It automatically writes code for developers

Answer: B — CI/CD enables automation, repeatability, consistency, faster feedback loops, and reduces manual error.

If a platform implements GitOps + declarative configs + reconciliation, but a manual change is made directly on the production system, what should happen (ideally)?
A) The manual change stays, because platform tools ignore external edits
B) The reconciliation process overwrites the manual change to match declared state from version control
C) The system crashes
D) The manual change triggers an alert but remains

Answer: B — Ideally, reconciliation ensures the running state matches version-controlled desired state, overriding manual drifts.

Observability, Monitoring & Platform Metrics

Which three pillars belong to the standard “observability” model in cloud-native environments?
A) Logs, ChatOps, Manual Reviews
B) Metrics, Logs, Traces/Events
C) Version Control, Testing, Deployment
D) Security, Compliance, Audits

Answer: B — Observability is commonly framed around metrics, logs, and traces/events, giving insights into system behavior.

What is the benefit of integrating observability into a platform rather than individual applications handling monitoring separately?
A) Centralized telemetry, consistent monitoring standards, easier incident triage across services
B) Makes applications lighter but offers no cross-service view
C) Allows developers to ignore performance
D) It reduces total logs generated

Answer: A — A platform-level observability system ensures unified monitoring, consistent alerting, and simplifies cross-service incident management.

When measuring platform performance, which of the following is least likely to be a focus metric?
A) Deployment frequency
B) Mean Time to Recovery (MTTR)
C) Developer onboarding time
D) Number of manual changes on production

Answer: D — While manual changes might be tracked, platform performance metrics typically emphasize deployment frequency, recovery times, reliability, developer experience, etc.

Security, Policy & Governance in Platforms

What role do “policy engines” play in a cloud-native platform?
A) They write code for developers
B) They enforce rules for resource creation, security, compliance, admission control in platform infrastructure
C) They monitor logs for performance only
D) They scale the infrastructure automatically

Answer: B — Policy engines enforce governance: security policies, RBAC, compliance, admission controls, resource quotas, etc.

Which of these is a recommended approach for securing inter-service communication in microservice environments?
A) Allow all services to communicate freely
B) Use mutual TLS (mTLS) or other service-to-service encryption and enforce network policies
C) Require manual authentication every time services communicate
D) Rely solely on firewall rules

Answer: B — mTLS or equivalent secure communication plus network/policy controls helps ensure secure and authorized service-to-service communication.

Why is integrating security checks (e.g. vulnerability scanning, compliance checks) into CI/CD pipelines considered a best practice?
A) It slows down deployments so fewer changes are made
B) It ensures security and compliance are applied automatically and consistently before production rollout
C) It avoids the need for runtime security tools
D) It reduces resource usage

Answer: B — Embedding security/compliance in CI/CD helps catch vulnerabilities early, enforce standards, and avoid insecure or non-compliant deployments.

Internal Developer Platforms (IDPs), Developer Experience & Platform Goals

What is an “Internal Developer Platform (IDP)”?
A) A platform service sold externally to customers
B) A custom, internal platform providing self-service, automation, tooling to developer teams within an organization
C) A cloud vendor’s public PaaS offering
D) A generic server managed manually

Answer: B — IDPs are internal platforms tailored to teams’ needs, enabling developers to self-service environment provisioning, deployments, and managing their lifecycles.

Which of the following is a key success indicator for an IDP in an organization?
A) Number of manual tickets for infrastructure changes
B) Developer productivity, deployment speed, stability, reduced cognitive load for dev teams
C) Number of servers purchased
D) Variety of programming languages used

Answer: B — An IDP succeeds when it improves developer experience, speeds up delivery, reduces overhead for devs, and increases stability and consistency.

Why might a platform architect choose to implement APIs/CRDs (Custom Resource Definitions) rather than imperative scripts for infrastructure provisioning?
A) CRDs are more verbose
B) APIs/CRDs support declarative, versioned, repeatable infrastructure provisioning; easier automation and self-service
C) Imperative scripts are faster to run
D) Scripts are easier to manage across teams

Answer: B — Declarative APIs/CRDs provide consistent, automated, self-service infrastructure provisioning, and are better suited for platform environments than ad-hoc scripts.

🧠 Extended/Thought-Provoking MCQs (Higher Complexity)

Suppose a platform uses GitOps + orchestration + observability + policy enforcement. A developer manually escalates privileges and deploys a service bypassing the normal pipelines. Which platform vulnerabilities does this scenario reveal? (Select all that apply)
A) Lack of audit trail and governance enforcement
B) Inadequate reconciliation mechanisms
C) Incomplete observability coverage
D) Overuse of automation

Answer: A and C — Without governance enforcement and audit trails, manual privilege escalations can go unnoticed. If observability doesn’t cover security/authorization events, it’s harder to detect such bypasses.

When building an IDP for multiple teams with varying requirements (e.g. different languages, runtimes, deployment patterns), what design principle helps ensure scalability and maintainability of the platform?
A) Hard-code configurations per team
B) Provide generic, parameterized templates + declarative definitions + self-service abstractions (APIs/interfaces)
C) Use separate platforms per team
D) Prevent teams from customizing their environments

Answer: B — Using generic, parameterized abstractions and declarative templates allows one platform to support diverse team requirements while staying maintainable.

What is a potential downside of very aggressive reconciliation loops (e.g. very high frequency) in a platform using declarative infrastructure?
A) Platform becomes too static and never updates
B) High load on control plane / resource churn — might affect performance or lead to race conditions
C) Developers lose productivity completely
D) The system becomes insecure

Answer: B — Frequent reconciliation can put load on control plane, cause unnecessary churn, or lead to contention/race conditions if not optimized.

In context of platform metrics, what does “cognitive load for developers” refer to, and why is it important?
A) The number of servers a developer manages manually — important to reduce manual toil
B) The mental effort required by developers to use, understand, and maintain the platform — lower cognitive load improves developer productivity and reduces errors
C) The number of open-source licenses in use
D) The bandwidth usage of developer tools

Answer: B — Cognitive load refers to mental overhead; minimizing it (via intuitive platforms, self-service tools, abstractions) helps developers focus on building features rather than infrastructure mechanics.

```
