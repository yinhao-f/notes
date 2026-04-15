# DevOps & Info Sec

Learning Outcomes (DevOps):

- What is a microservice architecture? How does it differ from a monolith?
- What is Continuous Delivery/Deployment and what are the key steps?
- What problems does CI/CD aim to solve?
- What problems does DevOps solve in a company?
- How and why do we test in production?

Learning Outcomes (Info Sec):

- Reason about how security requirements interact with software designs and implementations.
- Know how to ideate about security threat scenarios.
- Estimate the risk associated with security threats.
- Describe and apply mitigation principles (defense in depth, least privilege, etc) to abstract and concrete designs.
- Be able to outline how system security can be validated.

## DevOps

### Managing App Deployments at Scale

Monolith Architecture:

- Deploy code on one server
- Only one build and deployment
- Failures can be devastating

Microservice Architecture:

- Deploy code on multiple servers per service
- Deploy more often
- Failures are partial
- Decoupled versions
- Can't reason about system from code alone

### Goals of DevOps

- Collaboration - between developers and operations
- Efficiency - bring changes from development to production
- Holistic - entire tool chain from dev to ops
- Configurations as code - documentation and versioning of dependencies, configs, and environments
- Automation - continuous delivery and monitoring
- Quick - small iterations, incremental and continuous releases

Quality assurance

