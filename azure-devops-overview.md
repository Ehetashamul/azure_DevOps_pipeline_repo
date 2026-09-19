# Azure DevOps Overview

## 1. What is Azure DevOps?

Azure DevOps is a set of cloud-based and on-premises development tools from Microsoft that helps teams plan work, manage source code, build applications, test software, publish packages, and automate deployments.

In simple terms:

> **Azure DevOps provides a platform for managing the complete software delivery lifecycle.**

A typical software delivery lifecycle looks like:

```text
Plan
  ↓
Code
  ↓
Build
  ↓
Test
  ↓
Package
  ↓
Release
  ↓
Deploy
  ↓
Monitor
  ↓
Feedback
  ↺
```

Azure DevOps provides tools that support most of these activities.

---

# 2. Why Azure DevOps?

Without a DevOps platform, organizations may use separate tools:

```text
Planning       → Jira
Source Code    → GitHub
CI             → Jenkins
Artifacts      → Nexus
Deployment     → Custom Scripts
Testing        → Separate tools
```

This can create integration and management overhead.

Azure DevOps provides an integrated platform:

```text
                    Azure DevOps
                         │
       ┌─────────────────┼──────────────────┐
       │                 │                  │
     Boards            Repos             Pipelines
       │                 │                  │
    Planning           Git              CI/CD
       │                 │                  │
       └─────────────────┼──────────────────┘
                         │
              ┌──────────┴──────────┐
              │                     │
           Test Plans           Artifacts
```

The major advantage is that these services can work together.

For example:

```text
Azure Boards
     ↓
Work Item
     ↓
Azure Repos
     ↓
Pull Request
     ↓
Azure Pipelines
     ↓
Build
     ↓
Test
     ↓
Artifact
     ↓
Deployment
```

---

# 3. Azure DevOps Core Services

Azure DevOps consists of five major services:

| Service          | Purpose                    |
| ---------------- | -------------------------- |
| Azure Boards     | Planning and work tracking |
| Azure Repos      | Source code management     |
| Azure Pipelines  | CI/CD automation           |
| Azure Test Plans | Testing                    |
| Azure Artifacts  | Package management         |

Think of them as:

```text
Boards     → PLAN
Repos      → CODE
Pipelines  → BUILD + DEPLOY
Test Plans → TEST
Artifacts  → PACKAGE
```

---

# 4. Azure Boards

## What is Azure Boards?

Azure Boards is used to plan, track, and manage development work.

It provides work items such as:

* Epic
* Feature
* User Story
* Task
* Bug

Example:

```text
Epic
 │
 ├── Feature
 │      │
 │      ├── User Story
 │      │       ├── Task
 │      │       └── Task
 │      │
 │      └── User Story
 │
 └── Feature
```

### Example

Suppose an organization wants to develop a payment system.

```text
Epic:
Payment Platform

Feature:
Credit Card Payment

User Story:
As a customer, I want to pay using a credit card.

Tasks:
- Create payment API
- Implement validation
- Write unit tests
- Deploy API
```

Azure Boards can connect these work items to commits, branches, pull requests, builds, and deployments.

---

# 5. Azure Repos

## What is Azure Repos?

Azure Repos provides Git repositories for storing and managing source code.

It supports:

* Git repositories
* Branches
* Pull requests
* Code reviews
* Branch policies
* Permissions
* Repository management

Basic workflow:

```text
Developer
    ↓
Local Git Repository
    ↓
Commit
    ↓
Push
    ↓
Azure Repos
    ↓
Pull Request
    ↓
Code Review
    ↓
Merge
```

Example:

```bash
git clone <repository>
git checkout -b feature/login
git add .
git commit -m "Add login functionality"
git push origin feature/login
```

The developer can then create a Pull Request in Azure Repos.

---

# 6. Azure Pipelines

## What is Azure Pipelines?

Azure Pipelines is the CI/CD engine of Azure DevOps.

It automates activities such as:

* Building code
* Running tests
* Creating packages
* Building Docker images
* Publishing artifacts
* Deploying applications
* Deploying infrastructure

Typical pipeline:

```text
Source Code
    ↓
Checkout
    ↓
Build
    ↓
Unit Test
    ↓
Package
    ↓
Publish Artifact
    ↓
Deploy to Dev
    ↓
Deploy to QA
    ↓
Approval
    ↓
Deploy to Production
```

---

# 7. CI — Continuous Integration

Continuous Integration means frequently integrating code changes into a shared repository and automatically validating those changes.

Example:

```text
Developer
    ↓
git push
    ↓
Azure Repos
    ↓
Pipeline Trigger
    ↓
Build
    ↓
Unit Tests
    ↓
Result
```

If the build or tests fail, the team gets immediate feedback.

### Main objective

Catch problems early.

---

# 8. CD — Continuous Delivery

Continuous Delivery means keeping software in a deployable state and automating the process of preparing it for release.

Example:

```text
Code
 ↓
Build
 ↓
Test
 ↓
Artifact
 ↓
Deploy to Dev
 ↓
Deploy to QA
 ↓
Production-ready
```

Production deployment may require an approval.

---

# 9. Continuous Deployment

Continuous Deployment goes one step further.

A successful pipeline can automatically deploy changes to production without a manual approval step.

```text
Code
 ↓
Build
 ↓
Test
 ↓
Artifact
 ↓
Production
```

The distinction is:

```text
Continuous Delivery
    ↓
Production deployment is ready
but may require approval.

Continuous Deployment
    ↓
Successful changes automatically
reach production.
```

---

# 10. Azure Test Plans

Azure Test Plans provides tools for managing testing activities.

It can be used for:

* Test plans
* Test suites
* Test cases
* Manual testing
* Test execution
* Test results

Example:

```text
Application
    ↓
Build
    ↓
Automated Tests
    ↓
Manual Test Cases
    ↓
Test Results
    ↓
Release
```

---

# 11. Azure Artifacts

Azure Artifacts is used to store and manage packages.

It supports package types such as:

* NuGet
* npm
* Maven
* Python
* Universal Packages

Example:

```text
Developer
    ↓
Build Package
    ↓
Azure Artifacts
    ↓
Application Pipeline
    ↓
Consume Package
```

This is useful when organizations have internal libraries that need to be shared across applications.

---

# 12. Azure DevOps Services vs Azure DevOps Server

There are two major deployment models.

## Azure DevOps Services

Azure DevOps Services is Microsoft's cloud-hosted offering.

```text
Microsoft Azure
      ↓
Azure DevOps Services
      ↓
Your Organization
      ↓
Your Projects
```

Microsoft manages the underlying platform.

You access it through the web and APIs.

---

## Azure DevOps Server

Azure DevOps Server is the self-hosted/on-premises version.

```text
Your Data Center
       ↓
Azure DevOps Server
       ↓
Projects
       ↓
Repositories
       ↓
Pipelines
```

The organization is responsible for infrastructure, upgrades, availability, and maintenance.

---

# 13. Organization

An Azure DevOps organization is a logical container for Azure DevOps resources.

A simplified hierarchy is:

```text
Organization
     ↓
Projects
     ↓
Teams
     ↓
Repositories / Pipelines / Boards / etc.
```

For example:

```text
Company-A
   │
   ├── Banking-Project
   ├── E-Commerce-Project
   └── Internal-Tools
```

An organization generally represents a company, business unit, or major organizational boundary.

---

# 14. Project

A project is a logical boundary inside an Azure DevOps organization.

A project can contain:

* Boards
* Repositories
* Pipelines
* Test Plans
* Artifacts
* Teams
* Permissions

Example:

```text
Organization: ABC-Corp

Projects:
├── Payment-Service
├── Customer-Portal
└── Mobile-App
```

A project commonly represents a product, application, or related group of work.

---

# 15. Team

A team is a group of people working together on a project.

Teams can have:

* Members
* Backlogs
* Boards
* Sprints
* Team settings

Example:

```text
Project: E-Commerce

Teams:
├── Backend Team
├── Frontend Team
├── DevOps Team
└── QA Team
```

---

# 16. Repository

A repository stores source code and its Git history.

Example:

```text
Repository: payment-api

payment-api/
├── src/
├── tests/
├── Dockerfile
├── azure-pipelines.yml
└── README.md
```

Azure Repos can host Git repositories.

---

# 17. Branch

A branch represents an independent line of development.

Example:

```text
main
 │
 ├── feature/login
 ├── feature/payment
 └── bugfix/session
```

A common enterprise strategy is:

```text
main
  │
  ├── feature/*
  │
  ├── bugfix/*
  │
  └── release/*
```

Branches allow developers to work independently without directly modifying the main branch.

---

# 18. Pull Request

A Pull Request is a request to merge changes from one branch into another.

Example:

```text
feature/payment
       │
       │ Pull Request
       ↓
      main
```

A PR can include:

* Code review
* Build validation
* Automated tests
* Required reviewers
* Work-item linking
* Branch policy checks

Typical flow:

```text
Developer
   ↓
Feature Branch
   ↓
Commit
   ↓
Push
   ↓
Pull Request
   ↓
Review
   ↓
Pipeline Validation
   ↓
Approval
   ↓
Merge
```

---

# 19. Pipeline

A pipeline defines an automated process.

For example:

```text
Build Pipeline:

Checkout
   ↓
Install dependencies
   ↓
Compile
   ↓
Run tests
   ↓
Publish artifact
```

Deployment pipeline:

```text
Artifact
   ↓
Deploy Dev
   ↓
Deploy QA
   ↓
Approval
   ↓
Deploy Production
```

---

# 20. YAML Pipeline

Azure Pipelines supports YAML-based pipeline definitions.

Example:

```yaml
trigger:
- main

pool:
  vmImage: ubuntu-latest

steps:
- script: echo "Hello Azure DevOps"
  displayName: "Hello World"
```

The pipeline configuration becomes code.

This approach is called:

> **Pipeline as Code**

Advantages:

* Version controlled
* Reviewable
* Reusable
* Auditable
* Easy to reproduce

---

# 21. Stage

A stage represents a logical boundary within a pipeline.

Example:

```text
Build
  ↓
Test
  ↓
Deploy-Dev
  ↓
Deploy-QA
  ↓
Deploy-Production
```

Each can be represented as a stage.

Example:

```yaml
stages:

- stage: Build

- stage: Test

- stage: DeployDev

- stage: DeployProduction
```

---

# 22. Job

A job is a collection of steps executed by an agent.

Hierarchy:

```text
Pipeline
   ↓
Stage
   ↓
Job
   ↓
Step
   ↓
Task / Script
```

Example:

```yaml
jobs:
- job: Build
  steps:
  - script: echo "Building application"
```

Multiple jobs can sometimes run in parallel.

---

# 23. Step

A step is an individual action inside a job.

Example:

```yaml
steps:
- script: npm install

- script: npm test

- script: npm build
```

Each item is a step.

---

# 24. Task

A task is a reusable unit of functionality provided for pipeline execution.

Example:

```yaml
steps:
- task: TerraformInstaller@1
  inputs:
    terraformVersion: latest
```

Tasks can simplify common operations.

However, pipelines can also execute:

* Bash
* PowerShell
* Python
* Command-line scripts

---

# 25. Agent

An agent is the compute environment that executes pipeline jobs.

Think:

```text
Pipeline
    ↓
Agent Pool
    ↓
Agent
    ↓
Job
    ↓
Steps
```

Two common types:

### Microsoft-hosted agent

Microsoft provides temporary build infrastructure.

```text
Pipeline
   ↓
Microsoft-hosted Agent
   ↓
Job
```

### Self-hosted agent

The organization provides and manages the machine.

```text
Pipeline
   ↓
Self-hosted Agent
   ↓
Your VM / Server
   ↓
Job
```

---

# 26. Agent Pool

An agent pool is a collection of agents.

Example:

```text
Agent Pool: Linux-Production

├── agent-01
├── agent-02
└── agent-03
```

Pipelines can target a specific pool.

---

# 27. Artifact

An artifact is a file or package produced by a build that can be consumed later.

Example:

```text
Source
  ↓
Build
  ↓
Application Package
  ↓
Artifact
  ↓
Deployment
```

For example:

```text
application.zip
```

could be published by the build stage and consumed by a deployment stage.

---

# 28. Environment

An environment represents a deployment target or logical deployment boundary.

Examples:

```text
dev
qa
uat
production
```

A pipeline might look like:

```text
Build
 ↓
Dev
 ↓
QA
 ↓
UAT
 ↓
Production
```

Azure DevOps environments can also be associated with deployment controls such as approvals and checks.

---

# 29. Service Connection

A service connection allows Azure DevOps pipelines to authenticate to external services.

For example:

```text
Azure Pipeline
      ↓
Service Connection
      ↓
Azure
```

Other possible targets include:

* Azure
* Kubernetes
* Docker registries
* GitHub
* Other services

Service connections are a major security topic because they determine how pipelines obtain access to external systems.

---

# 30. Variable

A variable stores a value that can be used during pipeline execution.

Example:

```yaml
variables:
  environment: dev
  applicationName: payment-api
```

Use:

```text
$(environment)
$(applicationName)
```

Variables can contain:

* Configuration values
* Paths
* Environment names
* Build information
* Secrets

Secret variables should be protected and should not be hard-coded into YAML.

---

# 31. Variable Group

A variable group provides shared variables that can be consumed by multiple pipelines.

Example:

```text
Variable Group
     │
     ├── environment
     ├── subscription
     └── applicationName
          │
          ├── Pipeline A
          ├── Pipeline B
          └── Pipeline C
```

Variable groups are useful for centralized configuration.

---

# 32. Parameters

Parameters are inputs used to customize pipeline structure or behavior.

Example:

```yaml
parameters:
- name: environment
  type: string
  default: dev
```

Parameters are particularly important when building reusable templates.

A key concept to remember:

```text
Variables
    ↓
Values used during pipeline execution

Parameters
    ↓
Inputs used to customize pipeline structure/definition
```

The exact evaluation timing and behavior becomes important in advanced YAML.

---

# 33. Approvals and Checks

Approvals and checks can control whether a pipeline is allowed to proceed.

Example:

```text
Deploy QA
    ↓
Approval
    ↓
Deploy Production
```

Checks can enforce requirements such as:

* Manual approval
* Branch restrictions
* Required templates
* Business hours
* External checks

This is commonly used to protect production environments.

---

# 34. Work Item

A work item represents a piece of work.

Examples:

* Epic
* Feature
* User Story
* Task
* Bug

Work items can be connected to development activity.

Example:

```text
User Story
     ↓
Feature Branch
     ↓
Commit
     ↓
Pull Request
     ↓
Build
     ↓
Deployment
```

This creates traceability from requirement to production deployment.

---

# 35. DevOps End-to-End Workflow

A practical Azure DevOps workflow can look like this:

```text
                Azure Boards
                     │
                     ↓
               User Story
                     │
                     ↓
                Azure Repos
                     │
                     ↓
              Feature Branch
                     │
                     ↓
                  Commit
                     │
                     ↓
               Pull Request
                     │
              ┌──────┴──────┐
              ↓             ↓
         Code Review      CI Build
                            │
                            ↓
                          Tests
                            │
                            ↓
                         Artifact
                            │
                            ↓
                     Azure Pipeline
                            │
              ┌─────────────┼─────────────┐
              ↓             ↓             ↓
             Dev           QA            UAT
                                           │
                                           ↓
                                       Approval
                                           │
                                           ↓
                                      Production
```

This is the core mental model you should remember.

---

# 36. Azure DevOps with Azure

Azure DevOps does not mean that your application must run on Azure.

Azure DevOps can deploy to many targets.

However, Azure services integrate very well with Azure DevOps.

Example:

```text
Azure Repos
     ↓
Azure Pipelines
     ↓
Azure Resource Manager
     ↓
Azure Resources
```

Possible deployment targets:

* Azure App Service
* Azure Functions
* Azure Kubernetes Service
* Azure Virtual Machines
* Azure Container Apps
* Azure Storage
* Azure SQL
* Azure infrastructure managed through Terraform

---

# 37. Azure DevOps with Terraform

Azure DevOps is commonly used to automate Terraform.

Example:

```text
Git Repository
      ↓
Azure Pipeline
      ↓
terraform fmt
      ↓
terraform init
      ↓
terraform validate
      ↓
terraform plan
      ↓
Approval
      ↓
terraform apply
      ↓
Azure Infrastructure
```

This creates an Infrastructure-as-Code workflow.

---

# 38. Azure DevOps with Docker

A typical container pipeline:

```text
Source Code
     ↓
Azure Pipeline
     ↓
Docker Build
     ↓
Docker Image
     ↓
Container Registry
```

For Azure:

```text
Azure Pipeline
     ↓
Docker Build
     ↓
Azure Container Registry
     ↓
AKS / App Service / Container Apps
```

---

# 39. Azure DevOps with Kubernetes

Azure DevOps can automate Kubernetes deployments.

Typical flow:

```text
Developer
    ↓
Git
    ↓
Azure Pipeline
    ↓
Docker Build
    ↓
Container Registry
    ↓
Kubernetes
    ↓
Deployment
    ↓
Service
```

With Azure:

```text
Azure DevOps
      ↓
ACR
      ↓
AKS
```

---

# 40. Azure DevOps Security Model

Security exists at multiple layers.

```text
Organization
     ↓
Project
     ↓
Repository
     ↓
Pipeline
     ↓
Service Connection
     ↓
Azure Resource
```

Important security concepts include:

* Authentication
* Authorization
* Permissions
* Microsoft Entra ID
* RBAC
* Service principals
* Managed identities
* Workload identity federation
* Secret management
* Key Vault
* Branch policies
* Approvals
* Least privilege

Security should be treated as a cross-cutting concern rather than a separate final step.

---

# 41. Azure DevOps and DevSecOps

Traditional pipeline:

```text
Code
 ↓
Build
 ↓
Test
 ↓
Deploy
```

DevSecOps pipeline:

```text
Code
 ↓
Security Scan
 ↓
Build
 ↓
Dependency Scan
 ↓
Unit Test
 ↓
Container Scan
 ↓
Artifact
 ↓
Deploy
 ↓
Runtime Security
```

Security is integrated throughout the software lifecycle.

---

# 42. Azure DevOps vs Azure

These are different concepts.

### Azure

Azure is Microsoft's cloud computing platform.

It provides:

* Compute
* Storage
* Networking
* Databases
* Kubernetes
* AI
* Security
* Monitoring

### Azure DevOps

Azure DevOps is Microsoft's software development and delivery platform.

```text
Azure
    ↓
Cloud Infrastructure

Azure DevOps
    ↓
Software Delivery Lifecycle
```

They integrate closely but are not the same product.

---

# 43. Azure DevOps vs Git

Git and Azure DevOps are also different.

### Git

Git is a distributed version control system.

It manages:

```text
Code
Branches
Commits
History
Merges
```

### Azure DevOps

Azure DevOps is a broader DevOps platform.

```text
Planning
Source Control
CI/CD
Testing
Packages
Security
```

Azure Repos uses Git as its source-control technology.

---

# 44. Azure DevOps as a Platform

A useful mental model is:

```text
                 Azure DevOps
                      │
       ┌──────────────┼───────────────┐
       │              │               │
     PLAN            CODE            DELIVER
       │              │               │
     Boards          Repos         Pipelines
                                      │
                         ┌────────────┼────────────┐
                         │            │            │
                       Build        Test        Deploy
                         │
                         ↓
                    Artifacts
```

---

# 45. Important Azure DevOps Terminology

Before moving deeper into Azure DevOps, understand these terms:

```text
Organization
Project
Team
Repository
Branch
Commit
Pull Request
Pipeline
Stage
Job
Step
Task
Agent
Agent Pool
Artifact
Environment
Service Connection
Variable
Variable Group
Parameter
Work Item
Approval
Check
Feed
Package
```

These terms will appear repeatedly throughout the rest of this repository.

---

# 46. A Simple Real-World Example

Suppose a company develops a Python application.

### Step 1 — Planning

Product team creates:

```text
Epic
 ↓
Feature
 ↓
User Story
```

using Azure Boards.

### Step 2 — Development

Developer creates:

```text
feature/payment
```

in Azure Repos.

### Step 3 — Development

Developer writes code and commits:

```bash
git add .
git commit -m "Add payment API"
git push origin feature/payment
```

### Step 4 — Pull Request

Developer creates:

```text
feature/payment
       ↓
Pull Request
       ↓
main
```

### Step 5 — CI

Azure Pipeline automatically:

```text
Checkout
 ↓
Install Python
 ↓
Install dependencies
 ↓
Run lint
 ↓
Run unit tests
 ↓
Build
```

### Step 6 — Artifact

The pipeline publishes:

```text
payment-api.zip
```

### Step 7 — Deployment

The artifact is deployed:

```text
Dev
 ↓
QA
 ↓
UAT
 ↓
Production
```

### Step 8 — Production Approval

Production requires an approval.

```text
UAT
 ↓
Manual Approval
 ↓
Production
```

This is a basic enterprise CI/CD workflow.

---

# 47. What Azure DevOps Does NOT Automatically Do

Azure DevOps is a platform, not a magic DevOps implementation.

It does not automatically guarantee:

* Good architecture
* Secure pipelines
* Good branching strategy
* Proper testing
* Zero downtime
* Reliable deployments
* Infrastructure security
* Correct permissions

Those depend on how the organization designs and uses the platform.

For example:

```text
Azure DevOps
      +
Good Engineering Practices
      +
Security
      +
Automation
      +
Monitoring
      =
Effective DevOps Platform
```

---

# 48. Key Advantages

Azure DevOps provides:

### Integrated tooling

Planning, source control, CI/CD, testing, and artifacts can work together.

### Pipeline as Code

YAML pipelines can be version controlled.

### Traceability

Work items can be linked with commits, PRs, builds, and deployments.

### Automation

Build and deployment processes can be automated.

### Enterprise controls

Permissions, approvals, checks, and environments support controlled delivery.

### Cloud integration

Strong integration with Azure services.

### Extensibility

Azure DevOps can integrate with external tools and services.

---

# 49. Limitations / Considerations

Azure DevOps also requires engineering discipline.

Common considerations include:

* YAML complexity can grow significantly.
* Poorly designed pipelines become difficult to maintain.
* Excessive permissions can create security risks.
* Self-hosted agents require maintenance.
* Secrets must be managed carefully.
* Large organizations need consistent governance.
* Pipeline templates and standards become important at scale.

---

# 50. Senior DevOps Engineer Mental Model

At beginner level, think:

```text
How do I create a pipeline?
```

At intermediate level:

```text
How do I automate CI/CD?
```

At senior level:

```text
How do I design a secure,
scalable, reusable and maintainable
software delivery platform?
```

A Senior DevOps Engineer should understand:

```text
Git
 ↓
Azure Repos
 ↓
CI/CD
 ↓
YAML
 ↓
Agents
 ↓
Authentication
 ↓
Service Connections
 ↓
Security
 ↓
Artifacts
 ↓
Terraform
 ↓
Containers
 ↓
Kubernetes
 ↓
Environments
 ↓
Approvals
 ↓
Observability
 ↓
Enterprise Governance
```

The focus gradually changes from **"how to run a pipeline"** to **"how to design the entire delivery system."**

---

# 51. Quick Revision

```text
Azure DevOps
│
├── Azure Boards
│     └── Plan & Track
│
├── Azure Repos
│     └── Source Code
│
├── Azure Pipelines
│     └── CI/CD
│
├── Azure Test Plans
│     └── Testing
│
└── Azure Artifacts
      └── Packages
```

Core pipeline hierarchy:

```text
Pipeline
   ↓
Stage
   ↓
Job
   ↓
Step
   ↓
Task / Script
```

Core organizational hierarchy:

```text
Organization
   ↓
Project
   ↓
Team
   ↓
Repositories / Pipelines / Boards
```

Typical CI/CD:

```text
Code
 ↓
Commit
 ↓
PR
 ↓
Build
 ↓
Test
 ↓
Artifact
 ↓
Deploy
 ↓
Approval
 ↓
Production
```

---

# 52. Interview Questions

## Basic

1. What is Azure DevOps?
2. What are the major services of Azure DevOps?
3. What is Azure Boards?
4. What is Azure Repos?
5. What is Azure Pipelines?
6. What is Azure Test Plans?
7. What is Azure Artifacts?
8. What is the difference between Azure and Azure DevOps?
9. What is Azure DevOps Services?
10. What is Azure DevOps Server?

## Intermediate

11. What is the difference between CI, Continuous Delivery, and Continuous Deployment?
12. What is a pipeline?
13. What is a stage?
14. What is a job?
15. What is a step?
16. What is an agent?
17. What is an agent pool?
18. What is an artifact?
19. What is an environment?
20. What is a service connection?
21. What is a variable?
22. What is a variable group?
23. What is a pipeline parameter?
24. What is a Pull Request?
25. What are branch policies?

## Senior

26. How would you design an enterprise Azure DevOps CI/CD platform?
27. How would you secure Azure DevOps service connections?
28. Service Principal vs Managed Identity vs Workload Identity Federation?
29. How would you design reusable YAML pipelines?
30. How would you manage multiple environments?
31. How would you implement production approvals?
32. How would you design a self-hosted agent architecture?
33. How would you implement Terraform through Azure Pipelines?
34. How would you integrate Docker and Kubernetes?
35. How would you implement DevSecOps in Azure Pipelines?
36. How would you manage secrets across hundreds of pipelines?
37. How would you troubleshoot a pipeline that is stuck waiting for an agent?
38. How would you design CI/CD for multiple teams using centralized templates?
39. How would you implement governance across multiple Azure DevOps projects?
40. How would you design a secure enterprise deployment pipeline?

---

# 53. One-Line Definition

> **Azure DevOps is an integrated platform for planning, developing, testing, packaging, and delivering software through collaborative tools and automated CI/CD workflows.**

---

# 54. Remember This Architecture

```text
                    AZURE DEVOPS
                         │
       ┌─────────────────┼─────────────────┐
       │                 │                 │
     BOARDS             REPOS           PIPELINES
       │                 │                 │
      PLAN              CODE           BUILD / TEST
                                           │
                                           ↓
                                      ARTIFACTS
                                           │
                                           ↓
                                     ENVIRONMENTS
                                           │
                                           ↓
                                      DEPLOYMENT
                                           │
                                           ↓
                                      PRODUCTION
```

This is the foundation. The next files should build on this mental model rather than repeat it.
