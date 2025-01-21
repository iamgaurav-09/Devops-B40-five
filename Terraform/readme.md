# What is IAC


**Infrastructure as code** (IaC) is the ability to provision and support your computing infrastructure using code instead of manual processes and settings. Any application environment requires many infrastructure components like operating systems, database connections, and storage. Developers have to regularly set up, update, and maintain the infrastructure to develop, test, and deploy applications. 

![image](https://github.com/user-attachments/assets/86e3bdae-9bd4-4032-86aa-fac82276e509)


# What is Terraform


**Terraform** is an open-source IaC solution created by HashiCorp and primarily employed by DevOps teams. According to the State of IaC 2023 report, it’s the most widely-used solution to manage cloud resources. But before diving into the secrets of Terraform’s popularity, let's learn its specific terms.

**Resources** in Terraform are infrastructure objects—for example, networks, virtual machines (compute instances), or DNS (domain name system) records.

**Providers** are plugins that enable interaction with cloud providers, SaaS providers, and other APIs. Without providers, Terraform can't manage any kind of infrastructure.

**Modules** are containers for multiple resources used together and are the main way to package and reuse resource configurations.

**State** refers to a critical component that stores information about managed infrastructure and configurations. It keeps bindings between objects in a remote system and resource instances declared in configuration.

**Data sources** allow Terraform to use information defined outside of Terraform, or by another separate Terraform configuration, or modified by functions. Each provider may offer data sources alongside its set of resource types.

![image](https://github.com/user-attachments/assets/db567336-a690-4aac-8f9e-f4479797b6fd)


# Terraform vs Cloudformation


**Multi-Cloud Support**

Terraform is an open-source tool designed for provisioning and managing infrastructure across different cloud providers, such as AWS, Azure, Google Cloud, and on-premise environments. It provides a consistent syntax and workflow when managing resources across different clouds.

CloudFormation is an AWS native service specifically created to provision and manage resources on AWS. Embedded deeply within their ecosystem, this standardized way to describe and deploy infrastructure makes CloudFormation invaluable in meeting resource demand across an AWS environment.

**Language and Syntax**

Terraform utilizes HashiCorp Configuration Language (HCL), an easy and concise domain-specific language specifically tailored for describing infrastructure as code. HCL lets users easily define resources, variables, and other configuration elements with concise syntax.

AWS CloudFormation supports both JSON and YAML formats to describe infrastructure. JSON can provide machine-friendly data representation, while YAML facilitates natural, structured representations of resources with their relationships.

**Declarative vs. Templating**

Terraform is a declarative tool, while CloudFormation is templating. Terraform's configuration files describe your desired state, while CloudFormation templates outline how it should approach reaching this state.

**Ecosystem Integrations**

Terraform boasts an expansive ecosystem of providers and modules developed by its community that allow it to integrate with various tools, cloud platforms, and services. CloudFormation, on the other hand, excels at AWS-specific integrations.

**State Management**

Terraform relies on a state file that records the actual state of the deployed infrastructure. This state file is essential for tracking changes, detecting drift, and planning updates to the infrastructure. The state can be stored locally or in remote backends like Amazon S3 or Consul.

AWS CloudFormation manages the state of stacks internally without exposing it directly to users. Users interact with stacks through CloudFormation's API, and the tool internally manages the state of resources associated with each stack.

**Resource Lifecycle Management**

Terraform provides a "plan-apply" model. When you make changes to the infrastructure configuration, you generate an execution plan first ("terraform plan"), which shows the proposed changes. After reviewing the plan, you apply the changes ("terraform apply") to create, modify, or delete resources.

AWS CloudFormation utilizes a "create-update-delete" model. You define the desired state of your infrastructure using CloudFormation templates. During updates, CloudFormation determines what changes are needed to bring the stack's actual state in line with the desired state and applies those changes.

**Ecosystem and Extensibility**

With plugins, you can extend Terraform's functionality to support new providers, data sources, and resources. You can also write your own plugins to customize Terraform to your specific needs. Plus, there is already a ton of community-contributed plugins available that you can easily integrate into your workflows.

AWS CloudFormation integrates tightly with AWS services, enabling seamless management of AWS resources. However, its scope is limited to AWS services, and there is no direct support for managing resources from other cloud providers.

**Drift Detection**

Terraform provides built-in drift detection, allowing you to identify discrepancies between the infrastructure's current state and the state described in your configuration. This is useful for identifying manual changes or unexpected modifications.

AWS CloudFormation's drift detection is specific to CloudFormation-managed stacks. It directly compares the current state with the template-defined state. It helps ensure that the resources deployed through CloudFormation remain in the expected state.

**Interpolation and Functions**

Terraform provides an extensive set of interpolation functions that allow you to dynamically generate values based on other values or inputs, making your configurations more flexible and easier to manage.

AWS CloudFormation offers intrinsic functions that allow you to perform tasks like referencing other resource attributes, performing basic calculations, and conditional logic within your templates. While not as comprehensive as Terraform's interpolation functions, they still offer essential dynamic capabilities.

**Learning Curve**

While Terraform and AWS CloudFormation have relatively gentle learning curves, the choice may depend on the team's existing knowledge and expertise. Developers familiar with AWS services may find AWS CloudFormation more intuitive, while those with experience in multiple cloud environments may prefer Terraform.

**Community support**

Terraform boasts a larger and more active community than CloudFormation, so there are more resources to assist users when learning and using Terraform.


# Terraform vs Ansible

Ansible and Terraform are two popular tools in the infrastructure-as-code (IaC) domain, but they serve slightly different purposes. Here’s a detailed comparison:

---

### **1. Purpose**
| **Feature**                | **Ansible**                                       | **Terraform**                                             |
|----------------------------|---------------------------------------------------|-----------------------------------------------------------|
| **Primary Use**            | Configuration Management and Orchestration        | Infrastructure Provisioning and Management                |
| **Functionality**          | Focuses on configuring existing infrastructure    | Focuses on creating and managing infrastructure resources |

---

### **2. Declarative vs. Procedural**
| **Aspect**                | **Ansible**                                   | **Terraform**                                                |
|---------------------------|-----------------------------------------------|--------------------------------------------------------------|
| **Approach**              | Mix of declarative and procedural             | Purely declarative                                           |
| **Implementation**        | Tasks/plays execute in a sequence             | Describes desired end state, Terraform figures out execution |

---

### **3. Language**
| **Aspect**                | **Ansible**                                   | **Terraform**                                |
|---------------------------|-----------------------------------------------|----------------------------------------------|
| **Language**              | YAML for playbooks                            | HCL (HashiCorp Configuration Language)       |

---

### **4. Agent Requirement**
| **Aspect**                | **Ansible**                                    | **Terraform**                                |
|---------------------------|------------------------------------------------|----------------------------------------------|
| **Agentless**             | Yes (SSH or WinRM-based)                       | Yes, but uses a central state file           |

---

### **5. State Management**
| **Aspect**                | **Ansible**                                   | **Terraform**                                      |
|---------------------------|-----------------------------------------------|----------------------------------------------------|
| **State Management**      | No persistent state tracking                  | Maintains state in a `.tfstate` file               |
| **Impact of Changes**     | Executes tasks without a state reference      | Tracks state to plan and apply incremental changes |

---

### **6. Use Cases**
| **Aspect**                | **Ansible**                                   | **Terraform**                                |
|---------------------------|-----------------------------------------------|----------------------------------------------|
| **Best Suited For**       | Application deployment and configuration      | Infrastructure provisioning and scaling      |
| **Examples**              | - Install software                            | - Create VMs, networks, and load balancers   |
|                           | - Configure servers                           | - Manage cloud resources                     |

---

### **7. Integration with Cloud Providers**
| **Aspect**                | **Ansible**                                    | **Terraform**                                |
|---------------------------|------------------------------------------------|----------------------------------------------|
| **Cloud Support**         | Supports major cloud providers via modules     | Strong cloud support with provider plugins   |

---

### **8. Execution Model**
| **Aspect**                | **Ansible**                                   | **Terraform**                                |
|---------------------------|-----------------------------------------------|----------------------------------------------|
| **Push vs. Pull**         | Push-based model                              | Uses a client-based execution with plans     |


# Advantages of Terraform

**Advantages**

**Infrastructure as Code:** 

Terraform enables the use of Infrastructure as Code, where infrastructure is treated as software and can be version controlled, tested, and deployed using code. 

**Multi-Cloud Support:** 

Terraform supports multiple cloud platforms, making it easier to deploy and manage infrastructure across different environments. 

**Consistency and Standardization:** 

Terraform ensures consistency and standardization of infrastructure across different environments, reducing the risk of errors and increasing the efficiency of deployment. 

**Flexibility:** 

Terraform provides flexibility in terms of configuration and deployment, allowing for quick changes and modifications to the infrastructure. 


1.Terraform internally uses the DAG(direct acyclic graph) technique to get the best results. 

2.Terraform supports a variety of cloud options, and switching providers is a breeze. 

3.Because the whole infrastructure is managed as code, incremental resource changes are not a problem. 

4.Supports scripts that span many regions. For instance, we can search for an ami in us-east-1 and use that information to build an ec2 instance in us-east-2. 

5.Effective networking assistance. It might take months to build an on-premise data center, but using Terraform, it can be done in a matter of hours. 

6.Integrates easily with the build and deployment processes. 

7.Modular architecture. 

8.State upkeep. Terraform will reconstruct any objects produced by it if another process removes them. 

9.Allows for the import of existing resources to convert them to a Terraform state.


**Disadvantages**

1.Currently under development. Each month, we release a beta version. 

2.The concerns are more connected to Terraform’s (AWS) provider teams. For example, Terraform AWS’s quick sight does not yet support all features. 

3.Technology with a narrow application. To write loops or if blocks, intuition is required. Nonetheless, several hacks are accessible online. 

4.Specific configurations, such as the terraform backend, are not accessible through var files. Therefore, either give the information in place or construct a backend-
config block during Terraform’s initialization. 

5.There is no error handling. This implies that we cannot utilize try-catch in the manner we do in other languages. 

6.There is no way to roll back. As a result, we must delete everything and re-run if necessary. 

7.A few things are prohibited from import. 

8.Terraform does not support script generation from the state. 

9.Terraform acknowledges that specific versions may include bugs. 


# Terraform providers

Terraform relies on plugins called providers to interact with cloud providers, SaaS providers, and other APIs.
Terraform configurations must declare which providers they require so that Terraform can install and use them. Additionally, some providers require configuration (like endpoint URLs or cloud regions) before they can be used.

**What Providers Do**

Each provider adds a set of resource types and/or data sources that Terraform can manage.
Every resource type is implemented by a provider; without providers, Terraform can't manage any kind of infrastructure.
Most providers configure a specific infrastructure platform (either cloud or self-hosted). Providers can also offer local utilities for tasks like generating random numbers for unique resource names.

**Where Providers Come From**

Providers are distributed separately from Terraform itself, and each provider has its own release cadence and version numbers.
The Terraform Registry is the main directory of publicly available Terraform providers, and hosts providers for most major infrastructure platforms.

**Commonly Used Terraform Providers List**

**AWS**

Amazon Web Services (AWS) is a comprehensive and widely used cloud computing platform and service provided by Amazon.com. AWS offers a vast array of cloud-based computing resources, services, and tools that enable individuals, businesses, and organizations to build, deploy, and manage a wide range of applications, websites, and services in a highly scalable and cost-effective manner.

Each AWS service or resource type corresponds to a specific resource provider in Terraform. These providers define Terraform resources and data sources that map to the corresponding AWS resources. The AWS provider for Terraform acts as the intermediary between your Terraform configurations and the AWS API.

<img width="584" alt="image" src="https://github.com/user-attachments/assets/2479aa3f-e724-470b-8cbb-fd03f175fd20" />

**AZURE**

A cloud computing platform and service provided by Microsoft. It offers a wide range of cloud-based services and solutions, including infrastructure as a service (IaaS), platform as a service (PaaS), and software as a service (SaaS) that can be used for various computing, storage, analytics, databases, networking, machine learning, and application deployment needs.

Azure Resource Providers are components that Terraform uses to interact with Azure resources. Azure Resource Providers in Terraform correspond to different Azure services or resource types that you can manage and provision using Terraform configurations.

Each Azure service or resource type has its own resource provider in Terraform, and these providers are responsible for defining the Terraform resources and data sources that map to the corresponding Azure resources. The Azure provider for Terraform acts as the bridge between your Terraform configurations and the Azure API

<img width="584" alt="image" src="https://github.com/user-attachments/assets/20ff8e0c-8ff5-4b00-bf7a-86288dedd849" />

**Google Cloud**

Google Cloud, often referred to as Google Cloud Platform (GCP), is a comprehensive suite of cloud computing services provided by Google. It offers a wide range of cloud-based solutions for computing, storage, databases, machine learning, data analytics, and more.

The Google Cloud Terraform Provider is used to configure your Google Cloud Platform infrastructure. It is collaboratively maintained by the Google Terraform team at Google and the Terraform team at HashiCorp.

<img width="584" alt="image" src="https://github.com/user-attachments/assets/2614078d-4eb3-4dc8-b299-da7f8adceca9" />


![image](https://github.com/user-attachments/assets/fda973da-a60d-4831-a473-d890fc0db479)

