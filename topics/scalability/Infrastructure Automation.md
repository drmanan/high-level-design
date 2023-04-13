# Infrastructure Automation

- [Infrastructure Automation](#infrastructure-automation)
  - [Infrastructure provisioning](#infrastructure-provisioning)
    - [Terraform](#terraform)
      - [Useful Terraform Resources - all links non affiliated](#useful-terraform-resources---all-links-non-affiliated)
    - [Pulumi](#pulumi)
  - [Configuration Management](#configuration-management)
    - [Ansible](#ansible)
    - [Chef](#chef)
    - [Puppet](#puppet)
    - [Saltstack](#saltstack)
    - [Helm](#helm)

To achieve faster application delivery, the right **infrastructure automation tools** must be used in DevOps environments. Unfortunately, there is no single tool that fits all your needs, such as server provisioning, configuration management, automated builds, code deployments, and monitoring. Many factors determine the use of automation tools in an infrastructure. Leta look into core infrastructure automation tools that can be used in a typical environment practicing DevOps philosophy.

There are many tools available for infrastructure automation. Choosing the right tool for infrastructure automation is decided by factors like platform architecture, skillsets, budget, security compliance, and the needs of your infrastructure. I have listed a few great tools below, which come under various categories like configuration management, orchestration, continuous integration, monitoring, etc. Tools for automating deployment can be categorised into the following.

1. Infrastructure Provisioning
2. Configuration Management
3. Continuous Integration/Deployment
4. Config/Secret Management
5. Logging and Monitoring

---

## Infrastructure provisioning

Infrastructure provisioning is the process of provisioning or creating infrastructure resources. It is part of infrastructure as code.

### [Terraform][5]

Open source cloud-agnostic infrastructure provisioning tool. It is created by Hashicorp[7] and written in [Go][8]. It supports all public and private cloud infrastructure provisioning (Networks, servers, managed services, firewall, etc.).

Unlike other configuration management tools, terraform does a great job of maintaining the state of your infrastructure using a concept called state files. You can get started with Terraform in days as it is easy to understand. Terraform has its own domain-specific language (DSL) called HCL (Hashicorp configuration language). Also, you can write your own terraform plugin using Golang for custom functionalities.

An Example of Terraform configuration can be found [here](../Examples/Terraform.md).

#### Useful Terraform Resources - all links non affiliated

- [Terraform Tutorials][6] \[free\]
- [Terraform – Getting Started][1] \[paid\]
- [Terraform: From Beginner to Master with Examples in AWS][2] \[paid\]
- [Udemy Terraform Courses][3] \[both free (limited) and paid courses\]
- [The Terraform Book][4] by [James Turnbull][9] A sample section is available [here][10].

### [Pulumi][11]

[Pulumi][11] is an IAC tool that supports multiple programming languages like Python, [Go][8], Javascript, Java, etc.

Unlike other IaaC templating tools, Pulumi aims to provide better flexibility in terms of infrastructure code in your favorite programming language. This makes infra-code testing easy with existing testing frameworks that are native to a programming language.

Pulumi supports all the major cloud platforms like AWS, Google Cloud, and Azure. The best part is, it uses similar concepts like Terraform for state management.
If you are someone who wants to write pure code for your Infrastructure, you will give it a try for Pulumi.

Pulumi (unlike terraform) has great tutorial and examples on their website which can be found [here][12].

---

## Configuration Management

Configuration management is the process of configuring the provisioned infrastructure resources.

### [Ansible][13]

[Ansible][13] is agent-less configuration management as well as an orchestration tool. In Ansible, the configuration modules are called “Playbooks.”

Playbooks are written in YAML format, and it is relatively easy to write compared to other configuration management tools. Like other tools, Ansible can also be used for cloud provisioning. Ansible also supports dynamic inventory where it can fetch the server details dynamically through API calls. An example configuration is available [here with AWS](../Examples/Ansiable%20AWS%20Dynamic%20inventory.md) and [here with Google Cloud](../Examples/Ansible%20Dynamic%20Inventory%20%20Google%20Cloud.md)

But it is better to use tools like terraform for infrastructure provision and use Ansible for just configuration management. You can find all community playbooks from [Ansible Galaxy][14].

### Chef

Chef is a ruby-based configuration management tool. Chef has the concept of cookbooks where you code your infrastructure in DSL (domain-specific language) and with a little bit of programming.

Chef configures virtual machines according to the rules mentioned in the cookbooks.A chef agent would be running on all the servers which have to be configured. The agent will pull the cookbooks from the chef master server and run those configurations on the server to reach their desired state.

You can find all the community cookbooks from Chef Supermarket.

### Puppet

Puppet is also a ruby-based configuration management tool like Chef. The configuration code is written using puppet DSLs and wrapped in modules.
While chef cookbooks are more developer-centric while the puppet is developed by keeping system administrators in mind.

Puppet runs a puppet agent on all servers to be configured and it pulls the compiled module from the puppet server and installs the required software packages specified in the module. You can find all community Puppet Modules from Puppetforge

### Saltstack

Saltstack is a python based opens configuration management tool. Unlike chef and puppet, Saltstack supports the remote execution of commands.

Normally in chef and puppet, the code for configuration will be pulled from the server while, in Saltstack, the code can be pushed to many nodes simultaneously. The compilation of code and configuration is very fast in Saltstack.

> Note: The tool selection should be based entirely on project requirements and the team’s ability to learn and use the tool. For example, You can use Ansible to create infrastructure components and to configure VM instances. So if you have a small team and environment, terraform is not required to manage the infrastructure separately. Again it depends on how the existing team can learn and manage the toolsets.

### Helm

Helm is a configuration and package manager for Kubernetes. You can deploy any complex application on a Kubernetes cluster using Helm Charts.
It has great templating features that support templates for all kubernetes objects like deployments, pods, services, config maps, secrets, RBAC, PSP, etc.

You can use a single template to deploy multiple applications.
Also, look at Kustomize. It is a native configuration management utility for Kubernetes.

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
[11]: https://www.pulumi.com/
[12]: https://www.pulumi.com/docs/get-started/
[13]: https://www.ansible.com/
[14]: https://galaxy.ansible.com/