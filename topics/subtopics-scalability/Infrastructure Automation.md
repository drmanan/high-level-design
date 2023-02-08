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

### [Terraform][5]

Open source cloud-agnostic infrastructure provisioning tool. It is created by Hashicorp[7] and written in Go[8]. It supports all public and private cloud infrastructure provisioning (Networks, servers, managed services, firewall, etc.).

Unlike other configuration management tools, terraform does a great job of maintaining the state of your infrastructure using a concept called state files. You can get started with Terraform in days as it is easy to understand. Terraform has its own domain-specific language (DSL) called HCL (Hashicorp configuration language). Also, you can write your own terraform plugin using Golang for custom functionalities.

An Example of Terraform configuration can be found [here](../Examples/Terraform.md).

#### Useful Terraform Resources - all links non affiliated

- [Terraform Tutorials][6] \[free\]
- [Terraform – Getting Started][1] \[paid\]
- [Terraform: From Beginner to Master with Examples in AWS][2] \[paid\]
- [Udemy Terraform Courses][3] \[both free (limited) and paid courses\]
- [The Terraform Book][4] by [James Turnbull][9] A sample section is available [here][10].

[1]: https://www.pluralsight.com/courses/terraform-getting-started
[2]: https://www.educative.io/courses/terraform-beginner-master-aws
[3]: https://www.udemy.com/topic/terraform
[4]: https://www.amazon.com/Terraform-Book-James-Turnbull-ebook/dp/B01MZYE7OY/
[5]: https://www.hashicorp.com/products/terraform
[6]: https://developer.hashicorp.com/terraform/tutorials
[7]: https://www.hashicorp.com
[8]: https://go.dev/
[9]: https://jamesturnbull.net/
[10]: https://terraformbook.com/TheTerraformBook_sample.pdf