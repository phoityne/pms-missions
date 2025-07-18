# 🔐 Security Checklist for Linux & Web Server (Port 8080)

This document outlines general security best practices to apply when building a Linux-based web service, especially in root-accessible environments like those initialized via the `web-service-prompt`.

---

## 🔧 Linux System-Level Hardening

- [ ] **Set restrictive file permissions** (`chmod`, `chown`) on all source and config files
- [ ] **Disable unnecessary services** using `systemctl` or `dnf remove`
- [ ] **Keep the system updated** (`dnf update -y`)

---

## 🌐 Web Server-Level Hardening

- [ ] **Return minimal HTTP headers** to reduce fingerprinting
- [ ] **Limit request size and rate** to prevent DoS attacks
- [ ] **Log all access and error events**, and monitor logs periodically

