# Pipelining

## Introduction

### Stages
- Fetch
- Decode
- Execute
- Memory
- Writeback

Pipeline adds registers between stages to transfer data

### Pipeline characteristics

- Pros:
    - More efficient hardware use b/c different parts of CPU can be used concurrently
    - Large batch of instructions completes more quickly
    - Increase throughput
- Cons:
    - Increase latency on individual instructions (due to pipeline registers)
    - Clock has to wait for slowest stage
    - Hazards
- Splitting into more stages usually introduces shorter clock cycles, thus higher throughput and more efficient in large batches of instructions
- Pipelining is most effective when each stages takes similar time
- Can:
    - Make multiple instructions in-flight at the same time
- Cannot:
    - Make processor fetch multiple instructions at the same time
    - be the only way to achieve hardware parallelism

### Latency

- Instruction latency
    - Sequential: simply add all stage execution times and register delay
    - Pipelined: (longest stage + register delay) * number of stages
- Retirement latency
    - Sequential: same as single instruction
    - Pipelined: slowest stage + register delay

### Throughput

GIPS (giga instructions per second) = 1000 / retirement latency (in picoseconds)

## Pipeline registers

Holds signals for each stage to use

Latching: captures the signals flowing in the pipeline registers and hold them till next clock cycle

### Instruction memory and data memory

Each can have error checking (for bad address, invalid instructions). Will make more sense in caching

### Fetch

`calcPC`: calculated PC

### Decode

`stat`: if instruction is valid or not  
`icode` `ifun` `rA` `rB` `valC` `valP`

### Execute

`stat` `icode` `ifun` `valC`  
New:  
`valA` `valB`: values from register  
`dstE` `dstM`: for register `E` and `M`

### Memory

`stat`(may change value after memory stage) `icode` `valA` `dstE` `dstM`  
New: `valE` `Cnd`(condition codes)

### Writeback

`stat` `icode` `valE` `dstE` `dstM`  
New: `valM`(value from memory)

### Signal naming conventions

- `S_signal` for signal from S stage
    - e.g. `D_stat`: right out of decode
- `s_signal` for signal at the end of s stage
    - e.g. `m_stat`: after the logic that checks memory address in memory phase

## Pipeline stalling

```
addq %rax, %rbx
subq %rbx, %rcx
```

In this example, the CPU needs to stall 3 cycles (without forwarding)

### Counting stalls

- Assume the first instruction enters at time T=1 (fetch)
- When does the second instruction need the data? say at T=3
- When will the first instruction write the data? say at T=5
- Number of stalls = $5+1-3=3$
    - (+1 because the writing stage needs to finish)

### Performance

CPI (cycles per instruction): how efficiently a **program** is running on a hardware

For y86, the CPI is 1 if not stalling; modern hardware has CPI < 1

Remember when counting cycles: the last instruction still needs to go through the pipeline, so we need to add 4 cycles. 

## Data hazards

### Data forwarding

In the `addq` `subq` example, the `addq` instruction has the value `valE` ready in execute stage, and the `subq` instruction needs the value in decode stage, so we can wire `e_valE` into a forwarding logic block, which will pass them to pipeline registers for execute. 

Things that don't work:
1. forwarding `e_valE` into the register file: the value will only be available for reading in the next cycle and cause stalling (cannot read and write to register at the same time)
2. forwarding `M_valE` into the forwarding logic: `M_valE` is only available in the next cycle
3. forwarding `e_valE` into the beginning of the execute stage: forwarding to the same instruction, will create loop

## Control hazards

- `jmp`: just forward `f_valC` into `next PC` logic and latch into `F_calcPC`, no hazards
- `call`: same, just use `valC`, no hazards
- `ret`: requires address from `W_valM`, **hazard**, 3 stalls
- `jxx` (conditional jump): need to choose between `valC` and PC increment, 2 stalls without prediction

### Branch predictions

- Backward jumps: loop, always taken
- Forward jumps: conditionals, never taken

Linux kernel can let you decide which branch is more likely to jump

#### How to implement?
- Forward `valC` and PC increment into new logic `predictor`
- `predictor` sends value into `F_predPC` (used to be `F_calcPC`)

#### What happens if mis-predicted?
- `jxx` gets to execute phase, realizes prediction was wrong
- Bad news: two wrong instructions in pipeline
- Good news: the bad instructions haven't reached memory or writeback stages, so nothing has been changed
- Solution: squash the instructions by replacing with `nop`
- Penalty, but no worse than stalling

#### CPI

- CPI when squashing: number of cycles in total (including squashed ones b/c already entered pipeline) / number of instructions after squashing
- Good branch prediction can reduce CPI