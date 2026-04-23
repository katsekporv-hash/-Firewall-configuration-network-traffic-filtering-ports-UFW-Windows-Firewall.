

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

*Command:* wf.msc

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

**Phrase 3: rule to block inbound traffic on port 23 (Telnet)**

🔐 Basic Rule Structure

* A firewall rule to block inbound traffic includes:

Direction: Inbound (incoming traffic)
  
Action: Deny / Drop

Protocol: TCP or UDP

Port: Specific port number (e.g., 23)

Source (optional): IP address or “any”

*Purpose*: block inbound traffic on port 23 (Telnet)

*Command*: sudo ufw deny 23

screenshot

<img width="413" height="88" alt="Screenshot 2026-04-15 162319" src="https://github.com/user-attachments/assets/be02e86f-5f79-4312-92c1-fb33f4ec9df6" />

⚡ Key Rule Principles

✔ Use deny/drop to block traffic
✔ Specify port and protocol clearly
✔ Apply to inbound (INPUT) direction
✔ Restrict by IP if needed (more secure)
✔ Always verify rules after adding

---

**Phrase 4: Testing Firewall Rules for Network Security**

**Test Locally (on your Kali machine)**

Using Telnet:

👉 If blocked, you’ll see:

* Connection refused or
* Unable to connect

*Command:* telnet localhost 23

ScreenShot

<img width="543" height="119" alt="Screenshot 2026-04-15 212946" src="https://github.com/user-attachments/assets/e30358f6-ab6b-490c-9d84-4c5d2eb01494" />

---

**Test Remotely (from another machine)**

Replace TARGET_IP with your Kali IP:

**Command:**telnet TARGET_IP 23:

ScreenShot

<img width="356" height="71" alt="Screenshot 2026-04-15 214137" src="https://github.com/user-attachments/assets/6c033c1e-6548-4ee8-8808-66136627d41a" />

---

**Use Nmap (Recommended for testing)**

Scan port 23:

*Command:* nmap -p 23 TARGET_IP

screenshot

<img width="356" height="71" alt="Screenshot 2026-04-15 214137" src="https://github.com/user-attachments/assets/d0c9eb9c-1fe6-450c-90df-05e401354a6f" />

**How to Read Results**
* open → Port is accessible ❌ (rule not working)
* closed → Service not running
* filtered → Firewall is blocking ✅ (this is what you want)


---

**Phrase 5: Rules to Allow SSH(port 22) on Linux**

*Command:* sudo ufw allow 22

screenshot

<img width="262" height="80" alt="Screenshot 2026-04-23 073723" src="https://github.com/user-attachments/assets/f558c1e0-47ed-4d63-bb65-0c87beb09ee6" />

⚡**Quick Summary**
Allow SSH: sudo ufw allow 22
Restrict access: allow only trusted IPs
Always verify rules after adding

---

**Phrase 6: To remove the test block rule and restore your firewall to its previous state.**

*Command:* sudo ufw delete deny 23

ScreenShot

<img width="354" height="84" alt="Screenshot 2026-04-23 075153" src="https://github.com/user-attachments/assets/ebffc25f-fe57-42ac-80ad-42fe2ef8f3d5" />

---

**Phrase 7:documentation of the commands and GUI steps used for your firewall tasks**

1. Install UFW (Linux)

* sudo apt update
* sudo apt install ufw

---

2. Enable Firewall

* sudo ufw enable

---

3. List Current Rules

* sudo ufw status
* sudo ufw status verbose
* sudo ufw status numbered

---

4. Block Inbound Traffic (Test Rule – Port 23 Telnet)

* sudo ufw deny 23

---

5. Test the Rule Local test:

* telnet localhost 23
* nc -zv localhost 23

**Scan test**

* nmap -p 23 localhost
  
---

6. Allow SSH (Port 22)

* sudo ufw allow 22

---

7. Remove Test Rule (Restore State)

sudo ufw delete deny 23

---

**Alternative (iptables Commands)**

*Block port:*
* sudo iptables -A INPUT -p tcp --dport 23 -j DROP

---

*Remove rule:*
* sudo iptables -D INPUT -p tcp --dport 23 -j DROP

---

*List rules:*
* sudo iptables -L -n -v

---

**🖥️ Windows Firewall (GUI Steps)**
* Press Win + R
* Type: wf.msc
* Click Inbound Rules
* Click New Rule
* Select Port
* Choose TCP and enter port (e.g., 23)
* Select Block the connection
* Apply to all profiles
* Name the rule and finish


**⚡ Summary**
* Installed and enabled firewall
* Listed rules
* Blocked port 23 (Telnet)
* Tested rule (telnet, netcat, nmap)
* Allowed SSH (port 22)
* Removed test rule

---

**Phrase 7:Summary of how firewal filters traffic**

A firewall filters traffic by **examining network data and applying predefined rules** to decide whether to allow or block it. It checks key factors such as **IP address (source/destination), port number, protocol (TCP/UDP), and traffic direction (inbound/outbound)**.

If the traffic matches an **allowed rule**, it passes through; if it matches a **deny rule or looks suspicious**, it is blocked. This process helps protect systems by preventing unauthorized access while allowing legitimate communication.
  
-----

