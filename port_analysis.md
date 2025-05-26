# 🔐 Open Port Risk Analysis

This document analyzes the open ports found during a TCP SYN scan of the local network (`192.168.1.0/24`) and highlights associated security risks and recommendations.

---

## 🔎 192.168.1.1

### ✅ Open Ports:
- **21/tcp (FTP)**  
  - **Risk**: Transmits data and credentials in plain text. Easily sniffed.
  - **Recommendations**: 
    - Disable if unused.
    - Replace with SFTP or FTPS.
    - Restrict IPs via firewall.

- **22/tcp (SSH)** — *Filtered*  
  - **Risk**: Potential brute-force attack vector if reachable.
  - **Recommendations**:
    - Use key-based authentication.
    - Use a non-standard port.
    - Monitor login attempts.

- **53/tcp (DNS)**  
  - **Risk**: Can be abused for DNS amplification attacks or information leakage.
  - **Recommendations**:
    - Restrict to internal use.
    - Validate and secure zone transfers.

- **80/tcp (HTTP)**  
  - **Risk**: Unencrypted web traffic; may expose sensitive data.
  - **Recommendations**:
    - Redirect to HTTPS.
    - Patch web server software.
    - Use WAF (Web Application Firewall).

- **443/tcp (HTTPS)**  
  - **Risk**: Secure but still may be vulnerable to misconfigurations (e.g., weak TLS).
  - **Recommendations**:
    - Use strong TLS ciphers.
    - Keep certificates up to date.
    - Run vulnerability scans on web apps.

---

## 🔎 192.168.1.33

### ✅ Open Ports:
- **49152/tcp (unknown)**  
  - **Risk**: High-numbered dynamic port — could be used by custom or P2P apps.
  - **Recommendations**:
    - Identify the service.
    - Restrict via firewall if unnecessary.

- **62078/tcp (iPhone sync / usbmuxd)**  
  - **Risk**: Exposes Apple sync services over the network.
  - **Recommendations**:
    - Disable remote sync.
    - Block externally.
    - Use only via USB when needed.

---

## 🔎 192.168.1.37

### ✅ Open Ports:
- **8000/tcp (HTTP-alt)**  
  - **Risk**: Often used for dev/testing servers; may lack security hardening.
  - **Recommendations**:
    - Don’t expose dev servers externally.
    - Add authentication and HTTPS.
    - Restrict access.

- **8089/tcp (unknown)**  
  - **Risk**: Uncommon port; may be used by Splunk or other local services.
  - **Recommendations**:
    - Identify the service.
    - Disable or restrict unless needed.

---

## 🛑 Hosts with No Open Ports

- 192.168.1.42  
- 192.168.1.44  
- 192.168.1.45  
All ports closed. No immediate risk detected.

---

# ✅ Summary

| IP Address      | Ports           | High Risk Ports     |
|------------------|------------------|----------------------|
| 192.168.1.1     | 21, 22, 53, 80, 443 | **21 (FTP), 80 (HTTP)** |
| 192.168.1.33    | 49152, 62078     | **62078**             |
| 192.168.1.37    | 8000, 8089       | **8000**              |

---

# 📌 Recommendations

- Block unused ports via host firewall or router.
- Run vulnerability scans on exposed services.
- Harden services with encryption and authentication.
- Monitor network for suspicious connections.

