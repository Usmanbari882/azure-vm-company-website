# 🚀 CloudNova Solutions — Azure VM Web Deployment

![Azure](https://img.shields.io/badge/Microsoft%20Azure-Cloud-blue)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Linux-orange)
![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green)
![GitHub](https://img.shields.io/badge/GitHub-Version%20Control-black)
![Status](https://img.shields.io/badge/Project-Completed-success)

## 📌 Project Overview

This project demonstrates the deployment of a complete static business website on a Microsoft Azure Virtual Machine.

The website was developed using HTML, CSS, and JavaScript, stored in a GitHub repository, cloned onto an Azure Linux Virtual Machine, and deployed using the Nginx web server.

The website is publicly accessible through the Azure Virtual Machine's Public IP address.

This project represents my first practical Cloud Engineering deployment project and demonstrates the complete workflow from source code management to live website deployment.

---

# 🎯 Project Objectives

The main objectives of this project were:

* Create a Microsoft Azure Virtual Machine
* Deploy Ubuntu Linux on Azure
* Connect to the VM using SSH
* Configure Network Security Group rules
* Allow HTTP traffic on TCP Port 80
* Install and configure Nginx
* Create and manage a website using HTML, CSS, and JavaScript
* Store website source code in GitHub
* Clone a GitHub repository onto an Azure VM
* Deploy website files using Nginx
* Test the website locally using `curl`
* Verify Nginx and Port 80
* Access the website through a Public IP
* Update website code through GitHub
* Pull updated code using `git pull`
* Redeploy updated files to Nginx
* Troubleshoot deployment and connectivity issues

---

# 🏗️ Project Architecture

```text
                         Internet
                            │
                            │ HTTP
                            │ Port 80
                            ▼
                   Azure Public IP
                  130.131.197.190
                            │
                            ▼
              Azure Network Security Group
                   Allow TCP Port 80
                            │
                            ▼
                  Azure Virtual Machine
                       Ubuntu Linux
                            │
                            │
                            ▼
                         Nginx
                    Web Server
                            │
                            ▼
                    /var/www/html
                            │
             ┌──────────────┼──────────────┐
             │              │              │
             ▼              ▼              ▼
         index.html     style.css      script.js
             │              │              │
             └──────────────┼──────────────┘
                            │
                            ▼
                  🌐 Live Website
```

---

# ☁️ Azure Infrastructure

The project was deployed using the following Azure resources:

| Resource         | Configuration           |
| ---------------- | ----------------------- |
| Cloud Platform   | Microsoft Azure         |
| Virtual Machine  | `vm-web-01`             |
| Operating System | Ubuntu Server 24.04 LTS |
| VM Size          | Standard D2plds_v6      |
| vCPUs            | 2                       |
| Memory           | 4 GiB                   |
| Architecture     | ARM64                   |
| Region           | Central US              |
| Authentication   | SSH Public Key          |
| Web Server       | Nginx                   |
| Public IP        | Azure Public IP         |
| HTTP Port        | TCP 80                  |
| Network Security | Azure NSG               |
| Source Code      | GitHub                  |

---

# 💻 Technologies Used

* Microsoft Azure
* Azure Virtual Machines
* Ubuntu Linux
* Nginx
* Git
* GitHub
* HTML5
* CSS3
* JavaScript
* SSH
* Azure Networking
* Network Security Groups
* TCP/IP
* HTTP

---

# 📂 Project Structure

```text
azure-vm-company-website/
│
├── index.html
├── style.css
├── script.js
└── README.md
```

### `index.html`

Contains the main structure and content of the website.

### `style.css`

Contains the website design, layout, responsive styling, navigation, hero section, service cards, and other visual components.

### `script.js`

Provides JavaScript functionality for the website's contact form.

### `README.md`

Contains project documentation, architecture, deployment process, testing, and troubleshooting information.

---

# 🌐 Website Features

The deployed website includes:

* Responsive navigation bar
* Hero section
* Cloud infrastructure services section
* Cloud security services section
* Application deployment services section
* About section
* Project statistics
* Contact form
* Responsive design
* JavaScript form interaction
* Azure deployment information

---

# 🔐 Network Security Group Configuration

To make the website accessible from the Internet, an inbound security rule was configured in the Azure Network Security Group.

```text
Priority: 300
Name: SSH
Port: 22
Protocol: TCP
Source: Any
Destination: Any
Action: Allow
```

HTTP access was also configured:

```text
Priority: 110
Name: Allow-HTTP
Port: 80
Protocol: TCP
Source: Any
Destination: Any
Action: Allow
```

The HTTP rule allows users to access the website using:

```text
http://PUBLIC-IP
```

> SSH access on Port 22 was used for administration and deployment. In a production environment, SSH access should be restricted to trusted IP addresses instead of allowing access from any source.

---

# 🔑 Connecting to the Azure VM

The VM was accessed remotely using SSH.

Example:

```bash
ssh -i vm-web-01-key.pem azureadmin@PUBLIC-IP
```

After successful authentication, the Ubuntu Linux terminal was available:

```text
azureadmin@vm-web-01:~$
```

---

# 🛠️ Nginx Web Server

Nginx was used as the web server for hosting the website.

The default Nginx web root is:

```text
/var/www/html
```

The website files were deployed to this directory.

The Nginx service was verified using:

```bash
sudo systemctl status nginx
```

The expected status was:

```text
Active: active (running)
```

---

# 🧪 Testing

The deployment was tested using multiple methods.

## 1. Check Nginx Service

```bash
sudo systemctl status nginx
```

Result:

```text
Active: active (running)
```

---

## 2. Test Website Locally

```bash
curl http://localhost
```

The command returned the HTML source of the CloudNova Solutions website.

This confirmed that Nginx was successfully serving the website from inside the Azure VM.

---

## 3. Check Port 80

```bash
sudo ss -tulpn | grep :80
```

This confirmed that Nginx was listening for HTTP traffic on Port 80.

---

## 4. Check Website Files

```bash
ls -la /var/www/html
```

The deployed files included:

```text
index.html
style.css
script.js
```

---

## 5. Public Website Test

The website was accessed from a web browser using the Azure VM Public IP:

```text
http://PUBLIC-IP
```

The CloudNova Solutions website successfully loaded in the browser.

---

# 🔄 GitHub Deployment Workflow

The website source code was maintained in GitHub.

The deployment workflow was:

```text
Developer
    │
    ▼
Write Website Code
    │
    ▼
GitHub Repository
    │
    ▼
git clone
    │
    ▼
Azure VM
    │
    ▼
Nginx Web Root
    │
    ▼
Public IP
    │
    ▼
Live Website
```

---

# 📥 Clone Project on Azure VM

The GitHub repository was cloned using:

```bash
git clone https://github.com/Usmanbari882/azure-vm-company-website.git
```

The project directory was accessed using:

```bash
cd azure-vm-company-website
```

The project files were verified using:

```bash
ls
```

Expected files:

```text
README.md
index.html
script.js
style.css
```

---

# 🚀 Deploy Website to Nginx

The website files were copied to the Nginx web root:

```bash
sudo cp -r ./* /var/www/html/
```

The deployed files were verified using:

```bash
ls -la /var/www/html
```

---

# 🔄 Updating the Live Website

One of the most important practical tasks in this project was updating the live website through GitHub.

The workflow was:

```text
Update Code
    ↓
Commit Changes
    ↓
Push to GitHub
    ↓
Azure VM
    ↓
git pull
    ↓
Copy Updated Files
    ↓
Nginx
    ↓
Updated Live Website
```

The latest changes were downloaded from GitHub using:

```bash
git pull
```

After pulling the latest code, the updated files were deployed to Nginx:

```bash
sudo cp -r ./* /var/www/html/
```

The website was then refreshed in the browser to verify the changes.

---

# 🐛 Troubleshooting

During the deployment process, website connectivity was tested and troubleshooting was performed.

Common troubleshooting checks included:

### Check Nginx

```bash
sudo systemctl status nginx
```

### Check Local Website

```bash
curl http://localhost
```

### Check Port 80

```bash
sudo ss -tulpn | grep :80
```

### Check Website Files

```bash
ls -la /var/www/html
```

### Check Azure NSG

Verify that TCP Port 80 is allowed in the Network Security Group.

### Check Public IP

Verify that the correct Azure VM Public IP is being used in the browser.

---

# 📊 Deployment Verification

The deployment was considered successful when:

* [x] Azure VM created
* [x] Ubuntu Linux running
* [x] SSH connection successful
* [x] Nginx installed
* [x] Nginx service running
* [x] Git installed
* [x] GitHub repository cloned
* [x] Website files deployed
* [x] Port 80 configured
* [x] NSG HTTP rule configured
* [x] Website accessible using Public IP
* [x] Website tested using `curl`
* [x] GitHub code update tested
* [x] `git pull` tested
* [x] Updated website successfully redeployed

---

# 🎓 Key Learning Outcomes

Through this project, I gained practical experience with:

* Azure Virtual Machines
* Linux server management
* SSH remote administration
* Git and GitHub
* Nginx web server
* Website deployment
* Azure Network Security Groups
* HTTP Port 80
* Public IP networking
* Linux file management
* Cloud troubleshooting
* Source code deployment
* Updating live applications
* Basic cloud infrastructure architecture

---

# 🌍 Real-World Scenario

In a real-world company environment, a developer may create and update application code and push it to a Git repository.

A Cloud Engineer or DevOps Engineer may then:

1. Provision cloud infrastructure.
2. Configure Linux servers.
3. Configure networking and security.
4. Install required services.
5. Deploy application code.
6. Monitor the application.
7. Troubleshoot infrastructure issues.
8. Deploy new application versions.

This project demonstrates a simplified version of that real-world workflow.

---

# 🔮 Future Improvements

Future improvements for this project may include:

* HTTPS with SSL/TLS
* Custom domain name
* Azure DNS
* Automated deployment using Ansible
* CI/CD pipeline using GitHub Actions
* Docker containerization
* Azure Load Balancer
* Azure Monitor
* Application monitoring
* Automated infrastructure provisioning with Terraform
* Infrastructure as Code
* Production-grade security
* Restricting SSH access to trusted IP addresses

---

# 🏆 Project Status

**Status: ✅ Completed**

This project successfully demonstrates the deployment of a complete static website on Microsoft Azure using an Ubuntu Linux Virtual Machine and Nginx.

The website source code is maintained in GitHub and can be updated and redeployed to the Azure VM.

---

# 👨‍💻 Author

**Usman Bari**

Aspiring Cloud Engineer

Focused on:

* Microsoft Azure
* Cloud Computing
* Linux
* Infrastructure Automation
* Ansible
* Docker
* Kubernetes
* Terraform
* CI/CD

---

# ⭐ Final Project Summary

This project represents my first practical Cloud Engineering deployment.

I successfully built a website using HTML, CSS, and JavaScript, stored the source code in GitHub, deployed it to an Ubuntu Linux Virtual Machine running on Microsoft Azure, configured Nginx as the web server, allowed HTTP traffic through Azure Network Security Group rules, and exposed the application through a public IP address.

I also practiced updating the website source code in GitHub, pulling the latest changes onto the Azure VM, and redeploying the updated files to Nginx.

### Final Architecture

```text
GitHub
   │
   │ Source Code
   ▼
Azure VM
   │
   ├── Ubuntu Linux
   │
   ├── Nginx
   │
   └── /var/www/html
           │
           ▼
    Azure NSG — Port 80
           │
           ▼
      Public IP
           │
           ▼
    🌐 Live Website
```

> **Learn → Build → Deploy → Test → Troubleshoot → Update → Document**

