## Overview 

While a fugitive in Mexico, Mr. X remotely infiltrates the Arctic Nuclear Fusion Research Facility’s (ANFRF) lab subnet over the Interwebs. Virtually inside the facility (pivoting through a compromised system), he conducts some noisy network reconnaissance. Sadly, Mr. X is not yet very stealthy.

Unfortunately for Mr. X, the lab’s network is instrumented to capture all traffic (with full content). His activities are discovered and analyzed… by you!

Here is the packet capture containing Mr. X’s activity. As the network forensic investigator, your mission is to answer the following questions:

1. What was the IP address of Mr. X’s scanner?
2. For the FIRST port scan that Mr. X conducted, what type of port scan was it? (Note: the scan consisted of many thousands of packets.)
3. What were the IP addresses of the targets Mr. X discovered?
4. What was the MAC address of the Apple system he found?
5. What was the IP address of the Windows system he found?
6. What TCP ports were open on the Windows system? (Please list the decimal numbers from lowest to highest.)

<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/6ab4e17b-0337-4259-8ff3-5560a252e45c" />


---

## Solution

We can use Network Miner in this case also and it will much easier you can try it out, but I will stick with Wireshark.  

## 1. What was the IP address of Mr. X’s scanner?
Answer: 10.42.42.253

- After scrolling in the .pcap and opening the conversations, The IP 10.42.42.253 seems to be the attacker as he sent a large number of syn packets.

  <img width="1255" height="458" alt="image" src="https://github.com/user-attachments/assets/54d1d673-b7d7-4adb-89b4-10dd5db50807" />
  <img width="720" height="243" alt="image" src="https://github.com/user-attachments/assets/2a7d0394-f971-4376-9c86-387648dc4664" />

---

## 2. For the FIRST port scan that Mr. X conducted, what type of port scan was it? (Note: the scan consisted of many thousands of packets.)
Answer: TCP Full CONNECT Scan

```bash
tcp.flags.syn ==1 && tcp.flags.ack ==1
```
- By applying the above filter, we can see how devices respond to the SYN 
  
<img width="322" height="212" alt="image" src="https://github.com/user-attachments/assets/79e3db51-ebb4-4c9a-b819-60919b53715d" />
<img width="1286" height="244" alt="image" src="https://github.com/user-attachments/assets/e734237f-0cec-42c8-9a45-049c157a09d1" />

- By following the stream of any packet, We will conclude that the full handshake is done

  <img width="1349" height="190" alt="image" src="https://github.com/user-attachments/assets/4a8e0269-68af-4cb4-8e42-cf0f283a81aa" />

---

## 3. What were the IP addresses of the targets Mr. X discovered?
Answer: (10.42.42.25) (10.42.42.50) (10.42.42.56)

- We can find this answer easily from the conversations part or we can scroll easily and find this.

---

## 4. What was the MAC address of the Apple system he found?
Answer:  00:16:cb:92:6e:dc

- By opening a packet from the three scanned devices we can see the mac address of each device and reach the Apple device easily.
  
<img width="943" height="672" alt="image" src="https://github.com/user-attachments/assets/78f9c3a3-db3d-42bc-90a7-6fdfbfd5a60b" />

---

## 5. What was the IP address of the Windows system he found?
Answer: 10.42.42.50


---

## 6. What TCP ports were open on the Windows system? (Please list the decimal numbers from lowest to highest.)
Answer: 135, 139

- After applying the previous filter from q.1 (tcp.flags.syn ==1 && tcp.flags.ack ==1), we can see the open ports which replied.

  <img width="1179" height="490" alt="image" src="https://github.com/user-attachments/assets/64c4fb34-f529-457c-b24c-9dfd534fd5b7" /> 

---
## Conclusion
