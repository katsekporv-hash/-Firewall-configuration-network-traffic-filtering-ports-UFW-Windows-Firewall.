<img width="952" height="953" alt="image" src="https://github.com/user-attachments/assets/1013eddd-ae75-4ec0-ae36-ed3d52b1bdba" /># Firewall-configuration-network-traffic-filtering-ports-UFW-Windows-Firewall.

**OverView**

Firewall configuration involves setting rules to **control and protect network traffic**. It filters data based on **IP address, ports, protocols, and direction** (inbound/outbound). **Ports** act as access points for services. Tools like **UFW (Linux)** and **Windows Firewall** help manage these rules, allowing or blocking traffic to secure systems.

**Introduction**

Firewall configuration is a fundamental aspect of network security that involves setting up rules to monitor and control incoming and outgoing traffic. By filtering data based on factors such as IP addresses, ports, and protocols, firewalls help prevent unauthorized access while allowing legitimate communication. Tools like UFW on Linux and Windows Firewall make it easier to manage these security rules, ensuring systems remain protected from potential threats.

---

**Phrase 1: On Windows (Windows Firewall)**

Method 1: Using Control Panel

1. Press Windows + R
2. Type: control and press Enter
3. Go to:
System and Security → Windows Defender Firewall
4. Click:
* “Turn Windows Defender Firewall on or off” (basic settings)
* OR “Advanced settings” (for full configuration)

screenshot

<img width="1051" height="467" alt="Screenshot 2026-04-15 044653" src="https://github.com/user-attachments/assets/bad6ae5f-5c5c-4a25-98a8-f933ed2f5934" />

*for Advance settings*

<img width="1336" height="924" alt="Screenshot 2026-04-15 044908" src="https://github.com/user-attachments/assets/7c300239-dd32-4376-bf42-0118a5be78fd" />

---

**Method 2: Using Run Command (Quick Access)**

1. Press Windows + R

2. Type:

wf.msc

3. Press Enter
👉 This opens Windows Defender Firewall with Advanced Security

screenshot

<img width="1336" height="924" alt="Screenshot 2026-04-15 044908" src="https://github.com/user-attachments/assets/9c068d0f-b451-43a8-9cb8-9ae777947a7a" />

---

**Phrase 2:  Current firewall rules**

 Using GUI:
 
1. Press Win + R

2. Type:

wf.msc
3. View:
* Inbound Rules
* Outbound Rules

Screenshot Inbound rules

<img width="1915" height="1059" alt="Screenshot 2026-04-15 055309" src="https://github.com/user-attachments/assets/8b6db48f-3394-4e86-8c3e-3d1156bbd01a" />


ScreenShot Outbound Rule

<img width="1911" height="1058" alt="Screenshot 2026-04-15 055433" src="https://github.com/user-attachments/assets/0852b969-4eb5-40c6-9932-141596f21dd1" />

---

**Using Kali**

List all iptables rules:

* sudo iptables -L -n -v

ScreenShot

<img width="952" height="987" alt="Screenshot 2026-04-15 063914" src="https://github.com/user-attachments/assets/7e9251ad-f173-462d-87f4-59f4568214d0" />

---

**More readable (with line numbers):**

* sudo iptables -L --line-numbers

<img width="952" height="953" alt="Screenshot 2026-04-15 064719" src="https://github.com/user-attachments/assets/33ae5f9a-4cd8-451d-b3d4-27044576acda" />

---

