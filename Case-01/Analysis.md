## Overview

Anarchy-R-Us, Inc. suspects that one of their employees, Ann Dercover, is really a secret agent working for their competitor. Ann has access to the company’s prize asset, the secret recipe. Security staff are worried that Ann may try to leak the company’s secret recipe.

Security staff have been monitoring Ann’s activity for some time, but haven’t found anything suspicious– until now. Today an unexpected laptop briefly appeared on the company wireless network. Staff hypothesize it may have been someone in the parking lot, because no strangers were seen in the building. Ann’s computer, (192.168.1.158) sent IMs over the wireless network to this computer. The rogue laptop disappeared shortly thereafter.

“We have a packet capture of the activity,” said security staff, “but we can’t figure out what’s going on. Can you help?”

You are the forensic investigator. Your mission is to figure out who Ann was IM-ing, what she sent, and recover evidence including:

1. What is the name of Ann’s IM buddy?
2. What was the first comment in the captured IM conversation?
3. What is the name of the file Ann transferred?
4. What is the magic number of the file you want to extract (first four bytes)?
5. What is the secret recipe?


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


---

## 4. What is the magic number of the file you want to extract (first four bytes)?
Answer: 50 4B 03 04 14 00 06 00 (Packet 119)

There are two ways to do that:  

1- Since we know from other questions that their is a recipe.docx file so we can search for the magic byte of the .docx bytes on https://www.garykessler.net/library/file_sigs_GCK_latest.html  
then find them in the capture by the hex value so that you can verify and know the first packet where the file was seen.

<img width="974" height="350" alt="image" src="https://github.com/user-attachments/assets/b457b7a2-777a-44ed-90be-d7c0f239164e" />
<img width="1903" height="1061" alt="image" src="https://github.com/user-attachments/assets/7fd43448-6a58-443f-a417-85dcc4d1db02" />


2- As we know from the description that Ann contacted someone on the local network so we can search for LAN communication between Ann and anyone locally.

<img width="686" height="242" alt="image" src="https://github.com/user-attachments/assets/d2d47621-be20-444c-9e58-fc7a984660e6" />
<img width="1819" height="556" alt="image" src="https://github.com/user-attachments/assets/22894388-211e-4b4e-a61c-b35da8bfa1da" />
<img width="1255" height="988" alt="image" src="https://github.com/user-attachments/assets/0ec53fe9-e6f0-41bf-b010-5426017e0900" />


---




## 5. What is the secret recipe?
Answer: 

First we will change the data from ASCII to raw

<img width="1121" height="1064" alt="image" src="https://github.com/user-attachments/assets/1fb1c245-18c0-46d4-9c61-0da80879d648" />  


Second we will save it in the .docx format

<img width="1215" height="1100" alt="image" src="https://github.com/user-attachments/assets/b4ee3954-4cd5-4bfe-821b-3679f0b9f815" />

We will find the below error because we do not only saved the file alone but with another raw data so we will click yes and office we solve the corrupted data.

<img width="588" height="313" alt="image" src="https://github.com/user-attachments/assets/1c282f1f-29d4-4265-b49c-420edbf14861" />


Finally open the file and here is the recipe.

<img width="764" height="397" alt="image" src="https://github.com/user-attachments/assets/003e02ac-9313-422f-ae75-fbf17bf8514b" />




---

## Conclusion


This investigation demonstrated how packet capture analysis can be used to reconstruct user activity and recover valuable digital evidence. By examining the network traffic, it was possible to identify Ann's instant messaging conversation, recover the transferred file.













