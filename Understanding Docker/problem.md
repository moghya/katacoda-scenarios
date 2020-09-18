![](https://raw.githubusercontent.com/moghya/katacoda-scenarios/master/Understanding%20Docker/images/works-on-my-machine.jpg)

## Problems:
1. But it works on my machine.
2. That libray is missing.
3. The two applications need different version of shared library.
4. This one program eats up all the main memory and the other process can't allcoate memory at runtime that it requires.
5. Installation and manging this application is one hell of a task.

## Requirements for solving above problem:
1. How to get software to run reliably when moved from one computing environment to another.
2. Resolve conflicts between programs.
3. Limiting amount of resource usage by an application.
4. Better interface for managing lifecycle of processes.

## Solution:
Build something that provides mechanisms of doing all that is mentioned in requirements.
Would be better if it's flexible in a way that policies can be defined on top of provided mechanisms.
