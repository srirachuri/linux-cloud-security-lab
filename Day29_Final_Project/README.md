# Day 29 Final Project — AWS EC2 Linux Server Administration & Support

## Project Overview

This project demonstrates deploying, configuring, administering, monitoring, troubleshooting, and securing a Linux server running on **AWS EC2**.

The lab focuses on practical Linux administration and cloud support tasks that are commonly performed by Cloud Support Engineers, Cloud Operations Engineers, and Junior Cloud Security Engineers.

The project was completed using an Ubuntu Linux EC2 instance in AWS.

---

## Objectives

The main objectives of this project were to practice:

- AWS EC2 instance administration
- Linux server administration
- SSH remote access
- Linux file and directory permissions
- User and group management
- Ownership management
- Linux service management
- Systemd and journal logs
- Package management
- Nginx installation and administration
- Server monitoring
- Basic troubleshooting
- Cloud security fundamentals

---

## Technologies Used

| Technology | Purpose |
|---|---|
| AWS EC2 | Cloud virtual server |
| Ubuntu Linux | Server operating system |
| SSH | Remote server access |
| Nginx | Web server |
| systemd | Service management |
| journalctl | System log investigation |
| APT | Package management |
| Linux CLI | Server administration |
| AWS Security Groups | Network access control |

---

## AWS Environment

- Cloud Provider: **Amazon Web Services (AWS)**
- Service: **Amazon EC2**
- Operating System: **Ubuntu Linux**
- Instance Type: **t3.micro**
- Region: **Asia Pacific (Mumbai)**
- Access Method: **SSH**
- Web Server: **Nginx**

---

# Project Tasks

## 1. EC2 Instance Deployment

An Ubuntu Linux EC2 instance was deployed using the AWS Management Console.

The instance was configured with:

- Ubuntu Linux
- t3.micro instance type
- SSH access
- Network configuration
- Security Group rules
- Public connectivity

---

## 2. SSH Connection

The EC2 instance was accessed remotely using SSH from Windows PowerShell.

Example:

```
ssh -i "linux-key.pem" ubuntu@<PUBLIC-IP>
```

After connecting successfully, the Ubuntu server displayed the system information and provided access to the Linux shell.

---

## 3. Linux System Information

Basic Linux system information was inspected after connecting to the server.

Commands used included:

```
whoami
pwd
ls -l
```

These commands were used to identify the current user, working directory, and files/directories.

---

# 4. Linux File and Directory Permissions

A test application directory was created to practice Linux permissions.

```
mkdir test_app
chmod 777 test_app
ls -ld test_app
```

The permissions were then changed to a more restrictive configuration:

```
chmod 755 test_app
```

The resulting permissions were verified using:

```
ls -ld test_app
```

This demonstrated how Linux permissions control access to files and directories.

---

# 5. File Ownership

The ownership of the directory was explicitly configured using:

```
sudo chown ubuntu:ubuntu test_app
```

Ownership was then verified with:

```
ls -ld test_app
```

This demonstrated practical Linux ownership management.

---

# 6. System Logs

Linux system logs were investigated using `journalctl`.

Command:

```
sudo journalctl -xe
```

The command was used to inspect systemd events and service activity.

The logs showed events such as:

- System startup
- User sessions
- Service activity
- SSH activity
- sudo commands
- System shutdown events

---

# 7. Authentication Log Analysis

The authentication log was examined using:

```
sudo cat /var/log/auth.log
```

Specific SSH activity was also investigated using:

```
sudo grep Accepted /var/log/auth.log
```

and:

```
sudo grep Failed /var/log/auth.log
```

This provided practical experience with investigating authentication and SSH-related events.

---

# 8. SSH Monitoring

The system logs were used to identify SSH activity.

The logs showed events including:

```
Server listening on 0.0.0.0 port 22
Server listening on :: port 22
Accepted publickey for ubuntu
```

This helped demonstrate how Linux administrators can investigate remote access activity.

---

# 9. Package Management

The Ubuntu package repository information was updated using:

```
sudo apt update
```

The system reported available package updates.

This is a standard Linux administration task used before installing or updating software.

---

# 10. Nginx Installation

Nginx was installed using:

```
sudo apt install nginx -y
```

After installation, the Nginx service was checked using:

```
sudo systemctl status nginx
```

The service was running successfully.

Example status:

```
Active: active (running)
```

---

# 11. Nginx Service Management

The Nginx service was managed using systemd.

Useful commands include:

```
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl status nginx
```

The service was verified as active and running.

---

# 12. Running Services

Running system services were inspected using:

```
systemctl list-units --type=service --state=running
```

This displays currently running services such as:

- nginx.service
- ssh.service
- systemd-journald.service
- systemd-networkd.service
- cron.service
- rsyslog.service

This helped build familiarity with Linux service administration.

---

# 13. Final Verification

The final project environment was verified through:

- EC2 instance configuration
- SSH connectivity
- Linux administration commands
- File permissions
- File ownership
- System logs
- Authentication logs
- Nginx installation
- Nginx service status
- Running services

The project was completed.

---

# Security Concepts Practised

This project provided practical exposure to several cloud security concepts.

### Authentication

SSH public-key authentication was used to securely access the EC2 server.

### Access Control

Linux permissions and ownership were configured to control access to resources.

### Network Security

AWS Security Groups were used to control network access to the EC2 instance.

### Logging and Monitoring

Linux authentication logs and systemd journals were examined to investigate system activity.

### Service Security

Running services were inspected to understand which services were active on the server.

---

# Troubleshooting Skills Practised

The project also developed practical troubleshooting skills.

### SSH Troubleshooting

Investigating:

- SSH connectivity
- Port 22
- Authentication
- SSH service status

### Service Troubleshooting

Checking:

```
sudo systemctl status nginx
```

### Log Troubleshooting

Investigating:

```
sudo journalctl -xe
```

and:

```
sudo cat /var/log/auth.log
```

### Permission Troubleshooting

Checking:

```
ls -ld test_app
```

and modifying permissions using:

```
chmod
```

### Ownership Troubleshooting

Checking and modifying ownership using:

```
chown
```

---

# Important Commands

## Linux

```
whoami
pwd
ls -l
ls -ld
```

## Permissions

```
chmod 755 test_app
chmod 777 test_app
```

## Ownership

```
sudo chown ubuntu:ubuntu test_app
```

## Package Management

```
sudo apt update
sudo apt install nginx -y
```

## Services

```
sudo systemctl status nginx
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
```

## Logs

```
sudo journalctl -xe
sudo cat /var/log/auth.log
sudo grep Accepted /var/log/auth.log
sudo grep Failed /var/log/auth.log
```

## Running Services

```
systemctl list-units --type=service --state=running
```

---

# Skills Demonstrated

- AWS EC2
- Ubuntu Linux
- Linux Administration
- SSH
- Linux Permissions
- File Ownership
- User Management
- Systemd
- Journalctl
- Authentication Logs
- Nginx
- Package Management
- Service Management
- Troubleshooting
- Cloud Security Fundamentals
- Security Monitoring

---

# Project Evidence

Screenshots included in this project document the following activities:

1. AWS EC2 instance configuration
2. EC2 instance status
3. SSH connection to Ubuntu
4. Linux system information
5. Linux permissions
6. File ownership
7. System logs
8. Authentication logs
9. APT package management
10. Nginx installation
11. Nginx service status
12. Running Linux services
13. Final project completion

---

# What I Learned

Through this project, I gained practical experience administering a Linux server running in AWS EC2.

I learned how to:

- Connect to a cloud Linux server using SSH
- Manage Linux files and permissions
- Manage file ownership
- Install and manage software packages
- Start, stop, and monitor Linux services
- Install and verify Nginx
- Investigate system and authentication logs
- Monitor SSH activity
- Perform basic cloud server troubleshooting
- Apply basic security and access-control concepts

---

# Future Improvements

Possible future improvements include:

- Configure CloudWatch monitoring
- Create CloudWatch alarms
- Configure automated log monitoring
- Add Nginx access-log analysis
- Add security monitoring scripts
- Implement automated backup
- Add infrastructure-as-code using Terraform
- Add CI/CD automation
- Integrate the server with a security monitoring solution

---

# Author

**Sri Gayathri**

Aspiring Cloud Security Engineer
