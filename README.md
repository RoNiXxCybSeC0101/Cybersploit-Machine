# Cybersploit-Machine
A Damn vulnarable Machine to try pentesting skill escalate the privilages and use the vulnarabilities to access the machine 

## Overview

The **Cybersploit Machine** is a virtual environment designed specifically for cybersecurity education and penetration testing practice. It serves as a hands-on platform where users can explore various vulnerabilities and utilize a range of security tools in a safe and controlled setting.

### Purpose

The primary goal of the Cybersploit machine is to provide learners and professionals with a realistic environment to hone their hacking skills, understand security concepts, and test their knowledge against common vulnerabilities found in real-world applications and networks.

### Features

- **Variety of Vulnerabilities**: The machine includes multiple simulated vulnerabilities, allowing users to practice techniques such as SQL injection, Cross-Site Scripting (XSS), and more.
- **Pre-installed Tools**: Users have access to essential penetration testing tools like Metasploit, Burp Suite, and Nmap, facilitating a comprehensive learning experience.
- **User-Friendly Interface**: The Cybersploit machine is designed for both beginners and experienced users, providing intuitive navigation and clear instructions.
- **Realistic Scenarios**: Engage in practical exercises that mimic real-world cyber attacks, enhancing the learning experience.

### Target Audience

The Cybersploit machine is suitable for:
- **Students** studying cybersecurity and ethical hacking.
- **Professionals** looking to sharpen their skills and stay updated with the latest security practices.
- **Educators** seeking a resource to facilitate hands-on learning in cybersecurity courses.

By providing a comprehensive platform for exploration and practice, the Cybersploit Machine aims to foster a deeper understanding of cybersecurity principles and techniques.

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Tools used](#toolsused)
- [Access SSH](#accessssh)
- [Privilage Escalation](#privelageescalation)
  

## Features
- Simulated vulnerabilities for practice.
- Various tools pre-installed for testing.
- User-friendly interface for beginners.

## Getting Started

Welcome to the Cybersploit Machine! This guide will help you set up your environment and begin your journey into ethical hacking and penetration testing.

### Prerequisites

Before you start, make sure you have the following:

- **Kali Linux**: Installed on your machine or available via a live USB.
- **Cybersploit Machine**: Downloaded and set up in a virtualization environment like VirtualBox or VMware.
- **Basic Networking Knowledge**: Familiarity with IP addresses and network configurations.

## Installation

### Step 1: Setting Up the Environment

1. **Download the Cybersploit Machine**:
   Visit the [download page](https://www.vulnhub.com/entry/cybersploit-1,506/) to get the latest version of the Cybersploit machine.

2. **Import the VM**:
   - Open your virtualization software.
   - Import the downloaded VM image into your software.

3. **Configure Network Settings**:
   - Set the network adapter to **Bridged** or **NAT** to ensure both Kali and Cybersploit can communicate.
   - Allocate at least **2GB RAM** to the VM for optimal performance.

### Step 2: Starting the Cybersploit Machine

1. Launch the Cybersploit machine in your virtualization software.

### Step 3: Starting Kali linux Machine

1. Once logged in, take a moment to familiarize yourself with the environment.
2. Open a terminal and explore the pre-installed tools and applications.

### Step 4: Begin Hacking

1. Use Kali Linux to scan and identify vulnerabilities in the Cybersploit machine.
2. Follow the guides provided to exploit vulnerabilities and practice your skills.

## Tools Used

### Netdiscover

- **Description**: Netdiscover is an active/passive address reconnaissance tool, mainly developed for those wireless networks without dhcp server, when you are wardriving. It can be also used on hub/switched networks.
- **Usage** :
  ``` bash
  netdiscover -i eth0 
![Screenshot 2024-10-19 085636](https://github.com/user-attachments/assets/bccd7530-5603-4770-8c64-84760bb8d8de)  

### Nmap

- **Description**: Nmap is a free open source network scanning tool that helps user to maps network , identify hosts , ports , version and perform security audits
-  **Usage** :
   ```bash
      sudo nmap -A <target ip>
![Screenshot 2024-10-19 085743](https://github.com/user-attachments/assets/2f0b1dde-f07b-4bc0-b950-b1d426687aa3)

i used a simple network scan command "-A" here it enable me to identify the version,traceroute and also the open ports and the version and service they are running .    

Then after finding out the open ports and in one port their is an http is running so is searched it in the browser 

![Screenshot 2024-10-19 085935](https://github.com/user-attachments/assets/cd574c15-93b0-4ec0-9d17-938a5b69fda9)

And i found out the webpage that running inside it 

![Screenshot 2024-10-19 085951](https://github.com/user-attachments/assets/f469e1a0-517a-4476-9dde-85854ee05aa5)

So we got a webapp running in the port 80 so we are going deeper into it to find out the hidden directories in it so we are using our next tool

### dirb

- **Description** : DIRB is a Web Content Scanner. It looks for existing (and/or hidden) Web Objects. It basically works by launching a dictionary based attack against a web server and analyzing the responses.
- **Usage** :
   ```bash
     dirb http://<target ip>/

![Screenshot 2024-10-19 090020](https://github.com/user-attachments/assets/ea85cb52-1958-415b-a47a-7644e4467e42)

we got something after the dirb we got the robot.txt

so we just go to the browser and edit the url like this 

![Screenshot 2024-10-19 090100](https://github.com/user-attachments/assets/0041aeab-0446-43e5-86e2-18454199e11f)

okay running the url we got the hash formated flag like text 

![Screenshot 2024-10-19 090114](https://github.com/user-attachments/assets/7158e64e-32ca-4e14-914b-07785da77709)

so we are going to use a base64 decoder to decode this text 

[direct link to Base64 page ](https://www.base64decode.org/)

![Screenshot 2024-10-19 090212](https://github.com/user-attachments/assets/f027496a-f432-4848-b745-d731cb337a1f)

we just decoded the text and the result is

![Screenshot 2024-10-19 090238](https://github.com/user-attachments/assets/5632235d-5614-42d0-a33b-fd1f8416d398)

Yess we got our first flag for the machine 

Flag1: cybersploit{youtube.com/c/cybersploit}

Yess we just completed the first half now . From now on some interesting things are going happen

## Access SSH

So while running through the webpage and exploring the html sorce code of the webpage we found out and interesting information hidden in the html sorce command : username 

![Screenshot 2024-10-19 090308](https://github.com/user-attachments/assets/e4ace1de-6535-437c-aac7-b9f38b94afe4)

We got the username yes the ssh username
SSHusername = itsskv

so on our nmap scan we identified that the port 22 ssh is open and now with this username we can establish a remote connection via ssh like this 


  - ```bash
      ssh itsskv@<targetip>

![Screenshot 2024-10-19 090401](https://github.com/user-attachments/assets/6819682f-9371-4240-8598-0d67c6c5a048)

connected via ssh and ls into it to list the files and directories

![Screenshot 2024-10-19 090926](https://github.com/user-attachments/assets/eb1f5f52-eb95-4d56-858f-692d22e69c60)

and we find out a flag2.txt and we cat it and found out that is a bunch of 010101 so we decide to decode it using

[direct link to the code beautify](https://codebeautify.org/)

![Screenshot 2024-10-19 090557](https://github.com/user-attachments/assets/68b7958d-c637-425b-be9f-582978436cac)

by using the code beautify site we decoded the file

![Screenshot 2024-10-19 090634](https://github.com/user-attachments/assets/e5f38156-d4a0-43f3-807d-e516a849816d)

and we got the second flag 

flag2:cybersploit{https:t.me/cybersploit1}

next we are going do the privilage escalation

## Privilage Escalation 

So at first we are going to check the kernal version using the command 

- ```bash
       uname -a

![Screenshot 2024-10-19 091003](https://github.com/user-attachments/assets/a9b15cd5-6f46-492d-938d-a782b6135107)

after getting vresion we then check for the exploits for the version first using searchsploit 

![Screenshot 2024-10-19 094708](https://github.com/user-attachments/assets/61a54a17-7b35-4d54-960d-6bb70b03e510)

and search the privesc exploit in exploit db

[direct link for the exploit in exploit DB](https://www.exploit-db.com/exploits/37292)

![Screenshot 2024-10-19 091212](https://github.com/user-attachments/assets/10d7b105-dd1f-482c-b000-8655c542d59f)

we got an exploit that is usefull for  the version 

![Screenshot 2024-10-19 091246](https://github.com/user-attachments/assets/c062e08a-2331-4a42-997e-029aca7be459)

then download the exploit and go to our downloads directory and cat the file using

- ```bash
     cat <exploit file>

![Screenshot 2024-10-19 092029](https://github.com/user-attachments/assets/ee58720f-6ba6-4d3d-ad5d-ba8177b9ec9a)

then i just compress it in the ssh users file like this

![Screenshot 2024-10-19 102122](https://github.com/user-attachments/assets/306c6737-752a-4280-a9f1-5547d9d101db)

so i can directly exploit it through the remote accecs

then ls it and got the file called exploit

![Screenshot 2024-10-19 102159](https://github.com/user-attachments/assets/5324292e-b717-415d-8554-dc73ea562e8b)

then i used the command

- ```bash
  
     ./exploit
     
to run the exploit and to get privilage access means root access in the system

![Screenshot 2024-10-19 102217](https://github.com/user-attachments/assets/d6c9d427-0724-44a2-873f-740f24557b79)

we can see we are now in the root directory

after getting the root access cd into the root and ls we can see the finalflag.txt

![Screenshot 2024-10-19 102257](https://github.com/user-attachments/assets/d6ceb539-5d2d-46a8-ae30-6e0fccf93f63)


hope you enjoy reading through this have  a NICE DAY !!!!!
























   



