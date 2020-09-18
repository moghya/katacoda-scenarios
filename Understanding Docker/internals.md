
## Docker components:

- Docker Daemon :
  - The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system which clients talk to.

- Docker Client:
  - The command line tool that allows the user to interact with the daemon. More generally, there can be other forms of clients too - such as Kitematic which provide a GUI to the users.

- Docker Hub:
  - A registry of Docker images. If required, one can host their own Docker registries and can use them for pulling images. (Private/OnPrem registries)

![](https://docs.docker.com/engine/images/architecture.svg)

## Containerization primitives

- Namespaces:  
  Docker uses a technology called namespaces to provide the isolated workspace called the container. When we run a container, Docker creates a set of namespaces for that container.
  Docker Engine uses namespaces such as the following on Linux:
  - The `pid` namespace: Process isolation (PID: Process ID).
  - The `net` namespace: Managing network interfaces (NET: Networking).
  - The `ipc` namespace: Managing access to IPC resources (IPC: InterProcess Communication).
  - The `mnt` namespace: Managing filesystem mount points (MNT: Mount).
  - The `uts` namespace: Isolating kernel and version identifiers. (UTS: Unix Timesharing System).
  - https://man7.org/linux/man-pages/man7/namespaces.7.html

- Control Groups:  
  Docker Engine on Linux relies on another technology called control groups (cgroups). A cgroup limits an application to a specific set of resources. 
  Control groups allow Docker Engine to share available hardware resources to containers and optionally enforce limits and constraints.
  For example, one can limit the memory available to a specific container.
  - https://man7.org/linux/man-pages/man7/cgroups.7.html

- Layered Filesystem:  
  Union file systems, or UnionFS, are file systems that operate by creating layers, making them very lightweight and fast.  
  Docker Engine uses UnionFS to provide the building blocks for containers. Docker Engine can use multiple UnionFS variants, including AUFS, btrfs, vfs, and DeviceMapper.

## Simple Docker Implementations:
- https://github.com/p8952/bocker/blob/master/bocker
- https://blog.lizzie.io/linux-containers-in-500-loc.html
- https://www.infoq.com/articles/build-a-container-golang/
