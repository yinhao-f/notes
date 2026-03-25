# Refactoring

Definition: predictable and meaning (semantics and behavior) preserving code transformations

## How to refactor?

- Pass tests
- Look for code smell
- Choose how to refactor
- Test after refactoring
- Repeat until no more smell

Refactoring should be opportunistical and more frequent

## Code smells

### Magic numbers

Use constants

### Long methods

- Try to extract into new methods

### Explanatory comments

Comment technology is fine

- Comments not updated with code - documentation drift
- Copy and paste code, but forget about comments
- People don't like to read comments

Solution: elements with better naming

### Long parameter list

- Too many parameters is annoying

Solution: make a separate object (a type) for the parameters

### Switch on type

Solution: polymorphism

### Duplicate code

Solution: pull up to a function in superclass

Tricks about common and unique code:
- Use an abstract method in superclass
- Let the subclasses override the method
- Combine logic in superclass, not in subclasses

### Feature envy

When you need to access many fields from another class, this method should probably live in that other class

### Divergent changes (experiential)

- Have to make a change in more than one location  
- One class is actually two
- **One class that suffers many kinds of changes**

### Shotgun surgery (experiential)

- Changes will likely result in development collisions  
- When you make a change, you need to make lots of small changes, which are hard to find and easy to miss
- **One change that alters many classes**

## Technical dept

Extra cost to change the system later because of earlier shortcuts

- Code smells lead to later interest payments of TD
- The dept kicks in when trying to add features or to fix bugs

Solution:
- Track TD explicitly
- Prioritize refactoring
- Refactor according to smell instead of everywhere
- Talk to owners
- Automate testing
