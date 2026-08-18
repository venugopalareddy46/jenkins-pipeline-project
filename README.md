::: {align="center"}
# 🚀 Jenkins CI/CD Basic Project

### 🔥 Jenkins • GitHub • CI/CD • DevOps Automation

[![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://www.jenkins.io/)
[![GitHub](https://img.shields.io/badge/GitHub-Source%20Control-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-Linux-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com/)
[![Git](https://img.shields.io/badge/Git-Version%20Control-F05032?style=for-the-badge&logo=git&logoColor=white)](https://git-scm.com/)
[![Status](https://img.shields.io/badge/Build-Success-2ea44f?style=for-the-badge&logo=checkmarx&logoColor=white)](#-project-outcome)

`<br>`{=html}

**A hands-on Jenkins CI project demonstrating GitHub integration,
credentials management, tool configuration, automated builds, console
output, and successful build verification.**
:::

---------------------------------------------------------------------
<div align="center">

![Jenkins CI/CD Banner](assets/jenkins-banner.svg)

</div>

---

## 📌 Project Overview

This project demonstrates a basic **Continuous Integration (CI)**
workflow using Jenkins and GitHub.

The implementation covers:

-   Jenkins installation on Ubuntu EC2
-   Jenkins Dashboard and configuration
-   User and permission management
-   Jenkins plugins
-   Git, JDK, Maven and Node.js configuration
-   GitHub credentials
-   Jenkins Freestyle job
-   GitHub source-code checkout
-   Shell-based build execution
-   Console output verification
-   Rebuilding after a GitHub repository change

------------------------------------------------------------------------

## 🎯 Objective

To understand Jenkins and CI/CD, install and configure Jenkins, manage
users and credentials, configure development tools, integrate GitHub,
and execute a basic Jenkins CI job.

------------------------------------------------------------------------

## 🧰 Technologies & Tools

  Technology    Purpose
  ------------- ---------------------------------
  🔴 Jenkins    CI automation
  🟣 GitHub     Source code management
  🟠 Git        Version control
  🟤 Ubuntu     Jenkins server operating system
  ☕ Java JDK   Jenkins runtime
  🔵 Maven      Build automation
  🟢 Node.js    JavaScript runtime
  ☁️ AWS EC2    Jenkins hosting environment

------------------------------------------------------------------------

<div align="center">

![Section Banner](assets/architecture-banner.svg)

</div>

## 🏗️ Jenkins Architecture

``` text
                         ┌──────────────────┐
                         │    Developer     │
                         └────────┬─────────┘
                                  │
                                  ▼
                         ┌──────────────────┐
                         │     GitHub       │
                         └────────┬─────────┘
                                  │
                                  ▼
                    ┌──────────────────────────┐
                    │    Jenkins Controller    │
                    │                          │
                    │ Jobs • Users • Plugins   │
                    │ Credentials • Scheduling │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │ Jenkins Built-In Node /  │
                    │         Agent            │
                    └────────────┬─────────────┘
                                 │
                         ┌───────┴───────┐
                         ▼               ▼
                      Checkout         Build
                         │               │
                         └───────┬───────┘
                                 ▼
                         ┌────────────────┐
                         │    SUCCESS     │
                         └────────────────┘
```

### Controller

The Jenkins Controller manages jobs, configuration, users, plugins,
credentials, scheduling, and agents.

### Agent

The Jenkins Agent executes build and testing tasks assigned by Jenkins.

------------------------------------------------------------------------

<div align="center">

![Section Banner](assets/workflow-banner.svg)

</div>

## 🔄 CI/CD Workflow

``` text
Developer
    │
    ▼
GitHub
    │
    ▼
Jenkins
    │
    ├── Git Checkout
    │
    ├── Build
    │
    ├── Test
    │
    ├── Docker
    │
    └── Kubernetes
    │
    ▼
Application
```

### Basic CI Flow Implemented

``` text
GitHub
   ↓
Jenkins Job
   ↓
Git Checkout
   ↓
Execute Shell
   ↓
Console Output
   ↓
Build SUCCESS
```

------------------------------------------------------------------------

## 📂 Repository Structure

``` text
jenkins-basic-project/
│
└── README.md
```

------------------------------------------------------------------------


<div align="center">

![Jenkins Concepts](assets/concepts-banner.svg)

</div>

# 📚 Jenkins Concepts

## What is Jenkins?

Jenkins is an open-source automation server used to automate software development and DevOps activities such as building, testing, and deploying applications.

Jenkins helps teams reduce manual work and create repeatable automation workflows.

```text
Developer
    ↓
GitHub
    ↓
Jenkins
    ↓
Build
    ↓
Test
    ↓
Deploy
```

## What is CI/CD?

**Continuous Integration (CI)** is the practice of frequently integrating source-code changes into a shared repository and automatically building and testing the application.

**Continuous Deployment (CD)** extends the automation process by deploying successfully tested changes to the target environment.

```text
Code Change
    ↓
GitHub
    ↓
Jenkins
    ↓
Build
    ↓
Test
    ↓
Deploy
```

## Continuous Integration vs Continuous Deployment

| Continuous Integration | Continuous Deployment |
|---|---|
| Integrates source code | Deploys the application |
| Automatically builds code | Automatically releases changes |
| Runs automated tests | Deploys successful changes |
| Finds issues early | Reduces manual deployment work |

**CI = Build + Test**

**CD = Release + Deploy**

## Jenkins Architecture

Jenkins uses a Controller-Agent architecture for managing and executing automation tasks.

```text
                 ┌────────────────────┐
                 │ Jenkins Controller │
                 │                    │
                 │ Jobs               │
                 │ Configuration      │
                 │ Credentials        │
                 │ Plugins            │
                 │ Scheduling         │
                 └─────────┬──────────┘
                           │
                ┌──────────┴──────────┐
                ▼                     ▼
        ┌──────────────┐      ┌──────────────┐
        │    Agent     │      │    Agent     │
        │              │      │              │
        │ Build        │      │ Build        │
        │ Test         │      │ Test         │
        └──────────────┘      └──────────────┘
```

### Jenkins Controller

The Controller manages Jenkins configuration, jobs, users, credentials, plugins, build scheduling, and connected agents.

### Jenkins Agent

An Agent executes build and testing tasks assigned by the Controller.

For this project, the Jenkins **Built-In Node** was used to execute the basic job.

## How Jenkins Works in a Real-Time Project

A typical DevOps workflow can be:

```text
Developer
    ↓
GitHub
    ↓
Jenkins
    ↓
Git Checkout
    ↓
Build
    ↓
Test
    ↓
Code Quality
    ↓
Docker Build
    ↓
Container Registry
    ↓
Kubernetes
    ↓
Application
```

Jenkins acts as the automation layer connecting source-code changes with build, test, and deployment activities.

## Jenkins Job

A Jenkins Job defines the automation Jenkins should execute.

For this project, a **Freestyle Project** was created:

```text
GitHub Repository
      ↓
Git Checkout
      ↓
Execute Shell
      ↓
Console Output
      ↓
Build Status
```

## Jenkins Credentials

Jenkins Credentials provide secure authentication when Jenkins connects to external systems such as GitHub.

Credentials should be stored in Jenkins rather than hardcoded into source code.

```text
Jenkins Job
     ↓
credentialsId
     ↓
Jenkins Credentials
     ↓
GitHub
```

## Jenkins Plugins

Plugins extend Jenkins functionality and provide integrations with development and DevOps tools.

Examples used or explored in this assignment include:

- Git
- Pipeline
- Credentials
- Maven
- NodeJS
- Docker

## Jenkins Tools

Jenkins can use development tools configured through **Manage Jenkins → Tools**.

Tools configured or verified in this project:

```text
Git
JDK
Maven
Node.js
```

## Build and Console Output

When a Jenkins job runs, Jenkins records the execution details in the **Console Output**.

A successful build ends with:

```text
Finished: SUCCESS
```

This provides a simple way to verify whether the job completed successfully.


# 🛠️ Jenkins Installation

## Update Ubuntu

``` bash
sudo apt update -y
sudo apt upgrade -y
```

## Install Java

``` bash
sudo apt install default-jdk -y
```

Verify:

``` bash
java -version
```

## Install Jenkins

Follow the official Jenkins Linux installation documentation:

https://www.jenkins.io/doc/book/installing/linux/

## Start Jenkins

``` bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Check status:

``` bash
sudo systemctl status jenkins
```

Expected:

``` text
Active: active (running)
```

## Check Jenkins Port

``` bash
sudo ss -tulpn
```

Jenkins normally runs on:

``` text
8080
```

## AWS Security Group

Allow inbound traffic for:

``` text
Type: Custom TCP
Port: 8080
Source: Your IP
```

For temporary lab testing, a wider source can be used, but restricting
access to your IP is recommended.

## Access Jenkins

``` text
http://YOUR_EC2_PUBLIC_IP:8080
```

## Get Initial Administrator Password

``` bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Install the suggested plugins and create the Jenkins administrator
account.

> ⚠️ Never commit the initial password or any other secret to GitHub.

------------------------------------------------------------------------

# 👤 Jenkins Users & Configuration

Jenkins configuration was explored through:

``` text
Manage Jenkins
```

Areas covered:

-   Users
-   Permissions
-   Plugins
-   Tools
-   Credentials
-   System configuration

### Test User

A test Jenkins user was created:

``` text
Username: testuser
Name: Jenkins Test User
```

### Common Permissions

``` text
Overall/Read
Job/Read
Job/Build
Job/Configure
Job/Create
Job/Delete
Credentials/View
Credentials/Manage
```

------------------------------------------------------------------------

# 🔌 Jenkins Plugins

Common plugins explored/configured:

-   Git
-   Pipeline
-   Credentials
-   Maven
-   NodeJS
-   Docker

Plugins extend Jenkins and provide integration with development,
testing, security, container, and deployment tools.

------------------------------------------------------------------------

# 🔧 Jenkins Tools Configuration

The following tools were installed and verified:

``` text
Git
JDK
Maven
Node.js
```

### Git

``` bash
sudo apt install git -y
git --version
```

### Java

``` bash
sudo apt install default-jdk -y
java -version
```

### Maven

``` bash
sudo apt install maven -y
mvn -version
```

### Node.js

``` bash
sudo apt install nodejs npm -y
node --version
npm --version
```

Jenkins tool configuration:

``` text
Manage Jenkins
      ↓
Tools
      ↓
JDK
Git
Maven
NodeJS
```

------------------------------------------------------------------------

<div align="center">

![Section Banner](assets/security-banner.svg)

</div>

# 🔐 Jenkins Credentials

Credentials are used when Jenkins needs to authenticate with external
systems such as GitHub.

For a private GitHub repository, a credential was configured with:

``` text
Username: GitHub username
Password: GitHub Personal Access Token
ID: github-credentials
```

### Secure Credential Flow

``` text
Jenkins Job
     │
     ▼
credentialsId
     │
     ▼
Jenkins Credentials Store
     │
     ▼
GitHub
```

### Security Best Practices

Never hardcode:

-   ❌ Passwords
-   ❌ GitHub Personal Access Tokens
-   ❌ API keys
-   ❌ AWS credentials
-   ❌ SSH private keys

Use Jenkins Credentials Manager instead.

------------------------------------------------------------------------

<div align="center">

![Section Banner](assets/job-banner.svg)

</div>

# 🚀 Basic Jenkins Job

## Job Details

  Setting         Value
  --------------- -------------------------
  Job Name        `github-build`
  Job Type        Freestyle Project
  SCM             Git
  Branch          `*/main`
  Repository      `jenkins-basic-project`
  Credential ID   `github-credentials`

------------------------------------------------------------------------

## 🔗 GitHub Configuration

Repository:

``` text
https://github.com/<USERNAME>/jenkins-basic-project.git
```

Branch:

``` text
*/main
```

For a private repository:

``` text
github-credentials
```

is selected from Jenkins Credentials.

------------------------------------------------------------------------

## 🧪 Build Step

The Jenkins job executes:

``` bash
echo "Jenkins build started"

echo "Current directory:"
pwd

echo "Repository files:"
ls -la

echo "Git version:"
git --version

echo "Jenkins build completed"
```

------------------------------------------------------------------------

# ▶️ Build Execution

## Build #1

The first Jenkins build performs:

``` text
GitHub
   ↓
Checkout Source Code
   ↓
Execute Shell
   ↓
Console Output
   ↓
SUCCESS
```

Expected result:

``` text
Finished: SUCCESS
```

------------------------------------------------------------------------

# 🔄 Repository Change & Build #2

A small change was made to `README.md`.

Example:

``` text
Jenkins Basic CI Project
Build and Test
```

The change was committed and pushed to GitHub.

``` bash
git add README.md
git commit -m "Update Jenkins project"
git push
```

Jenkins was then executed again.

``` text
GitHub Change
     ↓
Jenkins
     ↓
Checkout Latest Code
     ↓
Build #2
     ↓
SUCCESS
```

Expected result:

``` text
Finished: SUCCESS
```

------------------------------------------------------------------------

# 📊 Build Verification

Build results can be checked from:

``` text
Jenkins Dashboard
      ↓
github-build
      ↓
Build History
      ↓
Build #1 / Build #2
      ↓
Console Output
```

Successful builds display:

``` text
Finished: SUCCESS
```

------------------------------------------------------------------------

# 🧯 Troubleshooting

## Jenkins Node Offline

If the job displays:

``` text
Waiting for next available executor
```

check:

``` text
Manage Jenkins
   ↓
Nodes
   ↓
Built-In Node
```

Make sure the node is **Online** and has available executors.

## Git Branch Error

If Jenkins reports:

``` text
Couldn't find any revision to build
```

verify the branch configuration.

For this project:

``` text
*/main
```

## Disk Space Check

Check disk usage:

``` bash
df -h
```

Make sure sufficient disk and temporary space are available for Jenkins
operations.

------------------------------------------------------------------------

# 📸 Screenshots

Recommended project screenshots:

### Jenkins Installation

Show Jenkins installation, service status, and Web UI.

### Jenkins Dashboard

Show the Jenkins Dashboard after successful setup.

### Jenkins Configuration

Show:

-   Manage Jenkins
-   Users
-   Plugins
-   Tools
-   Credentials

### Jenkins Job Configuration

Show:

``` text
github-build
GitHub Repository
*/main
github-credentials
```

### Successful Build

Show:

``` text
Build #1
Finished: SUCCESS
```

### Console Output

Show Jenkins Git checkout and build output.

### GitHub Change

Show the updated `README.md`.

### Second Successful Build

Show:

``` text
Build #2
Finished: SUCCESS
```

> 🔒 **Security:** Hide passwords, tokens, API keys, private keys, and
> other sensitive information before publishing screenshots.

------------------------------------------------------------------------

# 📚 Key Learnings

-   Jenkins fundamentals
-   CI/CD concepts
-   Jenkins Controller and Agent architecture
-   Jenkins installation
-   Jenkins user management
-   Permissions
-   Plugin management
-   Tool configuration
-   Credential management
-   GitHub integration
-   Freestyle jobs
-   Build execution
-   Console output
-   Build verification

------------------------------------------------------------------------

<div align="center">

![Section Banner](assets/result-banner.svg)

</div>

# ✅ Project Outcome

Successfully created and executed a Jenkins CI job that connects to
GitHub, pulls source code, executes a build command, verifies the
Console Output, and successfully rebuilds the project after a GitHub
repository change.

------------------------------------------------------------------------

# 👨‍💻 Author

## Venu Gopala Reddy Eppala

**Cloud & DevOps \| AWS \| Jenkins \| Docker \| Kubernetes \| Terraform
\| CI/CD**

------------------------------------------------------------------------

::: {align="center"}
### ⭐ Jenkins CI/CD Practical Project

**GitHub → Jenkins → Build → Console Output → SUCCESS**
:::
