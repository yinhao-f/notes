# Design Pattern 

Learning Outcomes:

- Identify which SOLID principles are violated, and which code smells are responsible for the violation.
- Recognize scenarios where patterns could be applied and how they would address the violations.
- Identify the pattern that is being used by looking for its main features.
- Apply patterns to existing code, or implement them from scratch.
- Be able to explain how a pattern improves (and degrades) an existing design and justify the benefits and tradeoffs of different pattern choices.
- For MVC: Be able to describe the control flow as updates arise from the model or view.


Tried and true solution to a commonly encountered problem

Good when:

- Change is likely
- Coupling is painful

Not good when:

- No changes to requirement
- One concrete case
- Abstraction not worth the future benefit

### Observer

Watchers and watchee, lots of duplicate code (SRP), and watchee switching on type (DIP)

- One to many relationship between objects
- Relationships can be dynamically added
- Subject shouldn't be coupled to the objects observing them

### Composite

Wiki with a tree of articles, and each article may contain pages or more articles  
We want to traverse this tree of articles  
If we add a new type - posts, we need to modify traverse method in article (OCP)  

Solution: Use a traversable class

### Factory

Car factory, don't know what type of car is created

### Facade

To provide a unified, higher-level, interface to a whole module making it easier to use. 

The interfaces are more limited than the whole subsystem. Most clients will be served while enabling other clients to use internal classes when needed. 

### Decorator

### Adapter

## GUI Design patterns

Evolution:  
MVC -> MVP -> MVVM -> Component Based (React)

### Model-View-Controller

### Model-View-Presenter

Make MVC's boundaries explicit

### Model-View-ViewModel

### Component-Based

