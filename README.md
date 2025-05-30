# Setup and Use a Firewall on Windows/Linux
---
##  Objective: Configure and test basic firewall rules to allow or block traffic.

##  Tools: 
-  Windows Firewall / UFW (Uncomplicated Firewall) on Linux.
-  kali linux


## 👣 step i do for set up firewall to block telnet inbound


### first just list current rules in my machine using cmd by this command
-`netsh advfirewall firewall show rule name=all` 
- ![list](images/list%20curreny%20rule%20in%20windows.png)

### without gui set up rule using cmd 
- `netsh advfirewall firewall add rule name="Block Telnet" protocol=TCP dir=in localport=23 action=block` its for block.
-  `netsh advfirewall firewall add rule name="Allow Telnet" protocol=TCP dir=in localport=23 action=allow` its for allow 


This guide explains how to block inbound Telnet connections on port 23 using Windows Firewall with Advanced Security.

---

## Steps to Block Telnet Port 23

### 1. Open Windows Firewall with Advanced Security
- Press `Win + R`, type `wf.msc`, and press **Enter** -
- Opens the Windows Defender Firewall with Advanced Security console.
- ![firewall tab](images/firewall%20first%20page.png)


### 2. Create a New Inbound Rule
- In the left pane, click **Inbound Rules**  
- In the right pane, click **New Rule...**
- ![click telnet](images/click%20inbound.png)

### 3. Select Rule Type
- Select **Port** and click **Next**


### 4. Specify Ports
- Select **TCP**  
- Choose **Specific local ports:** and enter `23`
- ![port set up](images/add%20rule.png)
- Click **Next**
- 

### 5. Choose Action
- Select **Block the connection**
- ![block](images/block%20telnet.png)  
- Click **Next**

### 6. Choose Profile
- Check all: **Domain**, **Private**, **Public**
- ![profile](images/profile.png)  
- Click **Next**

### 7. Name the Rule
- Enter a name, e.g., `Block Telnet Port 23`  
- Click **Finish**

---
## note this 
- start a listener in windows  `ncat.exe -l -p 23 -v`
- 


## Testing the Rule

- From another machine (e.g., Kali Linux), run: `telnet <target-ip> 23`
- successfull blocked
- ![blocked](images/telnet.png)

---
## testing ssh port usign linux ufw on port 22

### install uwf 
- `sudo apt install ufw`
### set up the uwf for allow you can use 
- `sudo ufw allow 22/tcp`
### set up the uwf for deny you can use
- `sudo ufw deny 22/tcp`
### start the ssh service in kali linux usign this command
- `sudo systemctl start ssh`

#### to test this you can use localhost or any remote here am use git bash
## screenshot during the test
- before deny ssh
- ![before](images/before%20beny%20ssh.png)
- after allow ssh
- ![after](images/after%20allow%20ssh.png)
