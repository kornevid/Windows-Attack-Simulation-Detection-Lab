# Windows-Attack-Simulation-Detection-Lab

## Objective

This lab simulates a real-world attack scenario where a threat actor (Kali Linux) targets a Windows endpoint.

The objective was to:

- Simulate attacker behavior (initial access & reverse shell)
- Generate realistic telemetry
- Detect malicious activity using SIEM (Splunk)
- Analyze logs and identify indicators of compromise (IOCs)

### Skills Learned

- Red Team:
  - Reconnaissance (Nmap)
  - Payload generation (msfvenom)
  - Exploitation (Metasploit)

- Blue Team:
  - Log analysis (Splunk)
  - Endpoint monitoring (Sysmon)
  - Threat detection
  - Incident investigation

### Tools Used

**Red Team:**
- Kali Linux
- Metasploit
- msfvenom
- Nmap

**Blue Team:**
- Splunk SIEM
- Sysmon
- Windows Event Logs
- Splunk Forwarder

### Network Configuration

- Kali Linux: 192.168.20.20
- Windows Target: 192.168.20.10

<img width="647" height="518" alt="Screenshot 2026-04-18 201119" src="https://github.com/user-attachments/assets/89175a14-b082-46b3-a526-5db7dc74c408" />
<img width="395" height="445" alt="Screenshot 2026-04-18 201208" src="https://github.com/user-attachments/assets/b13df6bd-8210-4527-af19-b7700e5a5c17" />



**Static IP configuration AND Same subnet communication**



## Steps

1. **Endpoint Monitoring Setup (Sysmon)**

Sysmon deployed for advanced logging:

Process creation,Network connections and File activity

<img width="1008" height="788" alt="Screenshot 2026-04-18 200602" src="https://github.com/user-attachments/assets/adb48fbe-e394-4cb8-9af9-3aa681fb7999" /> .

2. **Reconaissance**

Attacker scans target:

- Host discovery
- Port scanning
- Service enumeration

  <img width="649" height="517" alt="Screenshot 2026-04-18 201612" src="https://github.com/user-attachments/assets/becd1aba-a588-47a0-8b08-d2c299e3d64e" /> .


3. **Payload Creation**

- Listing Available Payloads
  
- Reverse Shell Payload Created
  - windows/x64/meterpreter/reverse_tcp
  - Output disguised as .exe file

<img width="401" height="40" alt="Screenshot 2026-04-18 205028" src="https://github.com/user-attachments/assets/6d2ecec6-0f85-4f0e-a80f-8ebd5fdcdf7f" /> . <img width="574" height="49" alt="Screenshot 2026-04-18 205200" src="https://github.com/user-attachments/assets/983a1d85-6143-4822-bdf0-7aaf4e17b0e3" /> . <img width="806" height="254" alt="Screenshot 2026-04-18 205525" src="https://github.com/user-attachments/assets/10ad6173-84da-4c6b-bd05-624cbd8b6015" /> .

4. **Listener Setup**

- Configured:
  - LHOST: Attacker IP
  - LPORT: 4444
 
    <img width="521" height="73" alt="Screenshot 2026-04-18 205741" src="https://github.com/user-attachments/assets/4946895c-d710-4e8a-b5dd-24e06e9b9b13" /> . <img width="630" height="260" alt="Screenshot 2026-04-18 205823" src="https://github.com/user-attachments/assets/32aea249-71ca-4f01-92f8-33457e1c830d" /> . <img width="612" height="120" alt="Screenshot 2026-04-18 210228" src="https://github.com/user-attachments/assets/aa58bef7-dcd5-4376-a341-52620ee72880" /> .

Reverse TCP handler started

5. **Payload Delivery**
- Payload hosted via Python HTTP server
- Victim downloads malicious file

<img width="634" height="185" alt="Screenshot 2026-04-18 210409" src="https://github.com/user-attachments/assets/6f83bc30-5ac8-41f9-b6ce-68771ccdba06" /> . <img width="1275" height="576" alt="Screenshot 2026-04-18 210721" src="https://github.com/user-attachments/assets/7aaa5730-bfee-4db7-917c-c98e9f8a1400" /> . <img width="1017" height="542" alt="Screenshot 2026-04-18 210906" src="https://github.com/user-attachments/assets/6bd64833-49c8-400c-9583-263b262f75b8" /> . 

6. **Reverse Shell Connection**
- Target -> Attacker (Port 4444)

<img width="647" height="437" alt="Screenshot 2026-04-18 211131" src="https://github.com/user-attachments/assets/c7bfecd3-0ae6-4449-9218-9dc836661d4e" /> . <img width="629" height="62" alt="Screenshot 2026-04-18 211628" src="https://github.com/user-attachments/assets/fbd7b733-f10b-4457-9656-d077ab5206ea" /> . 

7. **Detection in Splunk**
- Suspicious process execution
- Network connection to attacker
- Windows Defender Alert

8. **Security Event Analysis**
- Windows Defender logs show:
    - Trojan detection
    - Malicious file execution
    - External communication
 
<img width="985" height="698" alt="Screenshot 2026-04-18 222001" src="https://github.com/user-attachments/assets/d10f7d61-6382-46da-b729-958bb1dd8ec1" /> .

**Indicator of compromise (IOC)**

- Malicious file : Resume3.pdf.exe
- Suspicious IP : 192.168.20.20
- Port : 4444
- Reverse shell behavior
- Defender detection : Trojan
- **The file name was updated after regenerating the payload during the weaponization stage, as the initial payload was misconfigured.* 

**Results**

- Succsessful attack simulation
- Reverse shell established
- Logs generated via Sysmin & Defender
- Detection achived in Splunk
 






