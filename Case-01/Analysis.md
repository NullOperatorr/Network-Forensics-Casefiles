## Overview

Anarchy-R-Us, Inc. suspects that one of their employees, Ann Dercover, is really a secret agent working for their competitor. Ann has access to the company’s prize asset, the secret recipe. Security staff are worried that Ann may try to leak the company’s secret recipe.

Security staff have been monitoring Ann’s activity for some time, but haven’t found anything suspicious– until now. Today an unexpected laptop briefly appeared on the company wireless network. Staff hypothesize it may have been someone in the parking lot, because no strangers were seen in the building. Ann’s computer, (192.168.1.158) sent IMs over the wireless network to this computer. The rogue laptop disappeared shortly thereafter.

“We have a packet capture of the activity,” said security staff, “but we can’t figure out what’s going on. Can you help?”

You are the forensic investigator. Your mission is to figure out who Ann was IM-ing, what she sent, and recover evidence including:

1. What is the name of Ann’s IM buddy?
2. What was the first comment in the captured IM conversation?
3. What is the name of the file Ann transferred?
4. What is the magic number of the file you want to extract (first four bytes)?mm
5. What was the MD5sum of the file?
6. What is the secret recipe?


<p align="center">
 <img width="400" height="400" alt="Screenshot 2026-07-26 213714" src="https://github.com/user-attachments/assets/0cae2a12-0a8f-428d-8966-96d32bc30ad4" />
</p>
  
   
---

 ## Solution
 ## 1. What is the name of Ann’s IM buddy?
 Answer: Sec558user1

 As we are only searching for Ann's PC, we can filter by her own IP address

 ```bash
ip.addr==192.168.1.158
```
<img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/9ea1c22f-ebb2-49c6-aca8-1415bbaed351" />

so, now we reduced the number of packets from 240 to 68 to invetigate more easily.  

After inspecting packets:

<img width="800" height="565" alt="image" src="https://github.com/user-attachments/assets/4c9da1a8-58e3-4da0-872e-b8e4400fa497" />  
<img width="800" height="565" alt="image" src="https://github.com/user-attachments/assets/b8b0a280-d214-4c55-bd87-ec67b45e90e5" />

---

## 2. What was the first comment in the captured IM conversation?
Answer: Here's the secret recipe... I just downloaded it from the file server. Just copy to a thumb drive and you're good to go

In the same packet stream inspection we found the second answer.

<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/2436183e-da75-4326-aaba-572bad59d131" />


---

## 3. What is the name of the file Ann transferred?
Answer: recipe.docx

In the same packet stream inspection we found the third answer.

<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/323ee013-0442-44bf-bb10-5775b2af9ecf" />






