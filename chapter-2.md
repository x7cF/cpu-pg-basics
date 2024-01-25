# CPU Program Counter
When your CPU is started, lets pretend there is a program in the ram by default. What happens is the CPU will read the data at address 0 and do something, then address 1, 2, 3, 4, etc... until it reaches the end, where it will start all over. There is a counter called the program counter which stores the address of the ram the cpu will do soemthing with.

**Clock**

Your CPU has a clock, each tick that happens it does something. For simplicity we will assume that an instruction is read and executed all in one tick of that clock. Realisticly it takes many ticks for each instruction based on what it does. 

With each tick, the program counter counts up. CPU boots up with program counter set to 0.

**Execution**

When I say do something, i mean the CPU executes it. Just like our custom string encoding, this is very similar. But rather than it corrosponding to letters, it corrosponds to commands. There is also one added complexity which is parameters to control the command.

Now youll notice a patteren once i show you this, its that lots of data and parameters are heavily controlled by how there used.

Now Ill make a simple instruction set architecture
```
Cmd | Action
0   | shut down cpu
1   | do nothing
```

Currently this architecture is very simply, it only has commands and NO parameters yet.
Lets bring back our ram.
```
Address | Value
0       | 1
1       | 1
2       | 1
3       | 1
4       | 0
5       | 0
6       | 0
7       | 0
8       | 0
```

This program does nothing for 4 ticks, aka clock cycles, or cycles, and then it reaches address 4 (5th instruction) and terminates the cpu. so the rest of the program never executes.
