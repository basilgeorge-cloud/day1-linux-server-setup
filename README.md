# day1-linux-server-setup

## Objective
Set up a Linux server, enable SSH, and deploy a web server.

---

## Environment
- OS: Ubuntu Server
- VM: VirtualBox
- Network: Bridged Adapter
- IP Address: 192.168.X.X

---

## Steps Performed

### 1. Installed Ubuntu Server
- Created VM
- Enabled SSH

### 2. Connected via SSH

- ssh vboxuser@192.168.X.X

### 3. Installed Nginx

- sudo apt update
- sudo apt install nginx -y

**#### Issues Faced**
  
   Issue 1: Apache page showing instead of Nginx

   Problem: Apache default page was showing in browser

        Investigation:
              curl http://localhost
              sudo ss -tulnp | grep :80

   Cause: Apache was still running and occupying port 80

         Solution:
               sudo apt purge apache2 -y
               sudo pkill apache2
               sudo systemctl restart nginx
   Verification
     curl http://localhost → showed Nginx page
     Browser → showed custom HTML
     Port 80 → owned by nginx

**####  Key Learnings**     
       - One port can be used by only one service
       - Always verify using ss and curl
       - Service status alone is not reliable
