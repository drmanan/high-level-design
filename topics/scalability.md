# Scalability

> the capacity to be changed in size or scale.
>
> This section deals with theory only.

Scalability is the property of a system to handle a growing amount of work by adding resources to the system. It describes a system’s elasticity. While we often use it to refer to a system’s ability to grow, it is not exclusive to this definition. We can scale down, scale up, and scale out accordingly.

## Content

- [Scalability](#scalability)
  - [Content](#content)
  - [Usage of scalability](#usage-of-scalability)
  - [Types of scaling](#types-of-scaling)
    - [Vertical scaling](#vertical-scaling)
      - [Advantages of vertical scaling](#advantages-of-vertical-scaling)
      - [Disadvantages of vertical scaling](#disadvantages-of-vertical-scaling)
    - [Horizontal scaling](#horizontal-scaling)
      - [Advantages of horizontal scaling](#advantages-of-horizontal-scaling)
      - [Disadvantages of horizontal scaling](#disadvantages-of-horizontal-scaling)
  - [Comparitive differences](#comparitive-differences)
  - [The decision to scale out or scale up](#the-decision-to-scale-out-or-scale-up)
    - [Cost: The Grand Determinant](#cost-the-grand-determinant)
  - [Cloneing](#cloneing)
    - [Tangential Topic - infrastructure automation](#tangential-topic---infrastructure-automation)

// **TODO**

- Caching
- Load Balancers
- Database
  - Replication
  - Partitioning
- Asynchronism

Scalability is the measure of a system’s ability to increase or decrease in performance and cost in response to changes in application and system processing demands. Examples would include how well a hardware system performs when the number of users is increased, how well a database withstands growing numbers of queries, or how well an operating system performs on different classes of hardware. Enterprises that are growing rapidly should pay special attention to scalability when evaluating hardware and software.

scalability describes system’s ability to adapt to change and demand. Good scalability protects you from future downtime and ensures the quality of your service.

---

## Usage of scalability

- The ability of a computer application or product (hardware or software) to continue to function well when it (or its context) is changed in size or volume in order to meet a user need. Typically, the rescaling is to a larger size or volume. The rescaling can be of the product itself (for example, a line of computer systems of different sizes in terms of storage, RAM, and so forth) or in the scalable object's movement to a new context (for example, a new operating system).

> An example: John Young in his book Exploring IBM's New-Age Mainframes describes the RS/6000 SP operating system as one that delivers scalability ("the ability to retain performance levels when adding additional processors"). Another example: In printing, scalable fonts are fonts that can be resized smaller or larger using software without losing quality.

- It is the ability not only to function well in the rescaled situation, but to actually take full advantage of it. For example, an application program would be scalable if it could be moved from a smaller to a larger operating system and take full advantage of the larger operating system in terms of performance (user response time and so forth) and the larger number of users that could be handled.

It is usually easier to have scalability upward rather than downward since developers often must make full use of a system's resources (for example, the amount of disk storage available) when an application is initially coded. Scaling a product downward may mean trying to achieve the same results in a more constrained environment.

---

## Types of scaling

![Scalability types](./../res/img/banner.jpg)

Capacity planning is a challenge that every engineering team faces when it comes to ensuring the right resources are in place to handle expected (and unexpected) traffic demands. When demand for your application or website is increasing and you need to expand its accessibility, storage power, and availability levels, is it better to scale horizontally or vertically?

That decision depends on a number of factors. Is request volume steadily growing and/or is the current growth experiencing spikes that lead to service degradation. These types of considerations, coupled with an application’s unique make-up, need to be evaluated when determining the optimal scaling approach.

Scaling horizontally and scaling vertically are similar in that they both involve adding computing resources to your infrastructure. There are distinct differences between the two in terms of implementation and performance.

> Horizontal scaling means scaling by adding more machines to your pool of resources (also described as “scaling out”), whereas vertical scaling refers to scaling by adding more power (e.g. CPU, RAM) to an existing machine (also described as “scaling up”).

One of the fundamental differences between the two is that horizontal scaling requires breaking a sequential piece of logic into smaller pieces so that they can be executed in parallel across multiple machines. In many respects, vertical scaling is easier because the logic really doesn’t need to change. Rather, you’re just running the same code on higher-spec machines. However, there are many other factors to consider when determining the appropriate approach.

![Vertical vs Horizontal scaling](../res/img/horizontal-vs-vertical-scaling.webp)

### Vertical scaling

Vertical scaling (aka scaling up) describes adding additional resources to a system so that it meets demand. How is this different from horizontal scaling?

While horizontal scaling refers to adding additional nodes, vertical scaling describes adding more power to your current machines. For instance, if your server requires more processing power, vertical scaling would mean upgrading the CPUs. You can also vertically scale the memory, storage, or network speed.

Additionally, vertical scaling may also describe replacing a server entirely or moving a server’s workload to an upgraded one.

#### Advantages of vertical scaling

- Cost-effective - Upgrading a pre-existing server costs less than purchasing a new one. Additionally, you are less likely to add new backup and virtualization software when scaling vertically. Maintenance costs may potentially remain the same too.
- Less complex process communication - When a single node handles all the layers of your services, it will not have to synchronize and communicate with other machines to work. This may result in faster responses.
- Less complicated maintenance - Not only is maintenance cheaper but it is less complex because of the number of nodes you will need to manage.
- Less need for software changes - You are less likely to change how the software on a server works or how it is implemented.

#### Disadvantages of vertical scaling

- Higher possibility for downtime - Unless you have a backup server that can handle operations and requests, you will need some considerable downtime to upgrade your machine.
- Single point of failure - Having all your operations on a single server increases the risk of losing all your data if a hardware or software failure was to occur.
- Upgrade limitations - There is a limitation to how much you can upgrade a machine. Every machine has its threshold for RAM, storage, and processing power.

---

### Horizontal scaling

![Vertical scaling vs horizontal scaling](../res/img/horizontal-vs-vertical-scaling.jfif)

Horizontal scaling (aka scaling out) refers to adding additional nodes or machines to your infrastructure to cope with new demands. If you are hosting an application on a server and find that it no longer has the capacity or capabilities to handle traffic, adding a server may be your solution.

It is quite similar to delegating workload among several employees instead of one. However, the downside of this may be the added complexity of your operation. You must decide which machine does what and how your new machines work with your old machines.

You can consider this the opposite of vertical scaling.

#### Advantages of horizontal scaling

- Scaling is easier from a hardware perspective - All horizontal scaling requires you to do is add additional machines to your current pool. It eliminates the need to analyze which system specifications you need to upgrade.
- Fewer periods of downtime - Because you’re adding a machine, you don’t have to switch the old machine off while scaling. If done effectively, there may never be a need for downtime and clients are less likely to be impacted.
- Increased resilience and fault tolerance - Relying on a single node for all your data and operations puts you at a high risk of losing it all when it fails. Distributing it among several nodes saves you from losing it all.
- Increased performance - If you are using horizontal scaling to manage your network traffic, it allows for more endpoints for connections, considering that the load will be delegated among multiple machines.

#### Disadvantages of horizontal scaling

- Increased complexity of maintenance and operation - Multiple servers are harder to maintain than a single server is. Additionally, you will need to add software for load balancing and possibly virtualization. - -
- Backing up your machines may also become a little more complex. You will need to ensure that nodes synchronize and communicate effectively.
- Increased Initial costs - Adding new servers is far more expensive than upgrading old ones.kk[s]

---

## Comparitive differences

|                  | Horizontal Scaling (scaling out)                                                                                                                                                                                     | Vertical Scaling (scaling up)                                                                                                                                                                                  |
|----------------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Databases        | In a database world, horizontal scaling is usually based on the partitioning of data (each node only contains part of the data).                                                                                     | In vertical scaling, the data lives on a single node and scaling is done through multi-core, e.g. spreading the load between the CPU and RAM resources of the machine.                                         |
| Downtime         | In theory, adding more machines to the existing pool means you are not limited to the capacity of a single unit, making it possible to scale with less downtime.                                                     | Vertical scaling is limited to the capacity of one machine, scaling beyond that capacity can involve downtime and has an upper hard limit, i.e. the scale of the hardware on which you are currently running.  |
| Concurrency      | Also described as distributed programming, as it involves distributing jobs across machines over the network. Several patterns associated with this model: Master/Worker*, Tuple Spaces, Blackboard, MapReduce.      | Actor model: concurrent programming on multi-core machines is often performed via multi-threading and in-process message passing.                                                                              |
| Message passing  | In distributed computing, the lack of a shared address space makes data sharing more complex. It also makes the process of sharing, passing or updating data more costly since you have to pass copies of the data.  | In a multi-threaded scenario, you can assume the existence of a shared address space, so data sharing and message passing can be done by passing a reference.                                                  |
| Examples         | Cassandra, MongoDB, Google Cloud Spanner                                                                                                                                                                             | MySQL, Amazon RDS                                                                                                                                                                                              |

---

## The decision to scale out or scale up

In choosing between the two, there are various factors to consider. These include:

- **Performance** - Scaling out allows you to combine the power of multiple machines into a single virtual machine with the combined power of all of them. This means you’re not limited to the capacity of a single unit. First, however, it’s worth working out if you have enough resources within a single machine to meet your scalability needs.
- **Flexibility** - If your system is solely designed for scaling up, you are effectively locked into a minimum price set by the hardware you are using. If you want the flexibility to choose the optimal configuration setup at any time to optimize cost and performance, scaling out might be a better option.
- **Regularity of Upgrades** - Again, flexibility is important here. Building an application as a single large unit will make it more difficult to add or change pieces of code individually without bringing the entire system down. In order to deliver a more continuous upgrade process, it’s easier to decouple your application and horizontally scale.
- **Redundancy** - Horizontal scaling offers built-in redundancy in comparison to having only one system in vertical scaling, and thus a single point of failure.
- **Geographical Distribution** - When you need to spread out an application across geographical regions or data centers in order to reduce geo-latency, comply with regulatory requirements, or handle disaster recovery scenarios, you don’t have the option of putting your application in a single box. You have to distribute it.
- **Cost** - As more large multi-core machines enter the market at significantly lower price points, consider if there are instances in which your application (or portions of your application) can be usefully packaged in a single box and will meet your performance and scalability goals. This might lead to reduced costs.

### Cost: The Grand Determinant

It doesn’t always make sense to choose between horizontal and vertical scaling. Moving between the two models is often a better choice. For instance, in storage, we often want to switch between a single local disk to a distributed storage system.

Building flexibility into the system, where some layers of the application run on vertically scaled machines and other layers on horizontally scaled infrastructure remains a matter of designing for parallelization. To achieve this, (i) design it from the outset as a decoupled set of services, making the code easier to move, meaning you can add more resources when needed without breaking the ties between your code sets; (ii) partition your application and data model so the parallel units don’t share anything.

Despite your aspirations or organization’s needs, what may determine your decision, in the end, is cost. While horizontal scaling sounds great from a functional standpoint, you may not be able to afford it (right now). Nevertheless, it is still important to note that on-premise vertical and horizontal scaling may not be the only options available to you.

You can integrate both or migrate your organization’s infrastructure to a cloud service provider and allow them to handle scaling for you. The latter may be more financially and pragmatically feasible for you, especially in the long run. 

However, how do you actually prove this? If you migrate to a cloud solution, how do you determine your present and future cloud expenditure? 

A cloud cost management platform may be the best way to do this. You can determine and prove that migration and cloud auto-scaling will ultimately be more cost-effective than on-premise scaling.

## Cloneing

Public servers of a scalable web service are hidden behind a load balancer.  This load balancer evenly distributes load (requests from your users) onto your group/cluster of  application servers. That means that if, for example, user interacts with your service, they may be served at his first request by server 2, then with his second request by server 9 and then maybe again by server 2 on his third request.

User should always get the same results of their request back, independent what server they  “landed on”. That leads to the first golden rule for scalability: **every server must contain exactly the same codebase and does not store any user-related data, like sessions or profile pictures, on local disc or memory.**

Sessions need to be stored in a centralized data store which is accessible to all your application servers. It can be an external database or an external persistent cache, like Redis. An external persistent cache will have better performance than an external database. External means that the data store does not reside on the application servers. Instead, it is somewhere in or near the data center of your application servers.

But what about deployment? How can you make sure that a code change is sent to all your servers without one server still serving old code? This tricky problem is fortunately already solved by the great tools which automate server configurations like Capistrano, Terraform, Ansible, Chef Infra, Puppet, etc. It requires some learning but it is definitely worth the effort.

After “outsourcing” your sessions and serving the same codebase from all your servers, you can now create an image file from one of these servers (AWS calls this AMI - Amazon Machine Image.) Use this AMI as a “super-clone” that all your new instances are based upon. A similar thing can be achieved by using Docker and Docker Images. Whenever you start a new instance/clone, just do an initial deployment of your latest code and you are ready!

### Tangential Topic - infrastructure automation

Tools for automating deployment can be categorised into the following.

1. Infrastructure Provisioning
1. Configuration Management
1. Continuous Integration/Deployment
1. Config/Secret Management
1. Logging and Monitoring
