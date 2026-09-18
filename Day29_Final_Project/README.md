# Day 29 Final Project — AWS EC2 Linux Server Administration & Support

## Project Overview

This final project simulates a real-world **Cloud Support / Linux Administration** task on an AWS EC2 Linux server.

### Scenario

A cloud server is running, but something needs checking and fixing.

The tasks were:

1. SSH into the EC2 instance
2. Check system logs using `journalctl`
3. Review authentication logs
4. Identify and correct unsafe file permissions
5. Verify file ownership
6. Update the APT package repository
7. Install a required package
8. Verify that the installed service is running
9. Check currently running system services
10. Confirm successful completion
11. Stop the EC2 instance after completing the lab

---

## Objectives

- Practice secure SSH access to an AWS EC2 Linux server
- Understand Linux system logs
- Use `journalctl` for troubleshooting
- Review authentication activity
- Understand Linux file permissions
- Correct unsafe permissions using `chmod`
- Correct file ownership using `chown`
- Manage packages using APT
- Install and verify Nginx
- Check Linux services using `systemctl`
- Perform basic cloud server troubleshooting
- Practice documenting a real-world support workflow

---

## Environment

| Component | Details |
|---|---|
| Cloud Platform | AWS |
| Service | Amazon EC2 |
| Operating System | Ubuntu 24.04.3 LTS |
| Architecture | x86_64 |
| Instance Type | t3.micro |
| Access Method | SSH |
| Package Manager | APT |
| Web Server Installed | Nginx |
| Service Manager | systemd |

---

# Part 1 — SSH into the EC2 Instance

I accessed the EC2 instance securely from Windows PowerShell using an SSH private key.
Part 2 — Check System Logs

The system logs were reviewed using:

sudo journalctl -xe

This command displays recent systemd journal messages and provides information useful for troubleshooting services, startup events, sessions, and system activity.

The logs showed successful system startup and service activity.

Examples of information observed included:

system startup
user session creation
systemd services
SSH activity
authentication activity
APT-related activity
Part 3 — Review Authentication Logs

The authentication log was inspected using:

sudo cat /var/log/auth.log

The log contained authentication and security-related events.

Examples included:

User creation
User group membership
SSH server activity
Successful public-key authentication
User sessions
sudo activity
Cron activity

Additional filtering commands were also used:

sudo grep Accepted /var/log/auth.log

and:

sudo grep Failed /var/log/auth.log

These commands help administrators quickly investigate successful and failed authentication attempts.

Part 4 — Check and Fix File Permissions

A test application directory was created:

mkdir test_app

The permissions were intentionally changed to an unsafe configuration:

chmod 777 test_app

The permissions were then checked:

ls -ld test_app

The output showed:

drwxrwxrwx

This means the owner, group, and other users had read, write, and execute permissions.

For a typical application directory, allowing write access to everyone can create unnecessary security risk.

Part 5 — Correct the Permissions

The directory permissions were changed to:

chmod 755 test_app

The permissions were verified:

ls -ld test_app

The resulting permissions were:

drwxr-xr-x

This provides:

Owner: read, write, execute
Group: read, execute
Others: read, execute

The permissions were therefore more restrictive than the original 777 configuration.

Part 6 — Verify File Ownership

The ownership of the directory was also checked and corrected using:

sudo chown ubuntu:ubuntu test_app

Then:

ls -ld test_app

The final ownership showed:

ubuntu ubuntu

This confirms that the directory belongs to the intended ubuntu user and group.

Part 7 — Update the Package Repository

Before installing the required package, the APT package information was updated:

sudo apt update

The command successfully contacted the Ubuntu package repositories and downloaded updated package metadata.

The system reported that packages could be upgraded.

Part 8 — Install Nginx

Nginx was installed using:

sudo apt install nginx -y

The installation completed successfully.

The installed Nginx package was:

nginx 1.24.0-2ubuntu7.5

The installation also created and configured the Nginx systemd service.

Part 9 — Verify Nginx Service

The Nginx service was checked using:

sudo systemctl status nginx

The output confirmed:

Active: active (running)

This verifies that Nginx was successfully installed and running.

Part 10 — Check Running Services

The currently running system services were reviewed using:

systemctl list-units --type=service --state=running

The output showed multiple active services, including:

nginx.service
ssh.service
systemd-journald.service
systemd-networkd.service
systemd-resolved.service
rsyslog.service
cron.service
snap.amazon-ssm-agent.amazon-ssm-agent.service

This helped verify the operational state of the server.

Part 11 — Verify Project Completion

A completion message was created:

echo "Day 29 Final Project completed successfully" > day29_success.txt

The file was verified using:

cat day29_success.txt

Output:

Day 29 Final Project completed successfully

This confirmed that all planned tasks were completed.

Part 12 — Stop the EC2 Instance

After completing the lab, the EC2 instance was stopped from the AWS EC2 console.

The final AWS console screenshot shows:

Instance state: Stopped

Stopping the instance after completing the lab helps avoid unnecessary compute usage.

Troubleshooting Skills Practiced

This project provided practical experience with:

SSH
ssh -i "linux-key.pem" ubuntu@<EC2-PUBLIC-IP>
System Logs
sudo journalctl -xe
Authentication Logs
sudo cat /var/log/auth.log
Log Filtering
sudo grep Accepted /var/log/auth.log
sudo grep Failed /var/log/auth.log
File Permissions
ls -ld test_app
chmod 777 test_app
chmod 755 test_app
File Ownership
sudo chown ubuntu:ubuntu test_app
Package Management
sudo apt update
sudo apt install nginx -y
Service Management
sudo systemctl status nginx
Running Services
systemctl list-units --type=service --state=running

```bash
ssh -i "linux-key.pem" ubuntu@<EC2-PUBLIC-IP>
