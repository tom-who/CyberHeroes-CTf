# CyberHeroes-CTf
A step by step walk through for the CyberHeroes CTF on Tryhackme\

# Link: https://tryhackme.com/room/cyberheroes

---

### Enumeration

Lets begin with nmap, a popular enumeration tool!

more here: https://www.kali.org/tools/nmap/ *Nmap scans a machine to discover live services that are running, these services are sometimes vulnerable*

Command: nmap <machine_ip> -sV -sC -p- (We use -sV to determine the service version of the services running on the open ports and we use -p- to scan all ports, because by default nmap only scans 1000 ports, we can change it to scan all 65,000 using -p-)

Anways! Lets look at our results

![image](https://github.com/traveller404/CyberHeroes-CTf/assets/92340426/7c5ab531-06f8-48af-a5c6-5f0d4f0fe411)

We see that port 22 and 80 are running, port 80, is always a webserver, so if port 80 is running, we can visit the website the machine is running by going to a browser and typing in the machine IP address

Going to this webserver it is a website for White Hat hackers and you can either request their services or join them, the most important page is probably the login page
On the login page it is a basic password and username query. Trying some manual enumeration, which is just guessing some common usernames and passwords like admin this is the reply we get

![image](https://github.com/traveller404/CyberHeroes-CTf/assets/92340426/2be9cfa7-2ee0-4a9b-8cd7-a66dc3cf5ad2)

Inspecting the source code reveals something very insecure though, looking through it, we find a function named "function.authenticate" 

![image](https://github.com/traveller404/CyberHeroes-CTf/assets/92340426/7b2c5694-4d4b-46bc-820b-404dec4e99d2)

We see that in the function, there is code saying that if the username promt is = "h3ck3rBoi" and that the password is = "54321@terceSrepuS" reversed we should be able to get access

Hope this helps!!!
