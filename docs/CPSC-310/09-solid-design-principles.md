# Design Principles: SOLID

## SOLID

- Single Responsibility Principle
- Open/Closed Principle
- Liskov Substitution Principle
- Interface Segregation Principle
- Dependency Inversion Principle

## Single Responsibility Principle

A class should have only one responsibility  
This class should only be affected by one spec change  

- Signs of SRP violation: ripple effects  
- SRP tries to improve cohesion

## Open Close Principle

**Closed** for internal change, **open** for extension

- Subclasses should override methods of superclass
- Signs of violation: adapt behaviors using flags or `instanceof`

Benefits:

- Adapt to future changes
- Stable API
- Low coupling
- Explicit on "where to change"

Drawbacks:

- Unnecessary abstractions "just in case"
- Code is hard to understand
- Extension never happens

## Liskov Substitution Principle

If we substitute a subclass into the superclass, we shouldn't break any
behavior/properties. 

Subtype should have the properties of the supertype

Example

- Penguins can't be subtype of birds (birds can fly, but not penguins)
- Square can't be the subtype of rectangle (width and height can't be changed separately)

## Interface Segregation Principle

Many client-specific interfaces are better than one general-purpose interface. 

- Clients should not have to depend on unrelated methods
- Shouldn't be forced to implement methods that don't fit in
- Pathway to SRP and LSP
- Solution: role-based interfaces

## Dependency Inversion Principle

Depend on abstractions, not implementations

Depend on - declaring an entity

- Public methods call the private methods within the class
- Private methods then depend on interfaces

## Testability

- Observability: how much the response of CUT (code under test) can be verified
- Controllability: how much the CUT can be made to perform actions of interest
- Automatability: ability to execute tests programmatically
- Isolateability: how much the CUT can be verified on its own

### Observability - SRP

- What is needed to identify pass/fail?
- How expensive to do this?
- Can we extract result from CUT?
- Do we know enough to identify pass/fail?

Black box testing

### Controllability - ISP + DIP

How much public entry points are available to work with to control the system for testing?

### Automatability - DIP

Testing can sit between UI layer and controllers

### Isolateability - SRP + ISP + DIP

How much can we isolate the crux of the problem?

### Mocking

Used to mock a behavior when part of the code hasn't been implemented or is too slow

Can help with finding root cause of the bug

