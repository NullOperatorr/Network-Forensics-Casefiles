## Overview 

After being released on bail, Ann Dercover disappears! Fortunately, investigators were carefully monitoring her network activity before she skipped town.

“We believe Ann may have communicated with her secret lover, Mr. X, before she left,” says the police chief. “The packet capture may contain clues to her whereabouts.”

You are the forensic investigator. Your mission is to figure out what Ann emailed, where she went, and recover evidence including:

1. What is Ann’s email address?
2. What is Ann’s email password?
3. What is Ann’s secret lover’s email address?
4. What two items did Ann tell her secret lover to bring?
5. What is the NAME of the attachment Ann sent to her secret lover?
6. In what CITY and COUNTRY is their rendez-vous point?

  
<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/ca39ec68-37cf-4d2b-86cb-9f8b99c22215" />

---

## Solution

## 1. What is Ann’s email address?
Answer: sneakyg33k@aol.com

- Since we are searching for Email then I will filter by SMTP to see all Email traffic.
  
<img width="1894" height="873" alt="image" src="https://github.com/user-attachments/assets/01c9a69e-ba1a-47d1-8038-c776b1863aee" />

  
---

## 2. What is Ann’s email password?
Answer: 558r00lz

- We will follow the TCP stream and as shown the password is Base64 encoded.
- On any Decoder we can see the plain Ann's Email password.

<img width="1803" height="592" alt="image" src="https://github.com/user-attachments/assets/85678daa-c7bf-4ec6-b003-69ddb334cce5" />
<img width="393" height="410" alt="image" src="https://github.com/user-attachments/assets/2d346f7e-c12c-4bfb-bf3c-704e175d4f8a" />
<img width="915" height="692" alt="image" src="https://github.com/user-attachments/assets/7e527d93-a978-4a87-819c-299f4fec75ea" />

---

## 3. What is Ann’s secret lover’s email address?
Answer: mistersecretx@aol.com


<img width="370" height="202" alt="image" src="https://github.com/user-attachments/assets/995a9c4d-82c9-495a-9b2a-da1032db2bc6" />

---

## 4. What two items did Ann tell her secret lover to bring?
Answer: Fake passport & Bathing suit

<img width="777" height="430" alt="image" src="https://github.com/user-attachments/assets/148bf0d3-96dd-4452-b8af-757dadac4ea4" />

---

## 5. What is the NAME of the attachment Ann sent to her secret lover?
Answer: secretrendezvous.docx

<img width="770" height="437" alt="image" src="https://github.com/user-attachments/assets/40760cf1-19d4-4ac8-8011-4f05e903cd84" />

---

## 6. In what CITY and COUNTRY is their rendez-vous point?
Answer: Playa del Carmen

- We will make like the previous case, first change from ASCII to RAW, and open the file

<img width="1550" height="993" alt="image" src="https://github.com/user-attachments/assets/ff0e6895-2dcc-4121-a63f-5237f3b19212" />
<img width="962" height="582" alt="image" src="https://github.com/user-attachments/assets/4acd8c18-c1ff-4f68-b619-0ff2c59bdc6e" />


---

## Conclusion

By analyzing the captured email traffic, it was possible to recover credentials, identify the sender and recipient, examine the exchanged attachment, and determine the suspects' planned rendezvous location.
