# Homelab-PiHole
Set up and manage a personal network-wide ad blocker on a Raspberry Pi to improve network performance, enhance privacy, and gain practical experience with network management and DNS traffic monitoring.

### Skills Learned
- Set up and configured a Raspberry Pi 4 with an **Argon ONE V2 case** for improved cooling and stable operation.  
- Installed **DietPi** as a lightweight alternative to Raspbian for optimal performance.  
- Deployed **Pi-hole** and configured it as the DNS server on the home network/modem.  
- Monitored and analyzed network traffic via the **Pi-hole web interface**.  
- Added and managed custom **ad-blocking lists** to improve browsing experience and network performance.  
- Gained hands-on experience in **network management, DNS configuration, and home lab setup**.

### Network Diagram
<div style="display: flex; justify-content: center; align-items: center; flex-direction: column; gap: 10px; margin-top: 10px; margin-bottom: 30px;">
  <img src="https://github.com/user-attachments/assets/497482e5-0848-4157-89fe-67c73f5ff3c0" width="650" alt="Home Network Diagram" />
  <p style="text-align: center;">Home Network Architecture (Router → Pi-hole DNS → Devices)</p>
</div>

### Tools Used
- Hardware Setup
<div style="display: flex; gap: 20px; align-items: center;">
  <div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/31fb70c7-1a41-4860-b8db-dcc586634c84" width="250" />
    <p>Raspberry Pi 4 (Before)</p>
  </div>
  <div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/c2124c09-9c02-48eb-8525-ab09166e7477" width="250" />
    <p>Raspberry Pi 4 + Argon ONE V2 Case (After)</p>
  </div>
</div>

- Operating System

<div style="text-align: center; max-width: 400px; margin: auto;">
  <img src="https://github.com/user-attachments/assets/63c5df38-34c9-4e1e-a075-03ba670088e1" alt="DietPi Logo" style="width:200px; height:auto; margin-bottom: 10px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);" />
  <p style="font-size: 16px; line-height: 1.5; color: #333;">
    <strong>DietPi</strong> – a lightweight, Debian-based OS optimized for Raspberry Pi. Minimal, user-friendly, and efficient for running Pi-hole and other home lab services.
  </p>
</div>

## 🔧 Connecting to the Raspberry Pi via SSH

To begin the setup, connect to your Raspberry Pi remotely using **SSH** from your terminal or command prompt:

<div style="display: flex; justify-content: center; align-items: center; margin-top: 10px; margin-bottom: 20px;">
  <img width="372" height="36" alt="SSH Connection Command" src="https://github.com/user-attachments/assets/daaad7f6-2976-4a07-9ee5-382cd4d19880" />
</div>

Once connected successfully, you’ll be greeted with the **DietPi** login banner and system information overview:

<div style="display: flex; justify-content: center; align-items: center; margin-top: 10px; margin-bottom: 30px;">
  <img width="744" height="475" alt="DietPi SSH Login" src="https://github.com/user-attachments/assets/8188c2c2-0e12-4e56-b6f0-f73ba32f0fb3" />
</div>

---

## 🧠 Managing Software with DietPi-Software

DietPi comes with a powerful software installer called **`dietpi-software`**, which allows you to quickly deploy and manage various services and tools directly from a simple menu interface.

<div style="display: flex; justify-content: center; align-items: center; margin-top: 10px; margin-bottom: 30px;">
  <img width="718" height="339" alt="DietPi Software Menu" src="https://github.com/user-attachments/assets/b9500525-51b5-41ed-9494-84c6623e5d17" />
</div>

From here, you can install packages like **Pi-hole**, **Fail2Ban**, web servers, monitoring tools, and more with just a few key presses.

---

## 🧩 Installing Pi-hole (DNS & Ad-Blocking)

Within the DietPi Software menu, select **Pi-hole** to install the DNS-based ad blocker.  
DietPi handles all dependencies and service configurations automatically, making the setup process smooth and error-free.

<div style="display: flex; justify-content: center; align-items: center; margin-top: 10px; margin-bottom: 30px;">
  <img width="861" height="207" alt="Pi-hole Installation Menu" src="https://github.com/user-attachments/assets/87c68235-5d1e-43c6-94fa-5be16413dfe0" />
</div>

During installation, you’ll be prompted to select your preferred upstream DNS provider —  
I chose **Cloudflare (1.1.1.1)** for fast and privacy-focused DNS resolution.

---

## 🛡️ Adding Security with Fail2Ban

To improve security, **Fail2Ban** was also installed.  
This tool helps protect your Pi from brute-force login attempts by automatically banning suspicious IP addresses.

<div style="display: flex; justify-content: center; align-items: center; margin-top: 10px; margin-bottom: 30px;">
  <img width="805" height="27" alt="Fail2Ban Install" src="https://github.com/user-attachments/assets/2cf70b1e-583b-4ebb-aac0-437ffe399488" />
</div>

---

## ⚙️ Configuring the System – `dietpi-config`

The **`dietpi-config`** tool provides centralized configuration for network settings, system performance, and service management.

<div style="display: flex; justify-content: center; align-items: center; margin-top: 10px; margin-bottom: 30px;">
  <img width="1078" height="340" alt="DietPi Config" src="https://github.com/user-attachments/assets/56b323dc-585d-4ea8-ad2a-ae4dbfc824b5" />
</div>

Inside the **Network Options**, static IP addresses can be configured to ensure the Raspberry Pi remains reachable at the same address (e.g., `192.168.0.64`).

<div style="display: flex; justify-content: center; align-items: center; margin-top: 10px; margin-bottom: 30px;">
  <img width="1058" height="283" alt="Network Settings" src="https://github.com/user-attachments/assets/9d878dbb-b03f-49f6-968d-8424e6e74a8b" />
</div>

---

### 🧾 Summary

Most installation steps were guided through DietPi’s interactive prompts.  
The process required minimal user input — aside from selecting **Cloudflare** as the DNS provider — while DietPi handled all setup and service configurations automatically.

---
## 🌐 Accessing the Pi-hole Web Interface

After completing the installation, you can access the **Pi-hole web interface** through your browser.  
Simply enter the Raspberry Pi’s IP address (e.g. `http://192.168.0.64/admin`) in the address bar.

<div style="display: flex; justify-content: center; margin-top: 15px; margin-bottom: 25px;">
  <img width="1250" height="924" alt="Pi-hole Dashboard" src="https://github.com/user-attachments/assets/7198ff4e-2968-41fc-85f1-e9cfdbd8e2a3" />
</div>

### 🖥️ Overview of the Dashboard

Once logged in, the dashboard provides a real-time overview of your DNS activity and blocking statistics.

**Key elements displayed:**
- **Hostname:** `DietPi`
- **Status:** *Active*  
- **Query Rate:** `0.00 q/min`
- **Load:** `0.00 / 0.01 / 0.00`
- **Memory Usage:** `2.6%`
- **Menu Sections:**
  - **Main:** Dashboard · Query Log  
  - **Group Management:** Groups · Clients · Domains · Lists  
  - **DNS Control:** Disable Blocking  
  - **System:** Settings · Tools  
  - **Donate:** Support the Pi-hole project  

---

## 📋 Managing Blocklists

By navigating to the **Lists** section, you can manage which domains or trackers are blocked.  
Pi-hole allows you to subscribe to external ad-blocking lists or add your own URLs manually.

<div style="display: flex; justify-content: center; margin-top: 15px; margin-bottom: 25px;">
  <img width="1251" height="926" alt="Pi-hole Lists Management" src="https://github.com/user-attachments/assets/98782bf8-252d-47ec-a8c5-233d668f870e" />
</div>

**Available options:**
- **Add a new subscribed list**  
  - **Address (URL):** link to the blocklist  
  - **Comment:** short description of the list  
  - **Group Assignment:** assign to default or custom group  
- **Hints:**  
  - Run `pihole -g` or *Update Gravity* after modifying lists  
  - Multiple URLs can be added at once, separated by spaces or commas  
  - Icons next to each list indicate the list’s health and update status
## 🧱 Blocklist vs. Allowlist

Pi-hole decides for every DNS query whether a domain should be **resolved** (allowed) or **blocked**.  
This behavior is controlled by two types of lists: **Blocklists** and **Allowlists**.

### 🚫 Blocklist
**Domains you don’t want your devices to connect to.**

**Examples:**
- `ads.google.com`
- `tracking.facebook.net`
- `doubleclick.net`

**Behavior:**
- Pi-hole denies DNS resolution (returns `0.0.0.0` or no response).  
- Ads and trackers fail to load, improving browsing performance and privacy.

**Sources:**
- Public blocklists (e.g., StevenBlack, OISD, Energized)  
- Custom domains added manually

### ✅ Allowlist
**Domains you always want to allow, even if they appear on a blocklist.**

**Examples:**
- `cdn.cloudflare.com`  
- `youtube.com` (if some necessary content gets blocked)

**Behavior:**
- Domains are **always resolved**, regardless of blocklists.  
- Useful when legitimate services are blocked by mistake.

### ⚖️ How They Work Together
1. DNS request is made.  
2. Pi-hole checks in this order:
   - If domain is on **Allowlist** → ✅ Allow  
   - If domain is on **Blocklist** → 🚫 Block  
   - Otherwise → 🌐 Resolve normally

Once lists are added, Pi-hole automatically blocks DNS requests to any domain found on those lists — effectively preventing ads, tracking, and unwanted connections.

<div style="display: flex; justify-content: center; margin-top: 15px; margin-bottom: 25px;">
  <img width="228" height="118" alt="Pi-hole Blocked Domains" src="https://github.com/user-attachments/assets/20b25bc7-e791-4098-adba-50c2f0e380db" />
</div>

---

## 🚫 Real-World Example: Before vs. After

Below is a demonstration showing how Pi-hole filters ads in real time.  
When Pi-hole blocks a tracking or ad domain, the IP address cannot be resolved — meaning the ad simply doesn’t load.

### 🧩 Before (No Ad-Blocking)
<div style="display: flex; justify-content: center; margin-top: 10px; margin-bottom: 25px;">
  <img width="1009" height="454" alt="image" src="https://github.com/user-attachments/assets/b8d62acf-f59d-4893-9810-d426feff6cbb" />

</div>

### ✅ After (Pi-hole Active)
<div style="display: flex; justify-content: center; margin-top: 10px; margin-bottom: 25px;">
 <img width="806" height="459" alt="image" src="https://github.com/user-attachments/assets/73e6b422-e09f-4d26-9663-a3e83a99b583" />

</div>

As shown, ads and tracking elements disappear completely — reducing page load times and improving privacy.

---

### 💡 Summary

Unfortunately, the project could not be fully scaled across the entire network, as the Magenta modem does not allow manual DNS configuration.  
However, it worked successfully on devices where the DNS server can be manually set — such as the demonstration PC used for testing.

For now, the setup was completed and tested on a single computer to demonstrate the functionality.  
In the future, I plan to purchase a configurable router to gain full control over network settings, which will also be useful for upcoming projects.

Through the Pi-hole web interface, DNS-based ad blocking becomes simple and powerful.  
The dashboard provides live analytics, while the **Lists** section offers fine-grained control over what is allowed or blocked.  
With just a few configurations, the Raspberry Pi transforms into a network-wide ad filter — protecting every device in the home network.
