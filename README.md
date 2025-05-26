# Task 07 - Risk Analysis of Open Ports

## 📌 Objective

Analyze the open ports discovered during a TCP SYN scan on the local network (`192.168.1.0/24`) and identify potential security risks associated with those ports.

---

## 🧪 What I Did

- Ran a SYN scan using Nmap:
  ```bash
  nmap -sS 192.168.1.0/24 -oN scan_results.txt
Collected results from scan_results.txt.

Identified open ports on live hosts.

Researched common vulnerabilities and risks for those services.

Documented the risks and provided security recommendations in ports_analysis.md.

## 📂 Files Included

| File Name           | Description                                     |
| ------------------- | ----------------------------------------------- |
| `scan_results.txt`  | Raw Nmap scan output                            |
| `ports_analysis.md` | Detailed analysis of each open port             |
| `README.md`         | This summary file                               |
| `screenshots/`      | (Optional) Screenshots of terminal, tools, etc. |

## 🔍 Summary of Key Risks

| IP Address   | Risky Services        | Notes                                  |
| ------------ | --------------------- | -------------------------------------- |
| 192.168.1.1  | FTP (21), HTTP (80)   | FTP is insecure; HTTP should use HTTPS |
| 192.168.1.33 | iPhone sync (62078)   | Should not be exposed to network       |
| 192.168.1.37 | Dev web server (8000) | Ensure dev servers are not exposed     |

