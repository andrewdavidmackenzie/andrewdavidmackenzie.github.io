---
layout: post
title: Flow Origins - VLIW
--- 
# It was 1995 - VLIW

I was a Software Engineer at HP's Barcelona Division working on embedded rendering software
for large format printers. Rendering lines, text and images was very compute (and memory)
intensive (especially with those massive page sizes) and a bottleneck for printing speeds.

Wanting to increase rendering performance we started working with Josh Fisher and
Paolo Faraboschi from HP Labs Boston.

Josh had started Multiflow computer after leaving his job as a Yale CS professor, and was one of the pioneers
(if not the pioneer) of "Very Long Instruction Word" (VLIW) computing.
 
VLIW expanded on RISC, by having many execution units (of different types) in the CPU and a wide memory interface. 
Multiple instructions for the different execution units were fetched from memory in a single "Very Long Word" and 
were then dispatched to the many execution units in parallel.

In RISC fashion, the CPU avoided doing complex instructions scheduling, dependency management, branch prediction in
hardware. It focused on reducing hardware complexity, few transistors and aimed for higher clock speeds plus 
multiple instruction execution per clock cycle.

That moved a lot of the heavy lifting to software - the compiler laying our those instructions in memory in those
Very Long Instruction Words.

# The key to VLIW - Trace Scheduling
The key to high performance of VLIW lies in the optimizing compiler that lays out the 
many instructions for execution in parallel.

In order for a set of instructions to truly execute in parallel on multiple execution units it is necessary
to avoid dependencies between them, which would cause errors or pipeline "stalls" at runtime - defeating the purpose.
 
# Trace based instruction scheduling

# Summary of things that stuck with me
Or, "How does this apply to `flow`?"

key to parallelism is understanding data dependencies between pieces of execution.
something can only execute when it has the data it needs, and then it produces data for another piece of execution
that depends on it.

This can all be analyzed in the input algorithm and laid out in a graph.

Think of blocks of occam code, communicating by channels, or individual instructions (or blocks of instructions)
"communicating" via memory (heap or stack) or registers.