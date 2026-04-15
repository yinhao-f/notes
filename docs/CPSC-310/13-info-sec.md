# Information Security

## Terminology

- Assets: things the system try to protect
- Subjects: people or entities that interact with the system
- Policies: rules defining acceptable behavior
- Threats: potential actions that violate policies

#### Dimensions of security concerns:
- People: users, operators, developers, attackers
- Process: architecture, implementation, monitoring
- Technology: Mechanisms used to enforce security

## Security requirements

- Confidentiality
- Integrity
- Availability
- Accountability

### Security layers
- Physical security
- System security
- Network security
- Application security
- Human security

### Attack surface

How much system is exposed to attackers
- Entry points - APIs, input fields
- Exit points - error messages, responses
- Code handling those paths - validation, parsing, authentication

Security vs functionality is often a tradeoff

### Threat modelling

- Who might attack the system
- What are they trying to do
- Which vulnerability they use
- What is the risk

### STRIDE
A framework for ideating threat vectors:
- Spoofing - pretend to be someone else
- Tampering - modify data
- Repudiation - deny performing a task
- Information disclosure - access private information
- Denial of service - literally
- Elevation of privilege - gain unauthorized privileges

### Attack trees
Start with attacker's goal, trace the vulnerabilities of a system

### DREAD risk analysis
Evaluating an attack:
- Damage - how bad?
- Reproducibility - how easy to reproduce?
- Exploitability - how hard?
- Affected users - how many users impacted?
- Discoverability - how easy to discover?

## Mitigation strategies

### Defense in depth

### Least privilege

### Separation of duties

### Strong authentication

### Non-repudiation

## Validation

Validate mitigation strategies

- Code review
- Static analysis
- Dynamic analysis
- Penetration testing

### Static analysis

Linting - linters can check vulnerabilities

### Dynamic analysis

Fuzz testing - exercising software with unexpected inputs
