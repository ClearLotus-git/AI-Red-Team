# Attacking System Components — Summary

The **system component** includes the underlying infrastructure that hosts an ML-based system, such as **hardware, operating systems, system configuration, and model deployment details**. While many risks mirror traditional IT environments, ML deployments introduce additional system-level threats that must be considered.

---

## Why the System Component Is Critical
- Hosts and executes the ML model
- Controls access, availability, and performance
- Misconfigurations can undermine all other security controls
- Often exposed to the public through APIs or services

---

## Key Risks

### **System Misconfigurations**
Improper or default system settings can expose infrastructure to attackers.

**Common misconfigurations include:**
- Open or unnecessary network ports
- Weak or overly permissive ACLs
- Exposed administrative interfaces
- Default or weak credentials

These issues are frequently easy to identify and exploit using automated scanning tools.

---

### **Insecure ML Deployments**
ML models deployed without adequate security controls are vulnerable to:
- Unauthorized access
- Data leakage
- Abuse of inference endpoints
- Attacks discussed in model and data components

Missing safeguards include:
- Authentication and authorization
- Encryption
- Input validation

---

### **Resource Exhaustion Attacks**
ML workloads are computationally expensive and susceptible to:
- Denial-of-Service (DoS)
- Distributed Denial-of-Service (DDoS)

**Attack methods include:**
- Flooding inference endpoints with requests
- Submitting complex inputs to maximize CPU/GPU usage

**Impacts:**
- Service outages
- Increased operational costs (especially in auto-scaling environments)
- Distraction for security teams, enabling secondary attacks

---

## Attacker Tactics, Techniques & Procedures (TTPs)

### **Vulnerability Scanning & Exploitation**
- Scan for outdated or vulnerable software
- Exploit known CVEs in OS or system services

---

### **Credential Attacks**
- Password spraying using default or common credentials
- Brute-force attacks against exposed services (e.g., SSH, admin panels)

---

### **Misconfiguration Abuse**
- Identify weak firewall rules or ACLs
- Exploit exposed management interfaces
- Bypass poorly configured access controls

---

## Conclusion
System-level weaknesses remain a **foundational threat** to ML-based deployments. Misconfigurations, insecure deployments, and insufficient resource controls can enable attackers to compromise availability, confidentiality, and integrity—often with minimal effort. Securing the system component is essential to protecting the entire AI application lifecycle.

---

## Key Takeaway
Strong system hardening, secure deployment practices, credential hygiene, and resource monitoring are **non-negotiable** for defending ML-based systems against real-world attacks.
