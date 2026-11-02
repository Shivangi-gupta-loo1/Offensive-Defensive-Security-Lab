# Experiment No. 4

## Firewall and IDS Setup

### Aim

To configure basic firewall rules using pfSense and enable Snort IDS to monitor network traffic and detect suspicious activity in a controlled lab environment.

### Requirements

- Kali Linux
- Metasploitable 2
- pfSense
- Oracle VirtualBox
- pfSense ISO
- Internal Network

### Theory

A **firewall** controls incoming and outgoing network traffic according to predefined rules. **pfSense** is an open-source firewall and router platform. **Snort** is an Intrusion Detection System (IDS) that monitors network traffic and generates alerts when suspicious activity is detected.

## Procedure

### Step 1: Download pfSense ISO

1. Download the **AMD64 ISO for Virtual Machines** from the official pfSense/Netgate website.
2. Extract the downloaded file if required to obtain the `.iso` file.

![pfSense Installation](images/step1-pfsense-installation.png)

### Step 2: Create pfSense Virtual Machine

1. Open **VirtualBox → New**.
2. Configure the VM with:
   - **Name:** `pfSense`
   - **Type:** `BSD`
   - **Version:** `FreeBSD (64-bit)`
   - **RAM:** `1024–2048 MB`
   - **Disk:** `10–20 GB`
3. Create the virtual machine.

![pfSense Console](images/step2-pfsense-console-ip.png)
   
### Step 3: Configure Network

1. Open **pfSense → Settings → Network**.
2. Configure two network adapters:
   - **Adapter 1 (WAN):** NAT or Bridged Adapter
   - **Adapter 2 (LAN):** Internal Network
3. Attach the downloaded **pfSense ISO** through the Storage settings.

![pfSense Dashboard](images/step3-pfsense-dashboard.png)

### Step 4: Install pfSense

1. Start the pfSense VM.
2. Select **Install pfSense** from the boot menu.
3. Accept the default options and select **Guided Disk Setup**.
4. Confirm the installation.
5. Remove the ISO and reboot the VM.

![Firewall Rule Configuration](images/step4-firewall-rule.png)

### Step 5: Configure WAN and LAN

1. After reboot, check the pfSense console.
2. Identify the **WAN** and **LAN** interfaces.
3. Configure the LAN interface with an appropriate IP address.
4. Connect Kali Linux and Metasploitable 2 to the same lab network.

![Kali Connectivity Test](images/step5-kali-connectivity-test.png)

### Step 6: Access pfSense Web Interface

1. Start Kali Linux.
2. Open a web browser.
3. Enter the **pfSense LAN IP address**.
4. Log in to the pfSense web interface.

![Snort Installation](images/step6-snort-installation.png)

### Step 7: Configure Firewall Rule

1. Go to **Firewall → Rules → LAN**.
2. Add a basic rule to allow the required lab traffic.
3. Save and apply the rule.

![Snort Interface](images/step7-snort-interface.png)

### Step 8: Install and Enable Snort

1. Go to **System → Package Manager → Available Packages**.
2. Search for **Snort** and install it.
3. Go to **Services → Snort**.
4. Configure Snort on the LAN interface.
5. Enable the required detection rules and apply the configuration.

![Nmap Scan](images/step8-nmap-scan.png)

### Step 9: Generate Test Traffic

From Kali Linux, generate test traffic toward Metasploitable 2:

ping -c 3 METASPLOITABLE_IP

Perform a test scan:

nmap -sS METASPLOITABLE_IP

Replace <METASPLOITABLE_IP> with the actual IP address assigned to Metasploitable 2.

![Snort Alerts](images/step9-snort-alerts.png)

### Step 10: Observe Snort Alerts

1. Open the Snort section in pfSense.
2. Check the generated alerts.
3. Analyze the detected network activity.

Result:
The pfSense firewall was successfully configured and Snort IDS was enabled to monitor and detect test network activity in the controlled lab environment.

Conclusion:
The experiment demonstrated the use of pfSense as a firewall to control network traffic and Snort as an IDS to monitor traffic and generate alerts for suspicious activity.
