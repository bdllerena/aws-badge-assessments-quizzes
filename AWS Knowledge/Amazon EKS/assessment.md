## .NET Workloads on AWS Lambda

### Q1. As the Lead Engineer for a company that builds a financial management application, you want to move to a Continuous Operations model using GitOps. What are some of the advantages of using GitOps and Continuous Operations? (SELECT 2)

- [x] Git serves as the single source of truth system's desired state.
Comments: In GitOps. Git serves as a single sourth of truth for infrastucture and application state. Changes to that state should be submitted to Git then deployed out to each environment using automation.
- [ ] GitOps can identify tests that are written incorrectly during the continuous testing phase.
Comments: GitOps can run tests that report pass or fail during the test, but it can not identify incorrectly written tests.
- [x] GitOps enables reproducible, automated deployments of your application and infrastructure.
Comments: GitOps uses automated scripts and IAC to ensure a reproducible deployment.
- [ ] GitOps protects your API keys and passwords by securely storing them in version control.
Comments: Storing passwords and keys in source control is not secure
Using GItOps ensures agile development methodologies are being used.
- [ ] Comments: While GitOps can be couple with agile development to improve speed and consistency of applications, GitOps itself does not ensure that these methods are used. Additional team culture components must be implemented outside of GItOps to achieve agile development.

### Q2. A large retail enterprise has an application hosted on EKS. The app in its has a number of microservices, built by different teams using different programming languages(polyglot). They are seeing a lot of timeouts during peak times. Logs and metrics are useful, however it takes a lot of time to narrow down the point of failures and detect performance bottlenecks. This has significantly increased the Mean Time To Resolution (MTTR), leading to poor customer experience and loss of revenue. Given the polyglot nature of the application, auto-instrumentation and standardization is crucial. Another important criteria is that, the organization is currently evaluating several tracing backends and havent finalized one yet. As a chief architect, you are tasked to improve the observability and reduce the overall MTTR. What is your recommended solution?

- [x] Instrument application using AWS Distro for OpenTelemetry (ADOT) SDK, deploy ADOT add-on and collector in EKS cluster to capture and send traces to AWS X-Ray.
Comments: ADOT is a secure, production-ready, AWS-supported distribution of the OpenTelemetry project. It allows you to standardize with open source APIs from upstream OpenTelemetry and supports auto-instrumentation agents to collect traces without changing your code. It also allows you to instrument applications once and send correlated metrics and traces to multiple monitoring solutions.AWS X-Ray is a managed service used to analyze and debug distributed applications. It gives you visual representation of application in form of Service Maps and traces which can help you follow the path of the individual request and narrow down points of failures. As an immediate mitigation to reduce MTTR / customer impact, AWS X-Ray can be used as a tracing solution and it can be easily replaced with other 3rd party solutions later (post evaluation). Since ADOT is used, there will be no need to re-do application instrumentation.
- [ ] Instrument application using X-Ray SDK, deploy X-Ray agent in EKS cluster to capture and send traces to AWS X-Ray.
- [ ] Instrument application using X-Ray SDK, deploy CloudWatch agent in EKS cluster to capture and send traces to AWS X-Ray.
- [ ] Instrument application using Prometheus Library, deploy ADOT add-on and collector in EKS cluster to send correlated metrics and traces to AWS X-Ray.

### Q3. You are a DevOps engineer in a Travel Booking company that has recently deployed its critical application to the Amazon Elastic Kubernetes Service (EKS). During the holiday season, the application experienced a sudden drop in performance, causing disruption to the end users. Following the recent challenges, your manager has emphasized the need for preventive measures to avoid similar issues in the future. Which of the following observability strategies would be the most effective in detecting, investigating, and mitigating the underlying problem in the EKS cluster using metrics?

- [ ] Use FluentBit to aggregate essential metrics and forward them to CloudWatch.
- [ ] Analyze the control plane's metrics and evaluate its scaling configuration for improvements.
- [ ] Increase EKS cluster size and nodes using EKS Metrics data when anomalies are detected.
- [X] Install the CloudWatch agent on your cluster to gather and display metrics from the control and data planes. Set alarms for anomalies and use filters and dashboards to spot unusual patterns.
Comments: On an EKS Cluster, the CloudWatch Agent collects metrics from both data and control planes. Visualize these on the CloudWatch dashboard and set alarms for performance issues.

### Q4. As a Solutions Architect, you are asked to design a Kubernetes environment on AWS for a customer. Which of the following statements BEST describes the components of an EKS cluster?

- [X] EKS clusters contain master nodes that manage scheduling and orchestration, while application pods run on separate worker nodes. Comments: EKS handles provisioning and managing the Kubernetes control plane, while users are responsible for worker nodes that run application workloads. The control plane and worker nodes comprise the full EKS architecture.
- [ ] EKS clusters contain worker nodes that run pods, but the control plane runs on customer infrastructure.
- [ ] EKS does not provide a managed control plane - users must deploy their own Kubernetes masters to create a complete cluster.
- [ ] The customer has full control over both the master and worker nodes, being responsible for managing the underlying EC2 instances.

### Q5. Your team is adopting containers and wants to understand the security best practices for container images. What should the team keep in mind regarding security when working with container images?

- [ ] Encrypting container images provides full protection against security threats.
- [x] Container images should be scanned for vulnerabilities regularly and signed to validate their integrity. Updates should be applied frequently.
Comments: Container images should be scanned for vulnerabilities, signed, and kept up-to-date to maintain security.
- [ ] Container images are inherently secure and do not require any special security considerations.
- [ ] Downloading container images from random online sources is fine as long as they work.

### Q6. 

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q7.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q8.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q9.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q10.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q11.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q12.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q13.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q14.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q15.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q16.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q17.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q18.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q19.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q20.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q21.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q22.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q23.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q24.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q25.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q26.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q27.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q28.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q29.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q30.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q31.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q32.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q33.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q34.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q35.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q36.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q37.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q38.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q39.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q40.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q41.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q42.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q43.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q44.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q45.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q46.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q47.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q48.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q49.

- [ ] 
- [ ] 
- [ ] 
- [ ] 

### Q50.

- [ ] 
- [ ] 
- [ ] 
- [ ] 
