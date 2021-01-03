# Program deployment onto different topologies
A program (a set of parallel processes communicating over channels) could be deployed on
a single transputer, in which case the channels were implemented in Software and parallelism
was concurrency via threads.
 
Or the program could be deployed onto a network of transputer chips with a given interconnect 
topology where each parallel software process would map onto one of the transputer CPUs (each CPU
running one or more of the software processes via threads) and some of the software channels were 
mapped onto the serial links between them.

This was determined at run-time by the OS with hardware support. The programmer didn't 
need to know or worry about the hardware topology when programming, but instead
focus on the parallelism of the application.