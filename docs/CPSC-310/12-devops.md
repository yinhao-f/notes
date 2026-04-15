# DevOps

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

### Quality assurance

### Code release

Code must be released to become a product

#### Continuous release

- Traditional: fixed release date, heavy QA before release
- Frequent release: frequent and incremental updates, automated updates
- Hosted software: different versions for different customers

### Automation

- Mitigates release problems
- Requires heavy tooling
    - Infrastructure as code
    - CI/CD
    - Test automation
    - Containerization
    - Orchestration
    - Software deployment
    - Monitoring

#### Infrastructure as code (IaC)

Scripts to change system configs

#### Containerization

Example: Docker  
- Lightweight and fast virtualization
- Sharable virtual images

#### Monitoring and telemetry

- Monitor server hardware
- Capture telemetry data from clients

### Testing in Production

Some bugs can't be spotted unless in production

#### Feature flags

- Boolean variables to turn on/off features
- Features are documented, tracked, localized and independent

#### Canary releases

- Gradual rollout
- Router decides who gets new release
- Monitor issues
- Automatic rollback if needed

#### Chaos experiments

- Validate reliability
- Tests behavior under failure
- Tells when things break

#### Running experiments (A/B testing)

- Implement alternative versions
    - Use feature flags
    - Separate deployments
- Map users
- Monitor outcomes

### Microservices

Code is split up and deployed on multiple servers. Servers communicate via network requests. 

- Loosely coupled
- SRP for each service
- High cohesion