# Requirements

## Eliciting requirements

The process of gathering requirements from stakeholders

Two main kinds of requirements:
- Functional requirements: what the system must do, functionalities
- Non-functional requirements (aka quality attributes): properties a system must have, described using adjectives 

Requirement analysis: ensure requirements are measurable and testable

## Software Requirements Specification (SRS)

A formal document that describes what the system should do and the constraints under which it must operate

Purpose:
- Contract between stakeholders and developers
- Record-keeping, tracebility

Includes:
- Functional and non-functional requirements
- UI design and API
- Constraints and assumptions

Downsides:
- Can be too rigid for iterative (agile)
- Hard to maintain as software evolve
- Lack context of real use case
- Difficult for non-technical to understand

Solutions:
- Use cases: written description of an actor interacting with the system
- User stories: short, simple descriptions of a feature told from the perspective of the end user

## Validating requirements

Making sure requirements are correct, complete, consistent and feasible before development

Purpose:
- Prevents rework
- Make sure it's what stakeholders want

## Ethics in software engineering

- Transparency
- Respect for stakeholders (inclusiveness)
- Privacy and confidentiality
- Avoid bias
- Informed consent

ACM/IEEE Code of Ethics

## User stories

In large projects, user stories become:
- Themes
    - High-level, strategic
- Epics
    - Grouped together user stories
- User stories
- Task

Commitment artifacts:
- Role goal benefit (aka user story)
- Definitions of done (aka acceptance criteria, solution to role goal benefit)

Engineering details:
- Engineering tasks

Role goal benefit (RGB)
- Role: as a user,
- Goal: I want to search for contacts,
- Benefit: so I can message them

If it contains technical terms, likely not RGB

## Definition of Done (DoD)

What stakeholders and developers both agree on

- Unambiguous
- Testable
- Yes or No

Common formats:
- Checklist
- Given/When/Then

## Engineering tasks

What developers break down user stories into

Story points
- Corresponds to how much time is needed to develop
- Can be used as estimate of development progress

## Accessing user stories using INVEST
- Independent: stories should be independent of each other
- Negotiable: user fully understands the feature, able to add to the requirements later on
- Valuable: has value to the customer
- Estimatable: written precisely enough so developer can estimate how long it will take
- Small: should be 2-3 days to work for the team (sometimes single day)
- Testable: how developer knows it's done (DoD); what to test, how to test, and what it means when tests pass