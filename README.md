# 📘 Personal Study Guide - AWS Certified Cloud Practitioner (CCP) Exam 

## 1. What is Cloud Computing?

**Definition:**
Cloud computing is the on-demand delivery of IT resources (compute power, storage, databases, networking, software, etc.) via the internet with a pay-as-you-go pricing model. It eliminates the need for organizations to own and maintain physical data centers and servers, offering scalability, flexibility, and cost-efficiency.

### Characteristics of Cloud Computing (NIST Definition):
1. **On-Demand Self-Service:**
   - Users can provision computing resources like servers, storage, and databases as needed, automatically without requiring human intervention from the provider.
   - **When to Use:** For environments where agility and speed are crucial.
   - **When Not to Use:** In legacy environments requiring manual provisioning or strict governance.
   - **Analogy:** Like using water or electricity at home—you turn the tap or flip the switch without needing to call the utility company.

2. **Broad Network Access:**
   - Resources are accessible over the internet using standard devices (e.g., laptops, smartphones) and protocols (e.g., HTTP, HTTPS).
   - **When to Use:** For global accessibility and remote teams.
   - **When Not to Use:** For highly sensitive workloads that must remain isolated.
   - **Example:** AWS services can be accessed via the AWS Management Console, CLI, or SDKs.

3. **Resource Pooling:**
   - The provider's resources (compute, storage, memory) are pooled together to serve multiple customers using multi-tenant models, with different physical and virtual resources dynamically assigned and reassigned.
   - **When to Use:** For workloads that can benefit from shared infrastructure cost savings.
   - **When Not to Use:** When compliance requires dedicated hardware.
   - **Analogy:** Like an apartment building where different tenants share common utilities.

4. **Rapid Elasticity:**
   - Capabilities can scale rapidly outward and inward based on demand.
   - **When to Use:** For unpredictable workloads or seasonal spikes.
   - **When Not to Use:** For static workloads with predictable resource needs.
   - **Example:** AWS Auto Scaling automatically increases or decreases EC2 instances to match traffic patterns.

5. **Measured Service:**
   - Cloud systems automatically control and optimize resource usage by leveraging a metering capability at some level of abstraction.
   - **When to Use:** For cost optimization and transparency.
   - **When Not to Use:** Rarely unsuitable but might not align with fixed-cost budgeting models.
   - **Example:** AWS CloudWatch provides metrics on resource utilization (e.g., CPU, memory, storage), enabling cost transparency.

### Cloud Deployment Models:
- **Public Cloud:**
  - Operated by third-party providers like AWS, Azure, or GCP.
  - Resources are shared among multiple customers.
  - **Shines When:** Scalability, cost-effectiveness, and innovation are priorities.
  - **Avoid When:** Regulatory constraints require on-premises data storage.

- **Private Cloud:**
  - Infrastructure dedicated exclusively to a single organization, either managed internally or by a third-party.
  - **Shines When:** Data sovereignty, compliance, or custom hardware requirements are critical.
  - **Avoid When:** Flexibility and scalability are primary goals.

- **Hybrid Cloud:**
  - Combines public and private clouds, allowing data and applications to move between them.
  - **Shines When:** Organizations need to keep sensitive data on-premises but leverage the cloud for scalability.
  - **Avoid When:** Complexity of managing multiple environments outweighs benefits.

### Cloud Service Models:
- **IaaS (Infrastructure as a Service):**
  - Provides virtualized computing resources over the internet, including servers, storage, and networking.
  - **Shines When:** Full control over operating systems and applications is needed.
  - **Avoid When:** Managing infrastructure isn't a core competency.
  - **Example:** Amazon EC2, AWS VPC.

- **PaaS (Platform as a Service):**
  - Provides a platform for developing, testing, and deploying applications without managing the underlying infrastructure.
  - **Shines When:** Focus is on application development without infrastructure management.
  - **Avoid When:** Custom infrastructure configurations are required.
  - **Example:** AWS Elastic Beanstalk.

- **SaaS (Software as a Service):**
  - Delivers fully managed software applications over the internet.
  - **Shines When:** Rapid deployment of business applications is needed.
  - **Avoid When:** Customization beyond standard software offerings is required.
  - **Example:** Amazon WorkSpaces, Google Workspace.

---

## 2. AWS Networking Basics for CCP

### Key Concepts:

- **VPC (Virtual Private Cloud):**
  - A logically isolated virtual network in AWS where you can launch resources.
  - **Shines When:** Custom network configurations, security controls, and isolation are required.
  - **Avoid When:** Using fully managed services that abstract networking (e.g., AWS Lambda).

- **Subnets:**
  - A subdivision of a VPC's IP address range.
  - **Public Subnet:** Connected to the internet via an Internet Gateway.
  - **Private Subnet:** Not directly connected to the internet.
  - **Shines When:** Segregating workloads (public-facing vs. internal).
  - **Avoid When:** Simplicity is preferred (for small-scale applications).

- **Route Tables:**
  - Define rules (routes) that determine where network traffic is directed.
  - **Shines When:** Controlling traffic flow between subnets and external networks.

- **Internet Gateway (IGW):**
  - A VPC component that allows communication between instances in your VPC and the internet.
  - **Shines When:** You need public-facing resources (e.g., web servers).

- **NAT Gateway:**
  - Allows instances in private subnets to initiate outbound connections to the internet but prevents inbound connections.
  - **Shines When:** Instances need internet access for updates without exposing them.

- **Security Groups:**
  - Virtual firewalls for EC2 instances that control inbound and outbound traffic at the instance level.
  - **Shines When:** Fine-grained instance-level security is needed.
  - **Avoid When:** Subnet-wide rules are sufficient (use NACLs).

- **Network Access Control Lists (NACLs):**
  - Act as firewalls at the subnet level.
  - **Shines When:** Enforcing subnet-level security policies, like blocking malicious IP ranges.
  - **Avoid When:** Simpler, stateful security is preferred (use security groups).

### Shared Responsibility Model (Networking context):
- **AWS Responsibility:** Infrastructure security (hardware, software, networking, facilities).
- **Customer Responsibility:** Configuring security groups, NACLs, subnets, and traffic rules.

---

## 3. AWS Identity and Access Management (IAM)

### Key Concepts:

- **IAM Users:**
  - Represents an individual or service with long-term credentials (username, password, access keys).
  - **Shines When:** Assigning long-term access to specific individuals or services.

- **IAM Groups:**
  - A collection of IAM users.
  - **Shines When:** Applying uniform permissions to multiple users.

- **IAM Policies:**
  - Written in JSON, defining permissions for actions on AWS resources.
  - **Shines When:** Creating reusable, fine-grained permission sets.

- **IAM Roles:**
  - Assignable to AWS services, applications, or federated users.
  - **Shines When:** Temporary access or cross-account access is needed.

- **Principle of Least Privilege:**
  - Grant only the permissions necessary to perform a task.
  - **Shines When:** Enforcing security best practices.

- **Multi-Factor Authentication (MFA):**
  - Adds a second verification method (e.g., OTP from a mobile device).
  - **Shines When:** Strengthening account security against compromised credentials.

- **Shared Responsibility Model (IAM context):**
  - **AWS Responsibility:** Protecting the global infrastructure (hardware, software, networking, facilities).
  - **Customer Responsibility:** User management, permissions (IAM policies), MFA configuration, access controls.

---

## 4. Amazon EC2 Essentials

**Amazon EC2 (Elastic Compute Cloud):**
- Provides scalable compute capacity in the cloud.
- Allows you to launch virtual servers (instances) on-demand.
- **Shines When:** Custom server configurations or legacy applications are required.
- **Avoid When:** Fully managed, serverless compute (e.g., AWS Lambda) is preferred.

### Key Components:

- **Instance Types:**
  - Categorized into families (e.g., General Purpose, Compute Optimized, Memory Optimized).
  - **Shines When:** Matching instance types to workload requirements (e.g., compute-heavy vs. memory-heavy).

- **AMI (Amazon Machine Image):**
  - Templates that contain OS, applications, and configurations for launching EC2 instances.
  - **Shines When:** Rapidly deploying standardized environments.

- **Pricing Models:**
  - **On-Demand:** Pay by the second for instances.
  - **Shines When:** Unpredictable workloads.
  - **Reserved Instances:** 1- or 3-year commitment for predictable workloads.
  - **Shines When:** Long-term, stable workloads.
  - **Spot Instances:** Use spare capacity at lower costs, can be interrupted by AWS.
  - **Shines When:** Non-critical, flexible workloads.

- **Security Groups:**
  - Control traffic to instances (stateful).

- **Elastic IPs:**
  - Static public IP addresses you can allocate to instances.
  - **Shines When:** Consistent endpoint access is needed.

- **Key Pairs:**
  - Used for SSH access to Linux instances or RDP access to Windows instances.
  - **Shines When:** Secure access to EC2 instances.

### Shared Responsibility Model (EC2 context):
- **AWS Responsibility:** Hypervisor, hardware, physical data centers.
- **Customer Responsibility:** OS updates, patching, application configurations, firewall rules (security groups).

---

## 5. EC2 Instance Storage

### Storage Options:

- **EBS (Elastic Block Store):**
  - Persistent block-level storage for EC2.
  - **Shines When:** Durable storage is needed for data persistence.

- **Instance Store (Ephemeral Storage):**
  - Temporary storage physically attached to the host server.
  - **Shines When:** High-speed temporary storage is required (e.g., caching).

- **EFS (Elastic File System):**
  - Managed network file system accessible from multiple EC2 instances concurrently.
  - **Shines When:** Shared file storage across multiple instances.

- **S3 (Simple Storage Service):**
  - Object storage service for storing any amount of data.
  - **Shines When:** Storing static files, backups, media content.

### Shared Responsibility Model (Storage context):
- **AWS Responsibility:** Durability, availability of storage services.
- **Customer Responsibility:** Data encryption, access control policies, backups (snapshots).

