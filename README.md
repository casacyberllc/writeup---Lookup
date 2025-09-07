# writeup - TryHackMe Lookup 


Machine includes various real world vulnerabilities

- You will do reconnaissance, scanning and enumeration to uncover hidden services and subdomains

- You will exploit different web app vulnerabilities

- You will be challenged to automate tasks to understand the power of scripting in penetration testing

 <hr />

I have
- IP address
- Knowledge that there are a lot of different points of entry on here or activities I need to accomplish
- knowing there are two flags, a regular flag and a root flag. 

<hr />


What am I doing

**Step 1**
Start the machine and enter the IP address in the web browser to check out the website. 
Nothing seems to be coming up. Not exactly sure why. 

Lets try using `wget` to see if it can return the headers with the general outline of the page 

I used wget and got the following results

<img width="590" height="161" alt="image" src="https://github.com/user-attachments/assets/076804c7-7012-4dc2-8e61-6228682876f8" />

It didn't give me a page, but it did give me the site name I believe which is http://lookup.thm. We're going to write down this website for our notes. 

Let's try using `wget` on this website we found to see if anything gets returned 

<img width="591" height="92" alt="image" src="https://github.com/user-attachments/assets/b383db45-12a1-4b9a-95fc-a48f173861ec" />

Looks like nothing was there. 

<hr />

No matter, let's try nmap to see what ports are open on the machine. 

I'm going to try this command to send a UDP protocol. 
`sudo nmap -sU <ipaddress>`
Let's see what I get

<img width="673" height="113" alt="image" src="https://github.com/user-attachments/assets/a2c544fe-3042-484b-82f6-28f5092bac37" />

Doesn't seem to give me much information. Let's try the following command instead. 
`nmap -PA -sN <ipaddress>` 
This command sends a TCP ACK ping and is able to avoid IDS detection. 

I get the following results and am able to see port 20 SSH client and port 80 HTTP client is open. I write these in my notes. 

<img width="629" height="195" alt="image" src="https://github.com/user-attachments/assets/431d4f07-2662-4826-8829-a202ae799b61" />

<hr />

I'm not getting anywhere with this information so far. Let's try some passive reconnoisance methods. Lets try using **whois**

I'm going to try `whois <ipaddress>`

I get the following information. I'm not sure if any of it is going to be useful for me, 

<img width="637" height="419" alt="image" src="https://github.com/user-attachments/assets/de1d8ad6-81a9-487a-aecb-e29acc301b2d" />


<hr /> 

Ok scratch all the stuff I just did with whois, I dont think I was using my nmap as effectivly as I could have. 

I used a different nmap command to get more useful information. 

`nmap -A <ip address>`

-A: Enable OS detection, version detection, script scanning, and traceroute


I found the following information:

<img width="1280" height="771" alt="image" src="https://github.com/user-attachments/assets/815abcf4-ff63-4e25-b849-e6b636af023a" />

<img width="1108" height="274" alt="image" src="https://github.com/user-attachments/assets/e807dd3e-6b5e-47eb-a5a4-f3dcc1523516" />

