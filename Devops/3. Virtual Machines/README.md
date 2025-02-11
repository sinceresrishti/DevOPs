# Day 3 - Virtual Machines

- Devops is all about improving the efficiency
- search about latency (Latency is the delay or lag that happens when data travels from one place to another. In simple terms, it’s the time it takes for something to happen after you give a command or send a request. So, in short, latency is the delay between an action and its result)

## An Analogy for Virtual Machines

- Consider you have bought 2 acres of land and built a house on it
- You realized that your house and all other resources combined, takes up only 1 acre
- So, you built a house in the remaining 1 acre and rent it to a family
- This is an example of efficient usage of available resources, which is the core concept of **Virtualization**

### Note

- Server is just a computer that hosts an application, so that the clients can access it through the internet

## Before Virtualization

- Consider your team of developers created an application
- An application requires isolated environment and you need to serve multiple customers
- So, you deploy the copies of the application into 10 servers and each server has 50 GB RAM
- Later you realized that the application needs only 4 GB RAM, and the resources of the server are being under-utilized

## Virtualization

- Virtualization is the process of creating virtual machines from a physical machine
- Virtual machine is actually a software based computer, that utilizes a logical partition of the resources from a physical machine
- Note that each Virtual Machine has it's own Operating System
- The logical partitioning, isolation of the environments, configuration of OS, etc is managed by a software called as **Hypervisor**
- Hypervisor is a software that can install virtual machines on your physical servers. (popular hypervisore: vmware, xen)

## After Virtualization

- Now instead of using multiple servers that results mostly in under utilization, we can use Virtualization to use lesser number of servers and use available resources efficiently
- This concept of Virtualization eventually lead to Cloud Computing, which is one of the game changer in the Software Industry

- Virtual machines are nothing but virtual environments which function as a virtual computer systems and these virtual computer systems has their own cpu, memory and hardware. so, vm1 is not depending on vm2 either for memory, cpu or hardware.
The only difference is instead of physical servers thay are logical servers. hypervisor is doing the entire process (creating vms)

## Virtualization in Cloud

- The Cloud Service Providers buy a large set of powerful computers across the globe 
- By virtualization, they provision the Virtual Machines with desired configuration in desired location, over the cloud
- This service is called Elastic Cloud Compute in AWS, Google Compute Engine in GCP Cloud

- if there are 100 physical servers (p1, p2.... p100) then it is used by 100 users only, but by using hypervisers it can now be used by millions of users.