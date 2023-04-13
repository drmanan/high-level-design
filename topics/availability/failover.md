# Failover, mitigation and planning

**Failover** is a technique used to ensure high **[availability][1]** of a system. It is the process of automatically switching to a standby system in case the primary system fails or becomes unavailable. Failover is a key component of a disaster recovery plan, and it helps ensure that systems remain available during an outage and minimize downtime.

There are different types of failover, including:

1. **Active-passive** ***failover***: In this type, there is a primary system that handles all requests, while a secondary system is idle and waiting for the primary system to fail. When the primary system fails, the secondary system takes over and becomes active.

**Active-active** ***failover***: In this type, there are multiple active systems, each handling a portion of the traffic. If one system fails, the traffic is automatically redirected to the remaining active systems.

To implement failover, you need to have redundant systems and a mechanism for detecting the failure of the primary system. You also need to have a way of redirecting traffic to the standby system, and this is typically done using load balancers or DNS failover.

There are different strategies for mitigating failover, including:

1. **Testing**: Regularly testing the failover system to ensure it works as expected.

1. **Monitoring**: Monitoring the system to detect potential issues before they become problems.

3. **Redundancy**: Ensuring that all critical components of the system are redundant, so that if one component fails, another can take over seamlessly.

4. **Automation**: Automating the failover process as much as possible to minimize downtime and human error.

5. **Documentation**: Creating detailed documentation of the failover process, so that everyone involved knows exactly what to do in case of a failure.

<!-- Links -->

[1]:../availability.md