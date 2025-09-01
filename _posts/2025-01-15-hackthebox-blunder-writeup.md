---
layout: post
title: "HackTheBox: Blunder Machine Writeup"
date: 2025-01-15 10:00:00 +0300
categories: [hackthebox, writeup, linux]
tags: [bludit, php, privilege-escalation, sudo]
image: /img/htb-blunder.jpg
excerpt: "A detailed walkthrough of the HackTheBox Blunder machine featuring Bludit CMS exploitation and sudo privilege escalation."
---

# HackTheBox: Blunder Machine Writeup

Today we'll be tackling the **Blunder** machine from HackTheBox. This is a Linux box that involves exploiting a Bludit CMS installation and escalating privileges through sudo vulnerabilities.

## Initial Reconnaissance

Let's start with our usual nmap scan to discover open ports:

```bash
nmap -sC -sV -oA blunder 10.10.10.191
```

The scan reveals:
- Port 21: FTP
- Port 80: HTTP (Apache)

## Web Enumeration

Navigating to the web application, we discover it's running **Bludit CMS**. Let's enumerate further:

```bash
gobuster dir -u http://10.10.10.191 -w /usr/share/wordlists/dirb/common.txt
```

Key findings:
- `/admin` - Login panel
- `/bl-content` - Content directory
- `/bl-kernel` - Core files

## Exploitation

After discovering the Bludit version, we find it's vulnerable to:
1. **Authentication bypass**
2. **Directory traversal**
3. **Remote code execution**

### Step 1: Authentication Bypass

We use a known vulnerability (CVE-2019-16113) to bypass authentication:

```python
# Exploit code snippet
import requests

url = "http://10.10.10.191"
# ... exploitation logic
```

### Step 2: File Upload & RCE

Once authenticated, we upload a PHP reverse shell and gain initial access.

## Privilege Escalation

After gaining a foothold as `www-data`, we discover:
- User credentials in configuration files
- Sudo vulnerabilities

### Method 1: Password Reuse

Found credentials in `/var/www/bludit-3.9.2/bl-content/databases/users.php`

### Method 2: Sudo Exploitation

The target user has specific sudo privileges that can be exploited using CVE-2019-14287.

## Lessons Learned

1. Always check for default credentials
2. CMS versions matter - keep them updated
3. Proper sudo configuration is crucial
4. File permissions should be reviewed regularly

## Conclusion

Blunder demonstrates common web application vulnerabilities and privilege escalation techniques. The key takeaways involve proper input validation, secure configuration management, and regular security updates.

---

**Happy Hacking!** 🔐

*Follow me on [Medium](https://medium.com/@thisguyhack) for more cybersecurity content!*
