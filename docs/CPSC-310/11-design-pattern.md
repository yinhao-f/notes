# Design Pattern

Tried and true solution to a commonly encountered problem

Good when:

- Change is likely
- Coupling is painful

Not good when:

- No changes to requirement
- One concrete case
- Abstraction not worth the future benefit

## Observer

Watchers and watchee, lots of duplicate code (SRP), and watchee switching on type (DIP)

- One to many relationship between objects
- Relationships can be dynamically added
- Subject shouldn't be coupled to the objects observing them

## Composite

Wiki with a tree of articles, and each article may contain pages or more articles  
We want to traverse this tree of articles  
If we add a new type - posts, we need to modify traverse method in article (OCP)  

Solution: Use a traversable class

## Factory

Car factory, don't know what type of car is created


