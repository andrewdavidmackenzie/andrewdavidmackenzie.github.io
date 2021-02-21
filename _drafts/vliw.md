---
layout: post
title: Flow Origins - VLIW
--- 
# It was 1995 - VLIW

I was a Software Engineer at HP's Barcelona Division working on embedded rendering software
for large format printers. Rendering lines, text and images was very compute (and memory)
intensive and a bottleneck for printing speeds.

Wanting to increase rendering performance we started working with Josh Fisher and
Paolo Faraboschi from HP Labs Boston.

Josh has started Multiflow computer after leaving his job as a Yale CS professor, 
 and was one of the pioneers (if not the pioneer) of "Very Long Instruction Word" (VLIW)
 computing.
 
VLIW expanded on RISC, by having many execution units (of different types) in the CPU
and a wide memory interface with high bandwidth, and multiple instructions for the different
execution units were fetched from memory in a "Very Long Word" and dispatched in parallel.

In RISC fashion, the CPU avoided complex instructions scheduling, dependency management, 
branch prediction etc. It focused on reducing hardware complexity, few transistors,
aiming for higher clock sppeds plus multiple instruction execution per clock cycle.


# The key to VLIW - Trace Scheduling

The key to high performance of VLIW lies in the optimizing compiler that lays out the 
many instructions for execution in parallel, avoiding dependencies between them.
 
 mportance of compiler for parallelism
Trace based instruction scheduling