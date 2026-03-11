# Linux Web Server Deployment, Monitoring & Security

## 📌 Project Overview

This project demonstrates how to **deploy, monitor, and secure a production-style Linux web server environment** using **AlmaLinux**.

The setup includes:

- LAMP Stack Deployment
- Infrastructure Monitoring using Prometheus and Grafana
- Apache Virtual Hosting
- Linux Server Security Hardening

This project showcases **practical Linux System Administration and Monitoring skills**.

---

# 🏗 Architecture

| Component | Tool |
|-----------|------|
| Operating System | AlmaLinux |
| Web Server | Apache |
| Database | MariaDB |
| Backend Language | PHP |
| Monitoring | Prometheus |
| Visualization | Grafana |
| Metrics Exporter | Node Exporter |
| Security | Firewalld, Fail2Ban, SSH Hardening, SELinux |

---

# 📦 Project Components

---

# 1️⃣ LAMP Stack Deployment

Installed **Apache, MariaDB, and PHP** to host web applications.

## Install Packages

```bash
dnf install httpd mariadb-server php php-mysqlnd -y
Start Services
systemctl enable --now httpd
systemctl enable --now mariadb
Verify Installation
php -v
mysql --version
systemctl status httpd
Test Web Server
echo "Linux Web Server Working" > /var/www/html/index.html

Open in browser:

http://SERVER-IP
Screenshot
screenshots/lamp-webserver-working.png
2️⃣ Server Monitoring (Prometheus + Grafana)

Installed Prometheus to collect system metrics and Grafana to visualize them.

Monitoring Tools

Prometheus

Node Exporter

Grafana

Metrics Monitored

CPU Usage

Memory Usage

Disk Usage

Network Traffic

System Load

System Uptime

Prometheus Interface
http://SERVER-IP:9090
Screenshot
screenshots/prometheus-targets.png
Grafana Dashboard

Grafana was configured to use Prometheus as the data source.

Dashboard Used:

Node Exporter Full Dashboard (ID: 1860)

Grafana URL

http://SERVER-IP:3000
Screenshot
screenshots/grafana-node-exporter-dashboard.png
3️⃣ Apache Virtual Hosting

Configured Apache to host multiple websites on a single server using different domain names.

Example Domains
site1.local
site2.local
Directory Structure
/var/www/site1
/var/www/site2
Example VirtualHost Configuration
<VirtualHost *:80>
ServerName site1.local
DocumentRoot /var/www/site1
</VirtualHost>

<VirtualHost *:80>
ServerName site2.local
DocumentRoot /var/www/site2
</VirtualHost>
Testing
curl http://site1.local
curl http://site2.local
Screenshot
screenshots/apache-virtual-host-test.png
4️⃣ Linux Server Security Hardening

Implemented multiple security measures.

🔐 SSH Hardening

Edited SSH configuration file.

vi /etc/ssh/sshd_config

Security settings applied:

PermitRootLogin no
PasswordAuthentication no
PermitEmptyPasswords no

Restart SSH:

systemctl restart sshd

Verify:

systemctl status sshd
Screenshot
screenshots/ssh-hardening-verification.png
🔥 Firewall Configuration

Configured Firewalld to allow required services.

firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
firewall-cmd --permanent --add-service=ssh
firewall-cmd --reload

Verify firewall rules:

firewall-cmd --list-all
Screenshot
screenshots/firewall-rules.png
🛡 Fail2Ban Intrusion Protection

Installed Fail2Ban to prevent brute-force attacks.

dnf install fail2ban -y

Start service:

systemctl enable --now fail2ban

Check status:

fail2ban-client status
Screenshot
screenshots/fail2ban-status.png
🧩 SELinux Verification

Checked SELinux status.

getenforce
sestatus

Expected output:

Enforcing
Screenshot
screenshots/selinux-status.png
🧠 Skills Demonstrated

Linux System Administration

Web Server Deployment

Infrastructure Monitoring

Linux Security Hardening

Networking & Firewall Configuration

Troubleshooting & Diagnostics

📷 Screenshots

Recommended screenshots to include in the repository.

screenshots/
│
├── lamp-webserver-working.png
├── prometheus-targets.png
├── grafana-node-exporter-dashboard.png
├── apache-virtual-host-test.png
├── ssh-hardening-verification.png
├── firewall-rules.png
├── fail2ban-status.png
└── selinux-status.png
⚙ Technologies Used

Linux (AlmaLinux)

Apache HTTP Server

MariaDB

PHP

Prometheus

Grafana

Node Exporter

Firewalld

Fail2Ban

SELinux

🎯 Conclusion

This project demonstrates how to deploy, monitor, and secure a Linux-based web server environment using industry-standard tools.

It highlights core skills required for Linux System Administration and DevOps roles, including web server deployment, monitoring, security hardening, and infrastructure management.
