


# Rishabh Kandhari's Professional Portfolio Website

🌐 **LIVE WEBSITE:** [https://rishabhkandhari14.com](https://rishabhkandhari14.com) **← CLICK TO VIEW DEPLOYED SITE**

📋 **ICT 171 Assignment 2 - Complete Server Deployment & Automation Documentation**  
🎓 **Student:** Rishabh Kandhari | **ID:** 35118707

---
## 📖 Project Overview

**AWS Infrastructure:** EC2 IP Address: `54.66.64.231`  
**Custom Domain:** [https://rishabhkandhari14.com](https://rishabhkandhari14.com)  
**GitHub Repository:** [Website_Kandhari](https://github.com/KandhariRishabh14/Website_Kandhari)

This comprehensive project showcases the complete end-to-end deployment of a professional portfolio website on Amazon Web Services (AWS) EC2 infrastructure. The implementation goes beyond basic web hosting to include enterprise-level features such as automated backup systems, continuous integration workflows, real-time monitoring, and robust security configurations.

### 🎯 What Makes This Project Special:

**Professional Infrastructure:** Built on AWS EC2 with Ubuntu, featuring industry-standard Nginx web server configuration, custom domain integration, and enterprise-grade SSL security through Let's Encrypt certificates.

**Advanced Automation:** Three sophisticated bash scripts provide automated website backups, continuous GitHub synchronization, and system maintenance - all with real-time Slack notifications for monitoring and alerting.

**Real-World Application:** This isn't just a school project - it's a production-ready website with professional contact forms, resume downloads, and responsive design that could serve as an actual portfolio for job applications.

**DevOps Integration:** Implements core DevOps principles including Infrastructure as Code documentation, automated deployments, monitoring, and disaster recovery procedures.
---

## 📅 Development Timeline (May 19-30, 2025)

### Phase 1: Frontend Development (May 19-25)
- **May 19-20:** Project planning, repository setup, and initial HTML structure
- **May 21-22:** Professional CSS framework implementation and responsive design
- **May 23-24:** JavaScript functionality and Email.js contact form integration
- **May 25:** Frontend testing and user experience optimization

### Phase 2: Infrastructure & Automation (May 26-30)
- **May 26:** AWS EC2 deployment and security configuration
- **May 27:** Nginx setup, SSL implementation, and domain configuration
- **May 28-29:** Automation scripts development and Slack integration
- **May 30:** Final testing, documentation, and production deployment

---

## ✅ Checklist

**Core Infrastructure Requirements:**
- [x] ☁️ AWS EC2 (Ubuntu) instance with professional security groups
- [x] 🔐 SSH access configuration with proper key management
- [x] 📦 Nginx web server installation and configuration
- [x] 🔧 Git version control and Certbot SSL management setup

**Website Deployment & Integration:**
- [x] 📁 GitHub repository cloning to production server
- [x] ⚙️ Nginx virtual host configuration for website serving
- [x] 🌐 AWS Route 53 DNS management with A records and CNAME setup
- [x] 🔒 Let's Encrypt SSL certificate with automated renewal

**Advanced Features & Automation:**
- [x] 📱 Email.js integration for functional contact form
- [x] 🎨 Responsive design with JavaScript interactivity
- [x] 🤖 Three comprehensive Linux automation scripts
- [x] 📊 Real-time Slack monitoring and alerting system

---

## 🚀 Technical Implementation Guide

### Prerequisites & Requirements

**Essential Services & Accounts:**
- AWS Account with EC2 and Route 53 billing enabled
- GitHub account for version control and repository hosting
- Custom domain name registered through AWS Route 53
- Slack workspace for automation monitoring and alerts
- Local development environment with terminal access

**Technical Knowledge Base:**
- Linux command line operations and Ubuntu administration
- Basic web technologies (HTML, CSS, JavaScript)
- Git version control workflows and best practices
- DNS concepts and domain management fundamentals
- Server administration and security principles

---

## 📋 Complete Step-by-Step Implementation

### 1. 📂 GitHub Repository Setup - Version Control Foundation

**Professional Repository Configuration:**

1. **Create New Repository:**
   - Navigate to [GitHub](https://github.com) and click "New Repository"
   - Name: `Website_Kandhari` (professional naming convention)
   - Visibility: Public (required for assignment demonstration)
   - Initialize with README.md for proper documentation

2. **Upload Complete Website Assets:**
   - `index.html` - Main website with semantic HTML structure
   - Embedded CSS for responsive design and professional styling
   - JavaScript for interactive functionality and Email.js integration
   - Image assets optimized for web performance
   - PDF resume for professional download functionality

**Technical Decision:** Single-file HTML approach chosen for easier server deployment and nano editor management within EC2 terminal environment.

### 2. ☁️ AWS EC2 Instance Configuration - Professional Cloud Infrastructure

#### Strategic Instance Selection:
Instance Type: t3.small (Enhanced performance over free tier)
AMI: Ubuntu 22.04 LTS (Long-term support for stability)
Storage: 30GB gp3 SSD (High performance, sufficient capacity)

#### Production Security Group Configuration:
Inbound Rules:
├── SSH (Port 22) ← My IP Only (Enhanced security)
├── HTTP (Port 80) ← 0.0.0.0/0 (Public web access)
└── HTTPS (Port 443) ← 0.0.0.0/0 (Secure web access)
Security Principles Applied:

Principle of least privilege (SSH restricted)
Defense in depth (Multiple security layers)
Fail-safe defaults (Only required ports open)


#### Elastic IP Assignment:
- **Allocated IP:** `54.66.64.231`
- **Purpose:** Static IP for DNS configuration and consistent access
- **Associated:** Linked to running EC2 instance for permanent assignment

### 3. 🔐 Secure SSH Access Configuration

#### Windows PowerShell Method:
```powershell
# Set restrictive permissions (equivalent to chmod 400)
icacls .\website.pem /inheritance:r /grant:r "${env:USERNAME}:(R)"

# Establish secure connection
ssh -i "website.pem" ubuntu@54.66.64.231
Linux/Mac Method:
bash# Set proper key permissions
chmod 400 website.pem

# Connect to server
ssh -i "website.pem" ubuntu@54.66.64.231
4. 📦 Server Software Installation - Production Environment Setup
bash# System update and security patches
sudo apt update && sudo apt upgrade -y

# Install core web server components
sudo apt install nginx git -y

# Install SSL certificate management
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
5. 📁 Website Deployment - GitHub Integration
bash# Navigate to web root directory
cd /var/www

# Clone repository to production location
sudo git clone https://github.com/KandhariRishabh14/Website_Kandhari.git portfolio

# Verify deployment
ls -la /var/www/portfolio
6. ⚙️ Nginx Web Server Configuration
Remove Default Configuration:
bashsudo rm /etc/nginx/sites-enabled/default
Create Production Virtual Host:
bashsudo nano /etc/nginx/sites-available/portfolio
Virtual Host Configuration:
nginxserver {
    listen 80;
    server_name rishabhkandhari14.com www.rishabhkandhari14.com;
    
    root /var/www/portfolio;
    index index.html index.htm;
    
    location / {
        try_files $uri $uri/ =404;
    }
    

Enable and Test Configuration:
bashsudo ln -s /etc/nginx/sites-available/portfolio /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
7. 🌐 DNS Configuration with Route 53
Domain Registration Process:

Access AWS Route 53 console
Register custom domain: rishabhkandhari14.com
Complete email validation within 15-day window
Create public hosted zone for domain management

DNS Records Configuration:
A Record (Root Domain):
- Name: @ (empty)
- Type: A
- Value: 54.66.64.231
- TTL: 300

A Record (WWW Subdomain):
- Name: www
- Type: A
- Value: 54.66.64.231
- TTL: 300

CNAME Record (WWW Alias):
- Name: www
- Type: CNAME
- Value: rishabhkandhari14.com
- TTL: 300
DNS Propagation Verification:

Testing Tool: DNS Checker
Propagation Time: 1-5 minutes globally
Verification: All global DNS servers showing correct resolution

8. 🔒 SSL Certificate Implementation - Enterprise Security
Automated SSL Certificate Installation:
bashsudo certbot --nginx -d rishabhkandhari14.com -d www.rishabhkandhari14.com
Automatic Renewal Configuration:
bash# Test renewal process
sudo certbot renew --dry-run

# Verify renewal timer
sudo systemctl status certbot.timer
SSL Security Verification:

Testing Service: SSL Labs
Security Rating: A+ (Perfect score)
Certificate Authority: Let's Encrypt
Encryption: TLS 1.3 with modern cipher suites
```powershell

```


