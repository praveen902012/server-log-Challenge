# Challenge 2025

*Trace the attacker in distributed logs and extract key breach details.*
## Storyline

A distributed system of three servers quietly handled the day’s traffic, with a range-based load balancer ensuring each request reached its proper destination. For the most part, things ran smoothly.

But hidden deep inside the source code was a subtle flaw, an overlooked detail from using an unsafe language. The developers had known this could cause trouble eventually; they just didn’t expect it to surface today.

An attacker discovered the weakness and slipped through. With a carefully crafted request, they triggered a silent privilege escalation. In an instant, they went from an ordinary user to an administrator.

The compromised server struggles for a while before succumbing to the attack and going offline. In response, the load balancer reroutes all traffic to one of the remaining two servers.

Undeterred, the attacker makes their move. For the first time, they access a restricted endpoint that was never meant for them!

Your task is to trace their path through the logs and identify two crucial moments:

---

## Challenge Overview

A subtle code flaw in a distributed system allowed an attacker to escalate privileges and take down a server.  
Your goal is to review server logs and pinpoint:  
- **The exact moment and request used for the attack (“The Attack”)**
- **The first subsequent access to a privileged endpoint (“Post-Attack”)**

---

## Steps to Solve

### 1. Download Your Log File
- Go to the [Google Drive folder](https://drive.google.com/drive/folders/1e7UBoThqqZDCuSEpFaNE2aJ9CtUKaRNe?usp=sharing)
- Find and download the log file **named with your email address**

### 2. Understand Endpoint Types

| Endpoint Type         | Endpoints        |
|----------------------|------------------|
| **Public**           | `'/', '/login', '/register', '/logout', '/profile', '/search', '/images', '/videos', '/help', '/terms', '/faq', '/support'` |
| **Privileged/Admin** | `'/admin', '/settings', '/users', '/logs', '/reports', '/metrics', '/backup', '/restore', '/deleteUser', '/updateUser', '/banUser', '/unbanUser', '/escalateUser', '/news', '/about', '/contact'` |

### 3. Analyze the Logs
- Trace requests routed through each server.
- Look for:
    - Unusual/non-admin subnet IP accessing a privileged endpoint.
    - Abrupt CPU/memory/temp changes.
    - The fallback event when traffic is redirected.
- For each “crucial moment,” extract:

#### The Attack
- **Server Number**
- **Timestamp**
- **IP address**
- **Endpoint**
- **Method**
- **CPU utilization**
- **Memory utilization**
- **CPU temperature**

#### Post-Attack
- **Fallback Server Number**
- **Timestamp**
- **Endpoint**
- **Method**
- **CPU utilization**
- **Memory utilization**
- **CPU temperature**

---

## Answer Submission

- write a deatiled report regarding your findings 

---

## Tips

- Admins only come from specific network subnets—unusual IPs are a giveaway.
- The “Attack” is a privilege escalation attempt; watch for method (POST/PUT), odd payloads, or spiked CPU/memory/temp stats.
- The “Post-Attack” is the first privileged endpoint request post-compromise.
- Use text editors or scripts to search log entries for `privileged_endpoints` and pattern anomalies.

**Good luck!**
