# Infrastructure Automation

To achieve faster application delivery, the right **infrastructure automation tools** must be used in DevOps environments. Unfortunately, there is no single tool that fits all your needs, such as server provisioning, configuration management, automated builds, code deployments, and monitoring. Many factors determine the use of automation tools in an infrastructure. Leta look into core infrastructure automation tools that can be used in a typical environment practicing DevOps philosophy.

There are many tools available for infrastructure automation. Choosing the right tool for infrastructure automation is decided by factors like platform architecture, skillsets, budget, security compliance, and the needs of your infrastructure. I have listed a few great tools below, which come under various categories like configuration management, orchestration, continuous integration, monitoring, etc. Tools for automating deployment can be categorised into the following.

1. Infrastructure Provisioning
1. Configuration Management
1. Continuous Integration/Deployment
1. Config/Secret Management
1. Logging and Monitoring

## Infrastructure provisioning

Infrastructure provisioning is the process of provisioning or creating infrastructure resources. It is part of infrastructure as code.

### Terraform

Open source cloud-agnostic infrastructure provisioning tool. It is created by Hashicorp and written in Go. It supports all public and private cloud infrastructure provisioning (Networks, servers, managed services, firewall, etc.).

Unlike other configuration management tools, terraform does a great job of maintaining the state of your infrastructure using a concept called state files. You can get started with Terraform in days as it is easy to understand. Terraform has its own domain-specific language (DSL) called HCL (Hashicorp configuration language). Also, you can write your own terraform plugin using Golang for custom functionalities.