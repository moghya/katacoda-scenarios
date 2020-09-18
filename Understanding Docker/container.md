- `container /kənˈteɪnə/` : an object for holding or transporting something.

- A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.

- An application container is an isolated, resource-limited application execution context by host OS that has been unpacked and configured from an image.

- A  container is an environment that runs an application that is not dependent on the operating system. It isolates the app from the host by virtualizing it. This allows users to created multiple workloads on a single OS instance.

Looks like containers are completing all requirements that we had.

But how do containers are able to achieve it?
Containers can be formed using some meachnisms provided by Kernel/Operating System.
Let's keep rest of the details as an abstraction for a while and see it in action.

We'll deep dive post understanding how to use containers.

Let's clarify once how containers are different than virtual machines.

## What is Virtual Machine:

- A virtual machine (VM) is an operating system that shares the physical resources of one server. It is a guest on the host’s hardware, which is why it is also called a guest machine.


## Container vs Virtual Machine:

![Container](https://raw.githubusercontent.com/moghya/katacoda-scenarios/master/Understanding%20Docker/images/container-elements.png)

![Virtual Machine](https://raw.githubusercontent.com/moghya/katacoda-scenarios/master/Understanding%20Docker/images/virtual-machine-elements.png)
