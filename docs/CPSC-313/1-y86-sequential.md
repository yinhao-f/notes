# Y86 Sequential

## Calling coventions
- Parameter passing
- Caller-save registers (e.g. `%rcx`)
    - Functions may do whatever they want to these registers
    - If caller wants to keep the value, it needs to save it to memory before calling
- Callee-save regsiters (e.g. `%rbp`)
    - Functions can rely on these registers not changing
    - If function uses `%rbp`, it will need to save the value and restore it before returning
