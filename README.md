# 🚀 Jenkins Basics & CI/CD

![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-D24939?logo=jenkins&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Source%20Control-181717?logo=github&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Linux-E95420?logo=ubuntu&logoColor=white)
![Git](https://img.shields.io/badge/Git-Version%20Control-F05032?logo=git&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 👨‍💻 Name

**Venu Gopala Reddy Eppala**

## 📌 Assignment

**Jenkins Basics, Installation, Configuration, GitHub Integration and Basic CI Job**

## 🎯 Objective

To understand Jenkins and CI/CD, install and configure Jenkins, manage users and credentials, configure development tools, integrate GitHub, and execute a basic Jenkins CI job.

---

# 📖 Concepts

## Jenkins

Jenkins is an open-source automation server used to automate software development and DevOps activities such as building, testing, and deploying applications.

## CI/CD

**Continuous Integration (CI)** automatically builds and tests code whenever developers integrate changes.

**Continuous Deployment (CD)** automatically deploys successfully tested code to the target environment.

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
````

## Continuous Integration vs Continuous Deployment

| Continuous Integration      | Continuous Deployment           |
| --------------------------- | ------------------------------- |
| Builds and tests code       | Deploys the application         |
| Finds errors early          | Automates releases              |
| Focuses on code integration | Focuses on application delivery |

## Jenkins Architecture

```text
             Jenkins Controller
                    │
          ┌─────────┴─────────┐
          │                   │
       Agent 1             Agent 2
          │                   │
        Build               Build
          │                   │
          └─────────┬─────────┘
                    │
                Deployment
```

### Jenkins Controller

The Controller manages Jenkins jobs, configuration, users, plugins, credentials, and agents.

### Jenkins Agent

The Agent executes build and testing tasks assigned by Jenkins.

## Real-Time Jenkins Workflow

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
Docker
    ↓
Kubernetes
    ↓
Application
```

---

# 🧩 Task 1: Jenkins Basics and Installation

## Steps

### Update Ubuntu

```bash
sudo apt update -y
sudo apt upgrade -y
```

### Install Java

```bash
sudo apt install default-jdk -y
```

Verify Java:

```bash
java -version
```

### Install Jenkins

Jenkins was installed on an Ubuntu EC2 instance using the official Jenkins installation procedure.

Official Jenkins documentation:

[https://www.jenkins.io/doc/book/installing/linux/](https://www.jenkins.io/doc/book/installing/linux/)

### Start Jenkins

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Check Jenkins status:

```bash
sudo systemctl status jenkins
```

Expected result:

```text
Active: active (running)
```

### Check Jenkins Port

```bash
sudo ss -tulpn | grep 8080
```

Jenkins uses:

```text
Port: 8080
```

### Configure EC2 Security Group

Allow inbound traffic:

```text
Type: Custom TCP
Port: 8080
Source: My IP
```

For temporary testing, port 8080 can be opened as required.

### Access Jenkins Web UI

```text
http://YOUR_EC2_PUBLIC_IP:8080
```

### Get Jenkins Initial Password

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Enter the password in the Jenkins Web UI.

Install the suggested plugins and create the Jenkins administrator account.

## Outcome

Jenkins was installed successfully and accessed through the Web UI.

---

# 🧩 Task 2: Jenkins UI and Configuration

## Steps

### Explore Jenkins Dashboard

The following sections were explored:

```text
Dashboard
Manage Jenkins
New Item
Builds
```

### Create Test User

Navigate to:

```text
Manage Jenkins
→ Users
→ Create User
```

Create a test user:

```text
Username: testuser
Name: Jenkins Test User
Password: ********
```

Do not expose the password in screenshots or documentation.

### Understand User Permissions

Common Jenkins permissions include:

```text
Overall/Read
Job/Read
Job/Build
Job/Configure
Job/Create
Job/Delete
Credentials/View
Credentials/Manage
```

### Explore Plugin Management

Navigate to:

```text
Manage Jenkins
→ Plugins
```

Common Jenkins plugins include:

* Git
* Pipeline
* Credentials
* Maven
* NodeJS
* Docker

### Explore Global and System Configuration

Navigate to:

```text
Manage Jenkins
→ System
```

Review the available Jenkins system and global configuration options.

## Outcome

Users, permissions, plugins, and Jenkins configuration were explored successfully.

---

# 🧩 Task 3: Jenkins Tools Configuration

## Steps

### Install Git

```bash
sudo apt install git -y
```

Verify:

```bash
git --version
```

### Verify Java

```bash
java -version
```

### Install Maven

```bash
sudo apt install maven -y
```

Verify:

```bash
mvn -version
```

### Install Node.js

```bash
sudo apt install nodejs npm -y
```

Verify:

```bash
node --version
npm --version
```

### Configure Jenkins Tools

Navigate to:

```text
Manage Jenkins
→ Tools
```

Configure or verify:

```text
JDK
Git
Maven
NodeJS
```

## Outcome

Git, JDK, Maven, and Node.js were installed, verified, and configured in Jenkins.

---

# 🧩 Task 4: Jenkins Credentials

## Steps

### Open Jenkins Credentials

Navigate to:

```text
Manage Jenkins
→ Credentials
→ System
→ Global credentials
→ Add Credentials
```

For a private GitHub repository, configure:

```text
Kind: Username with password
Username: GitHub username
Password: GitHub Personal Access Token
ID: github-credentials
```

### Why Credentials Are Required

Jenkins requires credentials to securely authenticate with external systems such as GitHub.

```text
Jenkins
   ↓
Credentials
   ↓
GitHub
   ↓
Private Repository
```

### Credential Security

Credentials should not be hardcoded inside Jenkins pipelines or source code.

Instead:

```text
Jenkins Job
     ↓
credentialsId
     ↓
Jenkins Credentials
     ↓
GitHub
```

### Security

Never expose:

* Passwords
* GitHub Personal Access Tokens
* API Keys
* AWS Credentials
* SSH Private Keys

## Outcome

GitHub credentials were securely created and configured in Jenkins.

---

# 🧩 Task 5: Basic Jenkins Job

## Steps

### Create GitHub Repository

Create a GitHub repository:

```text
jenkins-basic-project
```

Add:

```text
README.md
```

Example content:

```text
Jenkins Basic CI Project
```

Repository URL:

```text
https://github.com/<USERNAME>/jenkins-basic-project.git
```

Replace `<USERNAME>` with your GitHub username.

### Create Jenkins Job

Navigate to:

```text
Jenkins Dashboard
→ New Item
```

Enter:

```text
github-build
```

Select:

```text
Freestyle project
```

Click **OK**.

### Configure GitHub Repository

Navigate to:

```text
Source Code Management
→ Git
```

Repository URL:

```text
https://github.com/<USERNAME>/jenkins-basic-project.git
```

For a private repository, select:

```text
github-credentials
```

### Configure Branch

The GitHub repository uses the `main` branch.

Configure:

```text
*/main
```

### Configure Build Step

Navigate to:

```text
Build Steps
→ Add build step
→ Execute shell
```

Add:

```bash
echo "Jenkins build started"

echo "Current directory:"
pwd

echo "Repository files:"
ls -la

echo "Git version:"
git --version

echo "Jenkins build completed"
```

Click **Save**.

### Run Jenkins Build

Click:

```text
Build Now
```

Jenkins creates:

```text
Build #1
```

### View Console Output

Open:

```text
Build #1
→ Console Output
```

The console output should show the GitHub checkout and build commands.

Expected result:

```text
Jenkins build started
```

```text
Current directory:
/var/lib/jenkins/workspace/github-build
```

```text
Repository files:
README.md
```

```text
Git version:
git version ...
```

Final result:

```text
Finished: SUCCESS
```

### Check Build Status

Go to:

```text
github-build
→ Build History
```

Verify that Build #1 completed successfully.

### Make a Change in GitHub

Update the `README.md` file.

Example:

```text
Jenkins Basic CI Project
Build and Test
```

If working locally:

```bash
git add README.md
git commit -m "Update Jenkins project"
git push
```

### Run Jenkins Again

Go back to:

```text
Jenkins
→ github-build
→ Build Now
```

Jenkins creates:

```text
Build #2
```

Open:

```text
Build #2
→ Console Output
```

Verify:

```text
Finished: SUCCESS
```

## Outcome

The Jenkins job successfully pulled GitHub code, executed the build, and completed successfully after a repository change.

---

# 🔄 CI Workflow Demonstrated

```text
GitHub Repository
       ↓
Jenkins Job
       ↓
Git Checkout
       ↓
Execute Build
       ↓
Console Output
       ↓
Build SUCCESS
       ↓
GitHub Code Change
       ↓
Jenkins Build #2
       ↓
Build SUCCESS
```

---

# 🛠️ Troubleshooting

## Jenkins Node Offline

If the Jenkins job displays:

```text
Waiting for next available executor
```

check:

```text
Manage Jenkins
→ Nodes
→ Built-In Node
```

Make sure the Built-In Node is **Online** and has available executors.

If the node is offline, use:

```text
Bring this node back online
```

## Git Branch Error

If Jenkins reports:

```text
Couldn't find any revision to build
```

verify the GitHub branch configuration.

For this project:

```text
*/main
```

Make sure the Jenkins branch matches the GitHub repository branch.

## Disk Space Warning

Check disk usage:

```bash
df -h
```

Make sure sufficient disk and temporary space are available for Jenkins operations.

---

# 📸 Screenshots / Output

All screenshots from the practical assignment should be added at the bottom of this README.

## Jenkins Installation

Add screenshots showing:

* Jenkins installation
* Jenkins service status
* Jenkins initial setup

## Jenkins Dashboard

Add a screenshot showing the Jenkins Dashboard after installation.

## Jenkins UI and Configuration

Add screenshots showing:

* Jenkins Dashboard
* Users
* Plugins
* System Configuration

## Jenkins Tools Configuration

Add a screenshot showing:

* JDK
* Git
* Maven
* NodeJS

## Jenkins Credentials

Add a screenshot showing:

```text
github-credentials
```

> Hide passwords, tokens, API keys, and other sensitive information.

## GitHub Repository

Add a screenshot showing:

```text
jenkins-basic-project
```

## Jenkins Job Configuration

Add a screenshot showing:

```text
github-build
```

with:

```text
GitHub Repository
*/main
github-credentials
```

## Jenkins Build #1

Add a screenshot showing the first Jenkins build.

## Jenkins Console Output

Add a screenshot showing the console output ending with:

```text
Finished: SUCCESS
```

## GitHub Repository Change

Add a screenshot showing the updated `README.md`.

## Jenkins Build #2

Add a screenshot showing the second Jenkins build after the GitHub repository change.

## Build #2 Console Output

Add a screenshot showing:

```text
Finished: SUCCESS
```

---

# 📚 Key Learnings

* Jenkins basics
* CI/CD concepts
* Jenkins Controller and Agent architecture
* Jenkins installation
* User management
* Permissions
* Plugin management
* Tool configuration
* Credential management
* GitHub integration
* Freestyle Jenkins jobs
* Build execution
* Console output
* Build status verification

---

# ✅ Overall Outcome

Understood Jenkins basics, CI/CD, architecture, installation, configuration, credentials, GitHub integration, and basic job execution. Successfully created and executed a Jenkins CI job and verified successful builds.

---

# 👨‍💻 Author

**Venu Gopala Reddy Eppala**

**Cloud & DevOps Engineer**

### Skills

`AWS` `Jenkins` `Git` `GitHub` `Docker` `Kubernetes` `Terraform` `CI/CD`

---

# ⭐ Project Status

**Completed Successfully**

```text
GitHub → Jenkins → Build → Console Output → SUCCESS
```

```
```
