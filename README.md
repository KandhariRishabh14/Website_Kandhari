


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
```
### 4. 📦 Server Software Installation - Production Environment Setup
# System update and security patches
```powershell
sudo apt update && sudo apt upgrade -y
```
## Install core web server components
```powershell
sudo apt install nginx git -y
```
## Install SSL certificate management
```powershell
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
### 5. 📁 Website Deployment - GitHub Integration
bash# Navigate to web root directory
```powershell
cd /var/www
```
# Clone repository to production location

sudo git clone https://github.com/KandhariRishabh14/Website_Kandhari.git portfolio

# Verify deployment
ls -la /var/www/portfolio
### 6. ⚙️ Nginx Web Server Configuration
Remove Default Configuration:
```powershell
sudo rm /etc/nginx/sites-enabled/default
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
```    

## Enable and Test Configuration:
```powershell
 ln -s /etc/nginx/sites-available/portfolio /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```
### 7. 🌐 DNS Configuration with Route 53
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

## 8. 🔒 SSL Certificate Implementation - Enterprise Security
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
```
## 🤖 Advanced Linux Automation Scripts

### Script Architecture Overview:

**Professional DevOps Implementation:** Three production-ready automation scripts providing comprehensive server management, continuous deployment, and disaster recovery capabilities with real-time monitoring integration.

### 1. 📦 Automated Backup System

**Business Purpose:** Provides automated daily backups with compression, timestamping, and immediate notification of success or failure to prevent catastrophic data loss.

**Script Location:** `/home/ubuntu/website_backup.sh`

```bash
#!/bin/bash

# Professional Configuration Management
BACKUP_DIR="/home/ubuntu/backups"
WEBSITE_DIR="/var/www/portfolio"
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_FILE="website_backup_$DATE.tar.gz"
SLACK_WEBHOOK="https://hooks.slack.com/services/YOUR/BACKUP/WEBHOOK"

# Create backup directory structure
mkdir -p $BACKUP_DIR

# Create compressed backup with error handling
tar -czf "$BACKUP_DIR/$BACKUP_FILE" -C "$WEBSITE_DIR" .

# Verify backup success and notify
if [ $? -eq 0 ]; then
    FILE_SIZE=$(du -h "$BACKUP_DIR/$BACKUP_FILE" | cut -f1)
    MESSAGE="✅ Website backup completed successfully: $BACKUP_FILE (Size: $FILE_SIZE)"
else
    MESSAGE="❌ Website backup failed! Immediate attention required."
fi

# Send Slack notification
curl -X POST -H 'Content-type: application/json' \
    --data "{\"text\":\"$MESSAGE\"}" \
    $SLACK_WEBHOOK
```
```bash
echo $MESSAGE
Scheduling Configuration:
bash# Crontab entry for daily backups at 1:08 AM
8 1 * * * /home/ubuntu/website_backup.sh
```
## 2. 🔄 Continuous Integration & Deployment Pipeline
Business Purpose: Implements automated continuous deployment by pulling latest GitHub changes every 5 minutes, enabling rapid feature deployment with zero-downtime updates.
Script Location: /home/ubuntu/github_auto_pull.sh
bash#!/bin/bash

# CI/CD Configuration
```bash
WEBSITE_DIR="/var/www/portfolio"
SLACK_WEBHOOK="https://hooks.slack.com/services/YOUR/GITHUB/WEBHOOK"

# Navigate to production directory
cd $WEBSITE_DIR

# Pull latest changes from repository
git pull origin main

# Check deployment success and apply changes
if [ $? -eq 0 ]; then
    # Successful deployment - reload web server
    sudo systemctl reload nginx
    MESSAGE="🚀 GitHub auto-update completed successfully - Website updated!"
else
    MESSAGE="❌ GitHub auto-update failed! Deployment requires manual intervention."
fi

# Send deployment notification
curl -X POST -H 'Content-type: application/json' \
    --data "{\"text\":\"$MESSAGE\"}" \
    $SLACK_WEBHOOK

echo $MESSAGE
High-Frequency Deployment Schedule:
bash# Crontab entry for continuous integration every 5 minutes
*/5 * * * * /home/ubuntu/github_auto_pull.sh
```
3. 🔧 Proactive System Maintenance & Security Management
Business Purpose: Automated system updates with intelligent reboot management, ensuring server security and stability while minimizing downtime through scheduled maintenance windows.
Script Location: /home/ubuntu/auto_update.sh
bash#!/bin/bash

# System Maintenance Configuration
SLACK_WEBHOOK="https://hooks.slack.com/services/YOUR/SYSTEM/WEBHOOK"

# Update package database
sudo apt update

# Check for available system updates
UPDATES=$(apt list --upgradable 2>/dev/null | wc -l)

if [ $UPDATES -gt 1 ]; then
    # Execute system updates
    sudo apt upgrade -y
    
    # Check if critical updates require reboot
    if [ -f /var/run/reboot-required ]; then
        MESSAGE="🔄 Critical system updates completed. Server rebooting for security patches."
        curl -X POST -H 'Content-type: application/json' \
            --data "{\"text\":\"$MESSAGE\"}" \
            $SLACK_WEBHOOK
        sudo reboot
    else
        MESSAGE="✅ System updates completed successfully - No reboot required."
    fi
else
    MESSAGE="✅ System is up to date - No maintenance required."
fi

# Send maintenance notification
curl -X POST -H 'Content-type: application/json' \
    --data "{\"text\":\"$MESSAGE\"}" \
    $SLACK_WEBHOOK
```
echo $MESSAGE
Strategic Maintenance Scheduling:
bash# Crontab entry for daily maintenance at 2:40 PM
40 14 * * * /home/ubuntu/auto_update.sh
```
### Script Installation & Configuration:
1. Create Script Files:
bashsudo nano /home/ubuntu/website_backup.sh
sudo nano /home/ubuntu/github_auto_pull.sh
sudo nano /home/ubuntu/auto_update.sh
2. Set Executable Permissions:
bashsudo chmod +x /home/ubuntu/website_backup.sh
sudo chmod +x /home/ubuntu/github_auto_pull.sh
sudo chmod +x /home/ubuntu/auto_update.sh
3. Configure Automated Scheduling:
bashcrontab -e

# Add all three automation schedules:
8 1 * * * /home/ubuntu/website_backup.sh
*/5 * * * * /home/ubuntu/github_auto_pull.sh
40 14 * * * /home/ubuntu/auto_update.sh
4. Verify Active Schedules:
bashcrontab -l

📱 Professional Slack Integration & Monitoring
Enterprise Monitoring Architecture:
Multi-Channel Strategy: Dedicated Slack channels for different automation types provide specialized alerting, noise reduction, and comprehensive audit trails for team collaboration.
Slack Webhook Configuration Process:

Access Slack API Console: https://api.slack.com/apps
Create Professional Application:

Click "Create New App" → "From scratch"
Name: "Portfolio-Server-Monitor" (descriptive naming)
Select appropriate workspace


Configure Incoming Webhooks:

Navigate to "Incoming Webhooks" in sidebar
Activate incoming webhooks (toggle to "On")
Create unique webhook for each service


Recommended Channel Structure:

#backup-alerts - Daily backup status and storage management

Successful backup confirmations with file sizes
Immediate failure alerts requiring attention
Storage usage monitoring and cleanup notifications

#deployment-updates - Continuous integration notifications

Real-time deployment confirmations with commit details
Failed deployment alerts with error context
Repository synchronization status updates

#system-maintenance - Server health and security updates

Security update installations and completion status
System reboot notifications with expected downtime
Critical system alerts requiring immediate response

Advanced Notification Examples:
Enhanced Backup Notifications:
bash# Rich system context in notifications
HOSTNAME=$(hostname)
DISK_USAGE=$(df -h /var/www | tail -1 | awk '{print $5}')
MESSAGE="🛡️ Backup Report for $HOSTNAME
✅ Status: Completed Successfully
📁 File: $BACKUP_FILE (Size: $FILE_SIZE)
🕐 Timestamp: $(date '+%Y-%m-%d %H:%M:%S %Z')"

🛠️ Comprehensive Troubleshooting Guide
Professional System Administration Methodology:
Diagnostic Approach: Systematic problem identification, variable isolation, hypothesis testing, and solution implementation with proper documentation.
1. 🤖 Cron Job Automation Diagnostics
Symptom: Scripts execute manually but fail during scheduled cron execution.
Diagnostic Process:
Step 1: Verify Cron Configuration
bash# Display active cron jobs
crontab -l

# Expected output:
# 8 1 * * * /home/ubuntu/website_backup.sh
# */5 * * * * /home/ubuntu/github_auto_pull.sh
# 40 14 * * * /home/ubuntu/auto_update.sh
Step 2: Permission Analysis
bash# Check file permissions
ls -la /home/ubuntu/*.sh

# Correct permissions should show:
# -rwxr-xr-x (executable for all)
Step 3: Execution Logging
bash# Monitor cron execution
grep CRON /var/log/syslog | tail -n 10

# Expected successful output:
# CRON[PID]: (ubuntu) CMD (/home/ubuntu/script-name.sh)
Resolution:
bash# Fix permissions definitively
sudo chmod +x /home/ubuntu/*.sh
sudo chown ubuntu:ubuntu /home/ubuntu/*.sh
2. 🔐 SSH Authentication Management
Windows PowerShell Solution:
powershell# Correct permission management for Windows
icacls website.pem /inheritance:r /grant:r "$($env:USERNAME):(R)"

# Verify connection
ssh -i "website.pem" ubuntu@54.66.64.231
Advanced SSH Debugging:
bash# Verbose connection testing
ssh -vvv -i "website.pem" ubuntu@54.66.64.231

# Test server accessibility
nmap -p 22 54.66.64.231
3. ⚙️ Nginx Web Server Diagnostics
Configuration Validation:
bash# Test configuration syntax
sudo nginx -t

# Monitor real-time errors
sudo tail -f /var/log/nginx/error.log

# Verify service status
sudo systemctl status nginx
Performance Monitoring:
bash# Check listening ports
sudo netstat -tlnp | grep nginx

# Test local connectivity
curl -I http://localhost
curl -I https://rishabhkandhari14.com
4. 🔒 SSL Certificate Management
Certificate Health Monitoring:
bash# Check certificate status
sudo certbot certificates

# Test renewal process
sudo certbot renew --dry-run

# Manual renewal if needed
sudo certbot renew --nginx
5. 📊 System Performance Monitoring
Comprehensive Health Checks:
bash# Resource monitoring
htop
free -h
df -h

# Network connectivity
ping -c 4 google.com
curl -I https://github.com

# Service status
sudo systemctl --failed
Emergency Response Procedures:
Website Down (502/503 Errors):

sudo systemctl status nginx
sudo systemctl restart nginx
Check logs: sudo tail -n 50 /var/log/nginx/error.log

SSL Certificate Issues:

sudo certbot renew --nginx
sudo certbot certificates
Test: curl -I https://rishabhkandhari14.com

Script Failures:

Manual test: /home/ubuntu/script-name.sh
Check permissions: ls -la /home/ubuntu/*.sh
Review logs: grep CRON /var/log/syslog


✨ Advanced Features & Professional Enhancements
Modern Web Development Implementation:
Email.js Integration: Professional contact form functionality without backend server requirements, enabling real-time communication with website visitors through automated email forwarding.
Responsive Design Framework: Mobile-first CSS Grid and Flexbox implementation ensuring optimal user experience across all device types and screen sizes.
JavaScript Interactivity: Dynamic content loading, smooth scroll animations, form validation, and interactive user interface elements providing professional user experience.
Performance Optimization: Optimized image assets, efficient CSS/JavaScript execution, and fast server response times achieving excellent performance metrics.
Enterprise Architecture Features:
Security Implementation:

HTTPS-only access with perfect SSL Labs A+ rating
Security headers preventing XSS and clickjacking attacks
Content Security Policy implementation
Automated security updates through custom maintenance scripts

Business Functionality:

Professional portfolio showcase with project demonstrations
Functional contact form with Email.js service integration
Resume download capability for potential employers
Social media integration and professional networking links

Scalability & Maintenance:

Modular design enabling easy feature additions
SEO optimization with semantic HTML and meta tags
Analytics integration for user behavior tracking
Comprehensive logging and monitoring systems
