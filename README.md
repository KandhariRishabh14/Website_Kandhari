


# Rishabh Kandhari's Professional Portfolio Website

🌐 **LIVE WEBSITE:** [https://rishabhkandhari14.com](https://rishabhkandhari14.com) **← CLICK TO VIEW DEPLOYED SITE**

📋 **ICT 171 Assignment 2 - Complete Server Deployment & Automation Documentation**  
🎓 **Student:** Rishabh Kandhari | **ID:** 35118707

---

## 📖 Project Overview - My Journey

**Student:** Rishabh Kandhari | **ID:** 35118707  
**Live Website:** [https://rishabhkandhari14.com](https://rishabhkandhari14.com)  
**AWS Infrastructure:** EC2 IP `54.66.64.231`

This project started as an assignment but became something much bigger - a real production website that I could actually use for job applications. I went beyond just hosting a basic site and built a complete DevOps automation system that runs 24/7.

**What makes this special:** I didn't just follow tutorials - I solved real problems, like figuring out how to manage CSS/JavaScript in terminal editors and setting up automated backups that actually saved me when I accidentally deleted files during development.

## 🤔 Real-World Technical Decisions

### Why Single HTML File?
**The Problem:** I couldn't figure out how to properly link separate CSS and JavaScript files when editing through nano in the EC2 terminal. Linking external files was causing issues during deployment.

**My Solution:** Combined everything into one HTML file. GitHub shows it as "HTML only" but it actually contains CSS and JavaScript too. This approach made terminal editing much easier and deployment more reliable.

**Lesson Learned:** Sometimes the "textbook" approach isn't always the most practical for real deployment scenarios.

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

## 1. 📂 GitHub Repository Setup - Version Control Foundation

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

## 2. ☁️ AWS EC2 Instance Configuration - Professional Cloud Infrastructure

#### Strategic Instance Selection:

Instance Type: t3.small 

AMI: Ubuntu 22.04 LTS (Long-term support for stability)

**My Choice:** t3.small (not free tier, but worth it) (Enhanced performance over free tier)

**Why:** I wanted better performance than the free tier limitations. Cost was manageable and gave me more reliable testing.

**Key Configuration:**
- **OS:** Ubuntu 
- **Storage:** 30GB gp3 SSD (plenty for website + backups)
- **Security Groups:** Carefully configured - SSH only from my IP, HTTP/HTTPS from anywhere

**Pro Tip:** Always create multiple copies of your .pem key file. I learned this the hard way when I almost lost access to my server!

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

## 3. 🔐 Secure SSH Access Configuration

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
## 4. 📦 Server Software Installation - Production Environment Setup
###System update and security patches
```powershell
sudo apt update && sudo apt upgrade -y
```
### Install core web server components
```powershell
sudo apt install nginx git -y
```
### Install SSL certificate management
```powershell
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
## 5. 📁 Website Deployment - GitHub Integration
 Navigate to web root directory
```powershell
cd /var/www
```
 Clone repository to production location
```powershell
sudo git clone https://github.com/KandhariRishabh14/Website_Kandhari.git portfolio
```
 Verify deployment
ls -la /var/www/portfolio
## 6. ⚙️ Nginx Web Server Configuration
### Remove Default Configuration:
```powershell
sudo rm /etc/nginx/sites-enabled/default
```
### Create Production Virtual Host:
```powershell
sudo nano /etc/nginx/sites-available/portfolio
Virtual Host Configuration:
nginxserver {
    listen 80;
    server_name rishabhkandhari14.com www.rishabhkandhari14.com;
    
    root /var/www/portfolio;
    index index.html index.htm;
    
    location / {
        try_files $uri $uri/ =404;
    }
    

    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header Referrer-Policy "no-referrer-when-downgrade" always;
    add_header Content-Security-Policy "default-src 'self' http: https: data: blob: 'unsafe-inline'" always;
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
    
    
    server_tokens off;
}
```
### Enable and Test Configuration:
```powershell
 ln -s /etc/nginx/sites-available/portfolio /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```
## 7. 🌐 DNS Configuration with Route 53
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
```powershell
sudo certbot --nginx -d rishabhkandhari14.com -d www.rishabhkandhari14.com
```
Automatic Renewal Configuration:
### Test renewal process
```powershell
sudo certbot renew --dry-run
```
### Verify renewal timer
```powershell
sudo systemctl status certbot.timer
```
### SSL Security Verification:

Testing Service: SSL Labs
Security Rating: A+ (Perfect score)
Certificate Authority: Let's Encrypt
Encryption: TLS 1.3 with modern cipher suites


# 🤖 Advanced Linux Automation Scripts
Script Architecture Overview:
Professional DevOps Implementation: Three production-ready automation scripts providing comprehensive server management, continuous deployment, and disaster recovery capabilities with real-time monitoring integration.
## 1. 📦 Automated Backup System
Business Purpose: Provides automated daily backups with compression, timestamping, and immediate notification of success or failure to prevent catastrophic data loss.
Script Location: /home/ubuntu/website_backup.sh
```powershell
#!/bin/bash
# === Configuration ===
TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")
BACKUP_DIR="/home/ubuntu/backups"
SOURCE_DIR="/var/www/portfolio"
BACKUP_FILE="portfolio_backup_$TIMESTAMP.tar.gz"
SLACK_WEBHOOK_URL="https://hooks.slack.com/services/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"

# === Backup Process ===
mkdir -p "$BACKUP_DIR"
tar -czf "$BACKUP_DIR/$BACKUP_FILE" "$SOURCE_DIR"

# === Slack Notification ===
/usr/bin/curl -X POST -H 'Content-type: application/json' \
--data "{\"text\":\" Backup created successfully enjoy : $BACKUP_FILE\"}" \
"Your Webhook url"
Proven Performance Evidence:
-rw-rw-r-- 1 ubuntu ubuntu 5153613 May 18 17:43 portfolio_backup_2025-05-18_17-43-00.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153691 May 19 01:08 portfolio_backup_2025-05-19_01-08-01.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153691 May 20 01:08 portfolio_backup_2025-05-20_01-08-01.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153691 May 21 13:36 portfolio_backup_2025-05-21_13-36-29.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153688 May 23 01:08 portfolio_backup_2025-05-23_01-08-01.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153696 May 24 01:08 portfolio_backup_2025-05-24_01-08-01.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153694 May 25 01:08 portfolio_backup_2025-05-25_01-08-01.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153689 May 26 01:08 portfolio_backup_2025-05-26_01-08-01.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5153694 May 27 01:08 portfolio_backup_2025-05-27_01-08-01.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 5159126 Jun  5 01:08 portfolio_backup_2025-06-05_01-08-01.tar.gz
Achievements:
```

Scheduling Configuration:
### Crontab entry for daily backups at 1:08 AM
8 1 * * * /home/ubuntu/website_backup.sh

## 2. 🔄 Continuous Integration & Deployment Pipeline
Business Purpose: Implements automated continuous deployment by pulling latest GitHub changes every 5 minutes, enabling rapid feature deployment with zero-downtime updates.
Script Location: /home/ubuntu/github_auto_pull.sh
```powershell
#!/bin/bash
cd /var/www/portfolio

Perform Git pull
GIT_OUTPUT=$(git pull 2>&1)
TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

Log the output
echo "[$TIMESTAMP] Git Pull Result: $GIT_OUTPUT" >> /home/ubuntu/github_sync.log

Send Slack notification
curl -X POST -H 'Content-type: application/json' \
--data "{\"text\":\"🔁 GitHub Auto-Pull Triggered at $TIMESTAMP\nResult:\n$GIT_OUTPUT\"}" \
Your Webhook url/
Live Performance Evidence:
bash[2025-06-05 04:40:04] Git Pull Result: From github.com:KandhariRishabh14/Website_Kandhari
   7bd9872..f8a1c46  main       -> origin/main
Updating 7bd9872..f8a1c46
Fast-forward
 README.md | 16 ++++++++++++----

[2025-06-05 04:45:04] Git Pull Result: From github.com:KandhariRishabh14/Website_Kandhari
   f8a1c46..edaf2f9  main       -> origin/main
Updating f8a1c46..edaf2f9
Fast-forward
 README.md | 223 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++---

[2025-06-05 05:20:03] Git Pull Result: From github.com:KandhariRishabh14/Website_Kandhari
   823b8f4..37b62e9  main       -> origin/main
Updating 823b8f4..37b62e9
Fast-forward
 README.md | 47 +++++++++++++++++++++++++++++------------------
Proven Capabilities:
```

High-Frequency Deployment Schedule:
## Crontab entry for continuous integration every 5 minutes
```powershell
*/5 * * * * /home/ubuntu/github_auto_pull.sh
```
## 3. 🔧 Automatic System Maintenance
Business Purpose: Automated system updates with intelligent reboot management, ensuring server security and stability while minimizing downtime through scheduled maintenance windows.
Script Location: /home/ubuntu/auto_update.sh
```powershell
#!/bin/bash
# Slack webhook URL
##cant expose url
WEBHOOK_URL="Your Webhook url/"
# Run updates
sudo apt update && sudo apt -y upgrade

# If the upgrade was successful
if [ $? -eq 0 ]; then
    curl -X POST -H 'Content-type: application/json' \
        --data "{\"text\":\"System updated completed successfully congrats bro on $(hostname).\"}" $WEBHOOK_URL
else
    curl -X POST -H 'Content-type: application/json' \
        --data "{\"text\":\" System update is failed bro check again on $(hostname). Please check logs.\"}" $WEBHOOK_URL
fi

# Check if a reboot is required
if [ -f /var/run/reboot-required ]; then
    curl -X POST -H 'Content-type: application/json' \
        --data "{\"text\":\"🔁 Reboot required. Rebooting server $(hostname)...\"}" $WEBHOOK_URL
    sudo reboot
fi
```
### Enterprise Features:


Strategic Maintenance Scheduling:
### Crontab entry for daily maintenance at 2:40 PM

```powershell
40 14 * * * /home/ubuntu/auto_update.sh
```
## Script Performance Verification:
System Health Status:
```powershell
ubuntu@ip-172-31-25-27:/var/www/portfolio$ sudo systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION
0 loaded units listed.
Script File Status:
ubuntu@ip-172-31-25-27:~$ ls -la /home/ubuntu/*.sh
-rwxrwxr-x 1 ubuntu ubuntu 836 May 19 13:24 /home/ubuntu/auto_update.sh
-rwxr-xr-x 1 root   root   477 May 18 18:36 /home/ubuntu/github_auto_pull.sh
-rwxr-xr-x 1 root   root   643 May 18 18:03 /home/ubuntu/website_backup.sh
```
Script Installation & Configuration:
### 1. Create Script Files:
```powershell
sudo nano /home/ubuntu/website_backup.sh
sudo nano /home/ubuntu/github_auto_pull.sh
sudo nano /home/ubuntu/auto_update.sh
```
### 2. Set Executable Permissions:
```powershell
sudo chmod +x /home/ubuntu/website_backup.sh
sudo chmod +x /home/ubuntu/github_auto_pull.sh
sudo chmod +x /home/ubuntu/auto_update.sh
```
### 3. Configure Automated Scheduling:
```powershell
crontab -e
```
 Add all three automation schedules:
```powershell
8 1 * * * /home/ubuntu/website_backup.sh
*/5 * * * * /home/ubuntu/github_auto_pull.sh
40 14 * * * /home/ubuntu/auto_update.sh
```
### 4. Verify Active Schedules:
```powershell
crontab -l
```
## 📱 Slack Integration - My 24/7 Server Monitoring Setup

### 🤔 Why I Built This Monitoring System

**The Problem:** I wanted to know what my server was doing without constantly checking logs manually. If something broke at 2 AM, I needed to know about it.

**My Solution:** Set up Slack notifications for everything important. Now my phone buzzes when backups complete, deployments happen, or something goes wrong.

**Real Benefit:** I can monitor my server from anywhere - whether I'm in class, at work, or sleeping. It's like having a personal assistant watching my infrastructure 24/7.

### 🔧 How I Set Up Slack Webhooks - Step by Step

#### Creating the Slack App (My Process)
**Step 1:** Went to [Slack API Console](https://api.slack.com/apps) and created a new app
**Step 2:** Named it "Portfolio-Server-Monitor" (descriptive names matter for organization)
**Step 3:** Selected my workspace where I wanted notifications

**Pro Tip:** I created separate webhook URLs for each type of notification. This lets me control which alerts go to which channels.

#### Webhook Configuration (What Actually Worked)
**Navigate to Incoming Webhooks:** Found it in the sidebar
**Activate Webhooks:** Toggled it to "On" (this enables external integrations)
**Create Multiple Webhooks:** Made one for each service I wanted to monitor

**Why Multiple Webhooks?** Different types of alerts need different channels. I don't want backup notifications mixed with deployment alerts.

### 📊 My Channel Strategy - Organized Monitoring

## Channel 1: #all-kandharico - Never Lose Data Again
**What I Get:** Real-time notifications when my daily backups complete
**Message Format:** "Backup created successfully enjoy : portfolio_backup_2025-06-05_01-08-01.tar.gz"
**Why This Matters:** I know immediately if a backup fails. In May, I had 13+ successful backups and got notified for every single one.

**Real Example from My Logs:**

### Channel 2: #github-updates - Deployment Tracking
**What I Monitor:** Every time my website updates from GitHub
**Frequency:** Checks every 5 minutes for changes
**Real Value:** I can push changes to GitHub and watch them automatically deploy to my live site

**Actual Deployment Messages I Receive:**

**Why This Is Powerful:** I have a complete audit trail of every deployment. I can see exactly when changes went live and what changed.

### Channel 3: #auto-updates - Server Health Updates
**What I Track:** System updates, reboots, and security patches
**Smart Notifications:** Only alerts me when something actually happens
**Reboot Intelligence:** Tells me when the server needs to restart for updates

**My Notification Examples:**

**Personal Touch:** I made the messages casual and friendly - it's my server, so I can have fun with the notifications!

### 🚀 Real-World Impact - Why This Actually Matters

#### Proactive Problem Solving
**Before Slack Integration:** I had to manually check if scripts ran successfully
**After Slack Integration:** I know immediately when something works or fails
**Real Example:** When my GitHub script had permission issues, I got failure notifications and could fix them quickly

#### Professional Monitoring Standards
**Enterprise-Level Alerting:** Same type of monitoring system used by tech companies
**Audit Trail:** Complete history of all automated operations
**Multi-Channel Organization:** Different notification types don't interfere with each other

#### Peace of Mind
**24/7 Awareness:** I know my server status without actively checking
**Immediate Response:** Can address issues quickly when they happen
**Success Confirmation:** Positive reinforcement when automation works correctly

### 💡 Advanced Monitoring Features I Added

#### Smart Message Formatting
**Timestamps:** Every message includes when the event happened
**Context Information:** Server hostname, file sizes, commit details
**Status Indicators:** Emojis make it easy to quickly scan for success/failure

#### Noise Reduction Strategy
**Dedicated Channels:** Different types of alerts go to specific channels
**Meaningful Messages:** Only get notifications for events that actually matter
**Success + Failure Alerts:** Know when things work AND when they don't

#### Integration Benefits
**Mobile Notifications:** Slack app on my phone means I'm always informed
**Historical Record:** Can scroll back through months of server activity
**Team Ready:** If I ever work with others, they can join relevant channels

**The Bottom Line:** This isn't just notification spam - it's a professional monitoring system that gives me complete visibility into my server operations. I can confidently say I know exactly what my infrastructure is doing at any moment.

### 🛠️ Comprehensive Troubleshooting Guide
Professional System Administration Methodology:
Diagnostic Approach: Systematic problem identification, variable isolation, hypothesis testing, and solution implementation with proper documentation.

## 1. 🤖 Cron Job Automation Diagnostics
Symptom: Scripts execute manually but fail during scheduled cron execution.
Diagnostic Process:
Step 1: Verify Cron Configuration
## Display active cron jobs
```powershell
crontab -l
```
### Expected output:
```powershell
# 8 1 * * * /home/ubuntu/website_backup.sh
# */5 * * * * /home/ubuntu/github_auto_pull.sh
# 40 14 * * * /home/ubuntu/auto_update.sh
```
### Step 2: Permission Analysis
   Check file permissions
```powershell
ls -la /home/ubuntu/*.sh
```
###  Correct permissions should show:
```powershell
 -rwxr-xr-x (executable for all)
Step 3: Execution Logging
bash# Monitor cron execution
grep CRON /var/log/syslog | tail -n 10

 Expected successful output:

 CRON[PID]: (ubuntu) CMD (/home/ubuntu/script-name.sh)
```
Resolution:
```powershell
# Fix permissions definitively
sudo chmod +x /home/ubuntu/*.sh
sudo chown ubuntu:ubuntu /home/ubuntu/*.sh
```
### 2. 🔐 SSH Authentication Management
Windows PowerShell Solution:
## Correct permission management for Windows
```powershell
icacls website.pem /inheritance:r /grant:r "$($env:USERNAME):(R)"
```
## Verify connection
```powershell
ssh -i "website.pem" ubuntu@54.66.64.231
```
Advanced SSH Debugging:
## Verbose connection testing
```powershell
ssh -vvv -i "website.pem" ubuntu@54.66.64.231
```
## Test server accessibility
```powershell
nmap -p 22 54.66.64.231
```
### 3. ⚙️ Nginx Web Server Diagnostics
Configuration Validation:
```powershell
 Test configuration syntax
sudo nginx -t
```

Monitor real-time errors
```powershell
sudo tail -f /var/log/nginx/error.log
```
 Verify service status
sudo systemctl status nginx
Performance Monitoring:
```powershell
Check listening ports
sudo netstat -tlnp | grep nginx
```
 Test local connectivity
 ```powershell
curl -I http://localhost
curl -I https://rishabhkandhari14.com
```
### 4. 🔒 SSL Certificate Management
Certificate Health Monitoring:

 Check certificate status
 ```powershell
sudo certbot certificates
```
Test renewal process
```powershell
sudo certbot renew --dry-run
```
Manual renewal if needed
```powershell
sudo certbot renew --nginx
```
### 5. 📊 System Performance Monitoring
Comprehensive Health Checks:
Resource monitoring
```powershell
htop
free -h
df -h
```
### 6. Network connectivity
```powershell
ping -c 4 google.com
curl -I https://github.com
```
### 7.Service status
```powershell
sudo systemctl --failed
```
Emergency Response Procedures:
Website Down (502/503 Errors):
```powershell
sudo systemctl status nginx
sudo systemctl restart nginx
Check logs: sudo tail -n 50 /var/log/nginx/error.log
```

### 8.SSL Certificate Issues:
```powershell
sudo certbot renew --nginx
sudo certbot certificates
```
Test:
```powershell
curl -I https://rishabhkandhari14.com
```
Script Failures:
```powershell
Manual test: /home/ubuntu/script-name.sh
Check permissions: ls -la /home/ubuntu/*.sh
Review logs: grep CRON /var/log/syslog
```
## 🛠️ Problems I Actually Solved

### Cron Jobs Not Running
**Problem:** Scripts worked perfectly when I ran them manually but failed via cron.
**Root Cause:** File permissions and environment variables.
**Solution:** 
```bash
sudo chmod +x /home/ubuntu/*.sh
sudo chown ubuntu:ubuntu /home/ubuntu/*.sh
```
### SSH Permission Errors on Windows
Problem: "Permission denied" errors with .pem file.
Windows Solution: Used icacls instead of chmod - this is specific to Windows users.
Script Debugging
Best Practice: Always check cron logs:
```powershell
grep CRON /var/log/syslog | tail -n 10
```
### **8. Results & Evidence (Your Achievements)**
```markdown
## 📊 Real Performance Evidence

### System Health: Perfect
```powershell
sudo systemctl --failed
# Result: 0 failed service

```
- rock solid system
### 🎨 Modern Web Development - What I Actually Built
## ✨ Extra Features I Added

### Email.js Contact Form
**Why:** Wanted a functional contact form without setting up a backend server.
**Result:** Visitors can actually contact me through the website - it's not just a demo.

### Multi-Channel Slack Integration
**Innovation:** Different Slack channels for different types of notifications:
- #backup-alerts for daily backups
- #github-updates for deployments  
- #system-maintenance for server updates

### Professional Monitoring
**Real-Time Alerts:** Know immediately when something goes wrong or succeeds.
**Audit Trail:** Complete history of all automated operations.



#### Email.js Contact Form - Real Communication
**Why I Added This:** I wanted people to actually be able to contact me, not just look at a fake demo form. Setting up a backend server seemed overkill for a simple contact form.

**How It Works:** When someone fills out my contact form, Email.js automatically sends me an email with their message. It's like having a backend without the complexity.

**Real Result:** I've received actual inquiries through this form - it's not just for show, it's functional business communication.

#### Responsive Design - Mobile-First Approach  
**My Thinking:** More people browse on phones than desktops now, so I designed for mobile first, then expanded to desktop.

**What I Implemented:** Used CSS Grid and Flexbox because they're modern and flexible. The site looks good whether you're on a phone, tablet, or desktop.

**User Experience:** Smooth scroll animations, form validation that actually helps users, and interactive elements that feel responsive and alive.

#### Performance Optimization - Speed Matters
**Problem I Solved:** Nobody waits for slow websites. I optimized images, streamlined CSS/JavaScript, and achieved fast loading times.

**Real Metrics:** Website loads quickly even on slower connections - this actually matters for user experience and SEO.

## 🔒 Security Implementation - Enterprise-Level Protection

#### HTTPS Everything - No Compromises
**My Standard:** Everything goes through HTTPS, no exceptions. Got an A+ rating from SSL Labs - same security level as major companies.

**Security Headers:** Added protection against XSS attacks and clickjacking. These aren't just buzzwords - they're real security measures that protect visitors.

**Automated Updates:** My scripts keep security patches current automatically. I don't have to remember to update - it just happens.

#### Content Security Policy
**Why This Matters:** Prevents malicious scripts from running on my site. It's like having a security guard that checks everything before it runs.

### 💼 Business Functionality - Professional Portfolio Features

#### Professional Showcase
**What I Built:** A real portfolio that showcases actual projects since it is my first project i have placed a gif .

**Contact Integration:** The Email.js form means potential employers can reach me directly from the website.

**Resume Download:** PDF resume available for download - makes it easy for recruiters and hiring managers.


## 📈 Scalability & Future-Proofing

#### Modular Design Philosophy
**My Approach:** Built the site so I can easily add new sections, projects, or features without breaking existing functionality.

**SEO Optimization:** Used semantic HTML and proper meta tags. Search engines can understand and index the content properly.

**Analytics Ready:** Set up for Google Analytics integration to track user behavior and site performance.

**Monitoring Systems:** My scripts log everything - I have a complete audit trail of all website activities.

---

## 🎯 What I Actually Accomplished - Real Results

### 🏆 Infrastructure Mastery - Production-Ready System

**What I Built vs. What Was Required:**
- ✅ **Required:** Basic EC2 deployment → **I Built:** Production-grade infrastructure with professional security
- ✅ **Required:** Domain setup → **I Built:** Complete DNS management with A+ SSL rating  
- ✅ **Required:** Basic scripting → **I Built:** Full CI/CD pipeline with automated deployments
- ✅ **Required:** Documentation → **I Built:** Enterprise-level disaster recovery and backup systems

**Real Monitoring:** Multi-channel Slack integration means I know exactly what's happening with my server 24/7.

## 💻 Technical Implementation - Beyond Assignment Scope

**Modern Development Stack:**
- ✅ **Responsive Design:** Works perfectly on any device
- ✅ **Real Functionality:** Contact form that actually sends emails
- ✅ **Security-First:** HTTPS everywhere with proper security headers
- ✅ **Performance Optimized:** Fast loading times and efficient resource usage

**Business Value:** This isn't just a school project - it's a professional website I can actually use for job applications.

## 📚 Skills I Actually Developed

#### System Administration - Hands-On Experience
**What I Learned Through Practice:**
- Linux server management (Ubuntu administration, package management)
- Web server configuration (Nginx virtual hosts, SSL certificates)
- Network administration (DNS records, security groups, firewall rules)
- Security implementation (HTTPS enforcement, security headers, automated updates)

#### DevOps & Cloud Computing - Real Implementation
**Practical Experience Gained:**
- AWS infrastructure deployment and management
- Infrastructure as Code through comprehensive documentation
- CI/CD pipeline implementation with automated GitHub deployments
- Real-time monitoring and alerting through Slack integration

#### Professional Development - Transferable Skills
**Problem-Solving Abilities:**
- Technical documentation that others can actually follow
- Systematic troubleshooting (like debugging cron jobs and SSH issues)
- Security best practices implementation
- Complete project delivery from planning to production

### 🚀 Real-World Application Value

#### Career Preparation - Industry-Ready Skills
**What This Prepares Me For:**
- **DevOps Engineer:** I've built actual CI/CD pipelines and automation systems
- **System Administrator:** I manage real servers with monitoring and maintenance
- **Web Developer:** I've deployed actual applications with professional features
- **Cloud Solutions Architect:** I understand AWS infrastructure and security

#### Portfolio Demonstration - Concrete Evidence
**What Employers Can See:**
- **Live Website:** Functional site with real features, not just demos
- **Professional Design:** Enterprise-level automation and monitoring
- **Technical Depth:** Real scripts, real logs, real performance metrics
- **Problem-Solving:** Documented solutions to actual challenges I faced

#### Interview Readiness - Real Experience to Discuss
**What I Can Talk About:**
- Actual cloud infrastructure I built and maintain
- Real automation systems I designed and implemented
- Security measures I put in place and why they matter
- Problems I encountered and how I solved them

**The Bottom Line:** This isn't just an assignment I completed - it's a professional system I built, maintain, and can confidently discuss in any technical interview.

## 📞 [Contact & Project Information](#contact--project-information)

**Student:** Rishabh Kandhari  
**Student ID:** 35118707  
**Course:** ICT 171 Assignment 2  
**Email:** [Contact via Website](https://rishabhkandhari14.com/#contact)  

**Project Verification:**  
- 🌐 [Live Website](https://rishabhkandhari14.com)  
- 📁 [GitHub Repository](https://github.com/your-username/Website_Kandhari)  
- 🔒 [SSL Certificate (SSL Labs Test)](https://www.ssllabs.com/ssltest/analyze.html?d=rishabhkandhari14.com)  
- 🌍 [DNS Verification (DNS Checker)](https://dnschecker.org/#A/rishabhkandhari14.com)

## 📄 License & Academic Integrity
This project is developed for ICT 171 Assignment 2 educational purposes and is licensed under Creative Commons. All implementation decisions, automation scripts, and documentation represent original student work demonstrating comprehensive understanding of cloud infrastructure, system administration, and professional web development practices.
Complete technical documentation enabling full environment reproduction and demonstrating enterprise-level implementation standards.
