
# VPROFILE PROJECT SETUP

## About the Project
In this project, we will be setting up a multi-tier web application stack. This setup will serve as the baseline for upcoming projects. The key steps involved are:
- Deploying the stack on AWS and refactoring it.
- Containerizing the application.
- Deploying the project on a Kubernetes cluster.
- Setting up the project and conducting R&D.

## Tools
* Hypervisor: Oracle VM VirtualBox
* Provisioning: Vagrant
* Command Line Tool: Bit-Bash
* Integrated Development Environment (IDE): Visual Studio
* Services: Nginx, Apache Tomcat, RabbitMQ, Memcached, MySQL
## Objective
* Set up a virtual machine locally.
* Establish a baseline for the next project.
## Architectural Design

<img src="https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/2ad6a1e1-af9b-4b1f-be1a-5d88071a5db6" width="500" height="300">


This architectural design illustrates the multi-tier web application stack we aim to implement. It includes:

- **Front-end Layer:** Managed by Nginx, handling web traffic and requests.
Application Layer: Handled by Apache Tomcat, managing the core application logic.
- **Messaging Layer:** Facilitated by RabbitMQ for efficient message queuing.
- **Caching Layer:** Managed by Memcached, ensuring quick data retrieval.
- **Database Layer:** Supported by MySQL for reliable data storage.

This project will involve setting up each layer, ensuring seamless integration, and deploying it on a scalable infrastructure. The skills and knowledge gained from this project will be crucial for subsequent, more advanced projects.

# Web App Setup on AWS Cloud

## Lift and Shift Application Workload

In this project, we are going to host and run our application on the AWS cloud for production using the lift and shift strategy.

### What is the Purpose of This Project?

The primary purpose of this project is to migrate existing application services from on-premises infrastructure to the AWS cloud. This approach, known as lift and shift, involves moving applications as-is to the cloud, without making significant changes to the application architecture.

### Why Did This Project Come into Existence?

Organizations often have various services like databases (PostgreSQL, Oracle), application servers (Tomcat), LAMP stacks, DNS services, and more running on physical or virtual machines within their data centers. These services are crucial for powering their applications and handling workloads.

Managing these services within a data center environment can be challenging and costly, requiring multiple specialized teams:
- **Virtualization Team**: To manage virtual platforms.
- **Data Center Team**: For data center operations.
- **Monitoring Team**: To monitor services 24/7.
- **System Admin Team**: For general system administration tasks.

### Problems with On-Premises Management

- **Complex Management**: Coordinating between different teams and managing various services can be cumbersome and time-consuming.
- **Scale Up/Down Complexity**: Adjusting resources to meet changing demands is often difficult and inefficient.
- **High Costs**: Procuring hardware and maintaining data center operations incurs significant expenses.
- Manual Process, Difficult to automate and Time Consuming



### Solution

To address the challenges of on-premises infrastructure management, we propose a cloud-based solution using AWS services:

#### Cloud Setup
- **AWS Environment Configuration**: Set up VPCs, subnets, and security groups for a secure and scalable network environment.

#### Automation
- **Infrastructure as Code (IaC)**: Use AWS CloudFormation or Terraform to automate resource provisioning and management.
- **CI/CD Pipelines**: Implement using AWS CodePipeline, CodeBuild, and CodeDeploy for automated build, test, and deployment.

#### AWS Services
- **Amazon EC2**: Deploy scalable virtual servers for application workloads.
- **Elastic Load Balancing (ELB)**: Distribute traffic across multiple EC2 instances for high availability.
- **Auto Scaling**: Automatically adjust the number of EC2 instances based on demand.
- **Amazon EFS/S3**: Use EFS or S3 for scalable and durable shared storage.
- **Amazon Certificate Manager (ACM)**: Manage SSL/TLS certificates for secure traffic.
- **Amazon Route 53**: Implement a scalable DNS service for efficient and reliable routing.

This solution simplifies management, enhances scalability, and reduces costs, ensuring a streamlined and efficient cloud infrastructure for production workloads.
  

### Benefits of Lift and Shift to AWS
- **Simplified Management**: AWS provides a unified platform to manage all services, reducing the need for separate teams.
- **Scalability**: AWS allows for easy scaling of resources up or down based on demand, improving efficiency and responsiveness.
- **Cost Efficiency**: Using AWS can lower costs by eliminating the need for physical hardware and reducing operational expenses.

By migrating to AWS, organizations can achieve better resource management, enhanced scalability, and cost savings, while maintaining the reliability and performance of their applications.

## Project flowchat:
<img src="https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/b5dcddcb-5e66-406e-a28f-bea08a89d3a6" alt="Screenshot 2024-06-24 110716" width="500" height="300">

## This site contain detail [explanation of project](https://github.com/Rishikesh11kr/DevOps-Projects/blob/master/VPROFILE%20PROJECT/Detailed%20Explanation.txt )


### Flow of Execution

1. **AWS Account Login**: Start by logging into your AWS account.

2. **Key Pair Creation**: Create key pairs to securely access EC2 instances.

3. **Security Group Setup**:
   - Create security groups for the load balancer, Tomcat instances, and backend services to control access.

4. **EC2 Instance Launch**:
   - Launch EC2 instances using user data scripts (bash scripts) for configuration during instance initialization.

5. **IP to Name Mapping in Route 53**:
   - Update IP to name mappings in Amazon Route 53 for DNS resolution of backend services.

6. **Application Build and Artifact Management**:
   - Build the application from source code locally on your laptop.
   - Upload the application artifact to an Amazon S3 bucket for storage.

7. **Artifact Deployment to EC2**:
   - Download the application artifact from the S3 bucket to the EC2 instances where Apache Tomcat will run.

8. **Load Balancer Setup with HTTPS**:
   - Configure an Elastic Load Balancer (ELB) with HTTPS to handle incoming traffic securely.

9. **DNS Configuration in GoDaddy**:
   - Map the endpoint of the Elastic Load Balancer to a domain name in GoDaddy DNS.

10. **Verification**:
    - Verify the entire setup to ensure all components are functioning correctly.

11. **Auto Scaling Group Creation**:
    - Create an auto-scaling group for Apache Tomcat instances to automatically adjust capacity based on traffic demand.

12. **Final Setup and Testing**:
    - Conduct final tests and validations to ensure the scalability, security, and reliability of the setup.



<img src="https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/58e74e59-6844-4eef-aeca-81406b8def21" width="500" height="300">



--------------------------------------------------------------------------------------

# Part 1: Refactoring with AWS

## About Part 1
This phase involves re-architecting services for the AWS cloud, aiming to enhance business continuity and operational efficiency. Leveraging Platform as a Service (PaaS) and Software as a Service (SaaS) models, we benefit from flexible, elastic services where scaling is managed primarily by cloud vendors, offering a pay-as-you-go pricing model.

### AWS Services Used in This Project
- **Elastic Beanstalk**: Deploy and manage applications without worrying about the infrastructure.
- **S3/EFS**: Scalable storage solutions for static and dynamic content.
- **RDS Instances**: Managed relational databases for scalable data storage.
- **Amazon MQ**: Managed message broker service for reliable communication.
- **Route 53**: Scalable DNS service for routing end users to internet applications.
- **CloudFront**: Content Delivery Network (CDN) for fast and secure delivery of content to users worldwide.
  
<img src="https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/7909ca5a-2a93-4714-adb6-3c98b7ff03b8" width="500"  height="300">

## This site contain detail [explanation of AWS architecture ](https://github.com/Rishikesh11kr/DevOps-Projects/blob/master/VPROFILE%20PROJECT/AWS%20Arc.txt )

-------------------------------------------------------------------------------------------------------------
# Part 2: Continuous integration Jenkins and tools

Using Continuous Integration (CI) with Jenkins offers several key benefits for your project:

1. **Automated Testing and Deployment**:
   - Ensures consistent and stable code by automatically running tests on code changes.
   - Identifies bugs early, reducing the chances of them reaching production.

2. **Improved Code Quality**:
   - Integrates with tools like SonarQube for static code analysis, maintaining high code quality.
   - Facilitates automated code reviews, ensuring adherence to coding standards.

3. **Faster Feedback Loop**:
   - Provides immediate feedback to developers, allowing quick issue resolution.
   - Enhances development speed and reduces time-to-market through rapid iterations.

4. **Enhanced Collaboration**:
   - Offers centralized pipeline management, improving team collaboration.
   - Seamlessly integrates with version control systems like GitHub, enabling smooth teamwork.

5. **Scalability and Flexibility**:
   - Handles complex, multi-stage pipelines that scale with your project's needs.
   - Supports a wide range of plugins and integrations, enhancing its flexibility.

These benefits make Jenkins an excellent choice for improving the efficiency and reliability of your project's development and deployment processes.


## TOOLS:

<img src="https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/1806942b-d10f-4a8e-b25c-650ee8004f7b " width="500" height="170">

<img src="https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/dadc289c-53a4-45ff-9d10-b674d4917e64" width="500" height="170">

