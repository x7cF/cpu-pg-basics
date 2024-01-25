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
0       | 1     // DO NOTHING
1       | 1     // DO NOTHING
2       | 1     // DO NOTHING
3       | 1     // DO NOTHING
4       | 0     // Shut down CPU
5       | 0
6       | 0
7       | 0
8       | 0
```

This program does nothing for 4 ticks, aka clock cycles, or cycles, and then it reaches address 4 (5th instruction) and terminates the cpu. so the rest of the program never executes.

**Parameters**
Now lets add a new instruction called set_ram_10. set_ram_10 will take an address and set the value at it to 10.

But before we get to that, lets talk about parameters and order. To our architecture rules lets add the first thing which is parameter types. **NOTE**: You can only use each of these once. Each instruction is allowed to accept any one of the following parameters. For now its just IMM.
- IMM: Immediate data, the number of bits for this is equal to the architecture bits, currently we are using 4 bits for our architecture, its very simple

As for order, well theres only one parameter for now. So no order rules needed **yet**.

Lets add the instruction now. **NOTE**: I will format my parameters with the name of the parameter then equals what the use is. like how the instruction will utilize it.
```
Cmd | Action        | Paramater
0   | shut down cpu | 
1   | do nothing    |
2   | set_ram_10    | IMM=address
```

**Lets use our new instruction**
```
Address | Value
0       | 1     // DO NOTHING
1       | 1     // DO NOTHING
2       | 1     // DO NOTHING
3       | 1     // DO NOTHING
4       | 2     // Set ram to 10's instruction action
5       | 8     // Set ram to 10's address.
6       | 0
7       | 0
8       | 0
```

**Whats going on...**
You may notice that I just added the address for instruction at address 4 right after it. Why? Wont the CPU see the data at address 5 and try to execute it? No! This is because the CPU will realize that set_ram_10 uses the next address to store the parameter! Thats how parameters are given to actions. They are simply added right after it.
