```markdown
# 🔥 Firewall Setup & Testing on Linux

## Overview
This guide explains how to set up and test firewall rules using **UFW (Uncomplicated Firewall)** on **Kali Linux**. It covers blocking inbound traffic, testing rules, allowing SSH, and documenting the configuration.

## Objective
The goal of this guide is to configure and test basic firewall rules using **UFW (Uncomplicated Firewall)** on Kali Linux. We will:
- List current firewall rules.
- Block inbound traffic on a specific port.
- Test the firewall configuration.
- Allow SSH for remote access.
- Remove test rules and restore the original state.
- Document steps and summarize firewall functionality.

## Tools Required
- Kali Linux
- **UFW (Uncomplicated Firewall)** or **iptables**
- **Telnet**, **SSH**, and testing tools like **Firewalk** or **ftester**

---

## 🚀 Step-by-Step Firewall Configuration on Kali Linux

### 📌 Install and Enable UFW
First, update your package repository and install **UFW**:
```bash
sudo apt update && sudo apt install ufw -y
```
Enable the firewall:
```bash
sudo ufw enable
```

### 📌 List Existing Rules
Check existing rules to see what is allowed or blocked:
```bash
sudo ufw status verbose
```

### 🚫 Block Telnet (Port 23)
To block incoming traffic on **port 23** (commonly used for Telnet), run:
```bash
sudo ufw deny 23/tcp
```
Verify the rule:
```bash
sudo ufw status
```

### 🔎 Test the Rule
Attempt to connect to **port 23** locally or remotely to check if it is blocked:
```bash
telnet localhost 23
```
If successful, the firewall isn't filtering properly.

### ✅ Allow SSH (Port 22)
To enable SSH access (essential for remote administration), allow **port 22**:
```bash
sudo ufw allow 22/tcp
```

### 🛠 Remove Test Rule
After testing, remove the block rule for **port 23**:
```bash
sudo ufw delete deny 23/tcp
```

---

## 🧪 Firewall Testing
Once configured, validate the firewall rules using the following methods:

### 🔹 Firewalk
Firewalk analyzes firewall rules by sending packets and checking responses.
- Install Firewalk:
  ```bash
  sudo apt-get install firewalk
  ```
- Test firewall filtering on **port 23**:
  ```bash
  firewalk -S 23 -D <target-IP>
  ```

### 🔹 ftester
Ftester simulates network traffic to assess firewall behavior.
- Install ftester:
  ```bash
  sudo apt install ftester
  ```
- Execute a test:
  ```bash
  ftest -c <source-IP>:23:<dest-IP>:23:S:TCP
  ```

### 🔹 Manual Testing
Manually test blocked and allowed ports:
- **Telnet Test** (should fail):
  ```bash
  telnet localhost 23
  ```
- **SSH Test** (should succeed):
  ```bash
  ssh user@localhost -p 22
  ```

---

## 🔥 Firewall Summary
A firewall regulates network traffic based on predefined security rules, preventing unauthorized access and mitigating cyber threats. Key functionalities include:
- Blocking specific ports to restrict services.
- Allowing essential ports for secure remote access.
- Filtering packets based on protocols, sources, and destinations.
- Enhancing system security against external intrusions.

---

## 📌 License & Contribution
- **Contributors:** _(CnRagnor)_
- **License:** MIT License
```
