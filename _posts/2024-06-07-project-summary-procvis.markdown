---
title: "Project Summary: ProcVis"
category: project
tag: project
layout: post
---

ProcVis (Proccessor Visualisor) was a project I undertook for my final year project whil at university.

The project was intended to help teach some parts computer architecture.
I intended to do this by creating a way to visualise how the components of a processor interact, and the various stages involved in executing instructions.

<!--more-->

## Design

<figure>
    <img src="/assets/posts/2024-06-07-project-summary-procvis/proc-vis.png" alt="Image of the user interface for ProcVis"/>
    <figcaption>Fig.1 The UI for ProcVis</figcaption>
</figure>

The processor (shown in Fig.1) is a simple 8 bit Von-Neumann design, consisting of: 
* 2 general use registers (A & B),
* 2 additional registers for serving the ALU,
* A single instruction register,
* A single program counter register,
* A single address register,
* An Arithmetic & Logic Unit (ALU),
* A Control Unit,
* 256 bytes of programmable memory (RAM),
* A "clock" (serves as the user's control for progressing the processor).

There are also various data busses on the processor:
* In blue we have the data busses
  * The main data bus connects the RAM to the various registers. This bus has 8 lanes.
  * There are two single land busses linking the ALU to the control unit. These hold the zero and sign flags for conditional jumps.
  * Finally there are busses connection the math regsters to the ALU, the instruction register to the control unit, and the address register to the ram.
  * Data busses connection registers directly to another component are always enabled.
* In red there are the command busses. These carry signals for
  * Set (store the current value on the main bus), 
  * Enable (Write the current value to the main bus), 
  * and Increment (increase the stored value by 1).
  * There are also three that carry an opcode to the ALU to tell it what instruction to execute.

## Instruction Set
