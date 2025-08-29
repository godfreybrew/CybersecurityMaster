___

# Cybersecurity
___

# Table of content

1. [Risk Generalities](https://github.com/godfreybrew/CybersecurityMaster#risk-generalities)
	* [DICP](https://github.com/godfreybrew/CybersecurityMaster#dicp)
	* [Risk Concept](https://github.com/godfreybrew/CybersecurityMaster#risk-concepts)
	* [Sniffing](https://github.com/godfreybrew/CybersecurityMaster#sniffing)
	* [TCP spoofing](https://github.com/godfreybrew/CybersecurityMaster#tcp-spoofing)
	* [SYN flooding Attack](https://github.com/godfreybrew/CybersecurityMaster#syn-flooding-attack)
	* [DOS & DDOS](https://github.com/godfreybrew/CybersecurityMaster#dos--ddos)
	* [Botnets](https://github.com/godfreybrew/CybersecurityMaster#dos--ddos)
	* [Keyloggers](https://github.com/godfreybrew/CybersecurityMaster#keyloggers)
	* [Virus](https://github.com/godfreybrew/CybersecurityMaster#virus)
	* [Cross Site Request Forgery Attack](https://github.com/godfreybrew/CybersecurityMaster#cross-site-request-forgery-attack)
2. [Phishing & BYOD](https://github.com/godfreybrew/CybersecurityMaster#phishing--byod)
	* [Phisphing](https://github.com/godfreybrew/CybersecurityMaster#phishing)
	* [BYOD](https://github.com/godfreybrew/CybersecurityMaster#byod)
3. [Cloud Computing & ISMS](https://github.com/godfreybrew/CybersecurityMaster#cloud-computing--isms)
	* [ICMP](https://github.com/godfreybrew/CybersecurityMaster#icmp)
	* [Services](https://github.com/godfreybrew/CybersecurityMaster#services)
	* [ISMS](https://github.com/godfreybrew/CybersecurityMaster#isms)
4. [Security Network Architecture & Filtering](https://github.com/godfreybrew/CybersecurityMaster#security-network-architecture--filtering)
	* [DMZ](https://github.com/godfreybrew/CybersecurityMaster#dmz)
	* [Firewall & Router](https://github.com/godfreybrew/CybersecurityMaster#firewall--router)
	* [Intrusion Detection Systems](https://github.com/godfreybrew/CybersecurityMaster#intrusion-detection-systems)
	* [Internet Access point](https://github.com/godfreybrew/CybersecurityMaster#internet-access-point)
5. [How to etablish trust ?](https://github.com/godfreybrew/CybersecurityMaster#how-to-etablish-trust-)
	* [Logs & Security Qualification](https://github.com/godfreybrew/CybersecurityMaster#logs--security-qualification)
	* [Remote accesses](https://github.com/godfreybrew/CybersecurityMaster#remote-accesses)
	* [VPN](https://github.com/godfreybrew/CybersecurityMaster#vpn)
	* [Cryptography](https://github.com/godfreybrew/CybersecurityMaster#cryptography)
	* [PKI](https://github.com/godfreybrew/CybersecurityMaster#pki)
	* [SSL / TLS](https://github.com/godfreybrew/CybersecurityMaster#{todo})
6. [Sources](https://github.com/godfreybrew/CybersecurityMaster#sources)

	
	
# Risk Generalities

```
"Every security rule or recommendation must be accompanied by its justification
in order to not be rejected or by-passed"

Trusted networks zone => networks on which we master the security

Never use a USB key found in a car park...

Users awarness remains essential.

The strength of the break is equal to the weakest channel passing through
```

## DICP
_**D**isponibility_ : Availability

_**I**ntegrity_

_**C**onfidentiality_

_**P**roof_ : Traceability

## Risk Concepts

1. Reduce the probability to see threats become a reality

2. Restrict the associated damages

3. Allow to recover to usual functioning within satisfactory
costs and time limits.

## Sniffing
Consists to catch  a traffic image of the network.

>For the hacker, the goal is to get information to prepare the attack

/!\ If someone is sniffing, he can see in `plaintext` all the messages using telnet, http, etc...

## TCP spoofing

In TCP header, there are 6 bits to influence the TCP behavior :

URG - __ACK__ - PSH - RST - __SYN__ - FIN

![TCP header](https://github.com/godfreybrew/CybersecurityMaster/blob/master/img/tcp_header.gif)

TCP uses a Three-way handshake.

![Three-way handshake](https://github.com/godfreybrew/CybersecurityMaster/blob/master/img/3wayhs.PNG)

1. The first packet is a SYNC. The sequence number is A.
2. Answering  a SYNC-ACK packet. The sequence number is B and the acknowledgment number is (A+1).
3. Sequence number A+1 and acknowledgment number B+1

The hacker replaces his IP address by an other source address that he wants to spoof. The victim will send its answer to the spoofed source address indicated in the SYN packet sent by the hacker.
This answer SYN+ACK contains the sequence number chosen by the victim that the hacker needs to continue his attack and send data to the victim.

Then there are 2 cases : 

* TCP spoofing on the same sub-network.
By sniffing, hacker may observe victim answers even if these answers are not for his destination. The hacker will see the sequence number that the victim will propose in its answer so he will be able to construct a correct ACK packet to establish the connexion

* TCP spoofing on being externally to the victim or usurped machine sub-network. The hacker as to guess the next sequence number. This one is coded on 32 bits. 2^32 possibilities...

## SYN flooding Attack

SYN Flood attack corresponds to a client who doesn’t answer to the SYN-ACK.
The goal of the attack is to fill the queue on the server where partially
established connections are stored.

A way to counter this attack is to delete partially connections after a delay.

## DOS & DDOS
**D**enial **O**f **S**ervice & **D**istributed **D**enial **O**f **S**ervice

A DOS consits to put down a service or a system.
A DDOS is a DOS with multiples equipments.

## Botnets

__Explanation__
A bot is an single infected machine, under control by untrusted person

A _Botnet_ : a network of bots working together

A _bot-herder_ : a the bot operator (i.e. bad human)

_Command & Control server_ : the botnet brain

Botnets are using to do DDOS, spamming, steal passwords, 


__How to counter them__
* _Decapitation_ ! Separate the bots from the _Command & Control servers_. Without intructions from a server, bots can't change their code to sneak, or target a new victim.

* _Defend !_
	* Preventing infections
	* Find infected devices
	* Limit attack perimeter
	* limiting damage
	
## Keyloggers

Trojan variant intercepting keystrokes. 2 types :
* __Hardware__ - Install between the keyboard and the system. Wicked needs to gain physical access.
* __Software__ 
	* Freeware, easy to find on internet
	* Commercial, sell in US to spy family

/!\ Keyloggers can steal all confidential informations : credit cards, password, identifiers, etc...
Storage or send datas to malicious people.

__Counter-measures__

* Keyloggers remain trojan and can be fight as a virus. So keep your Anti-virus updated : Signatures basis must be keep up-to-date.
* Firewall because if the keylogger exports datas collected through the network, the firewall can detect a unusual/non-conform port used.
* Protect the physical access & Search for keyloggers around keyboard.
* Keyloggers focus on password so use tokens, digital certificate, biometric stuff, etc.
* And users awarness remains essential. __Users awarness remains essential.__ U-s-e-r-s a-w-a-r-n-e... OK you get it.


## Virus

__Vocabulary__
* Wild Virus : most common.
* Zoo Virus : old ones and in laboratories.
* False positive : wrongly detected as virus.
* False negative : undetected by anti-virus.
* Known virus : Listed by anti-virus editor.
* Unknown virus : isn't or is no more in the antivirus signatures table.
* Polymorph virus : Light modification of the code to modify the signature.

__Different virus :__

### Boot virus
Infect when the computer boots (from external drive). 
Counter-measure : BIOS setup, avoid boot from external drive.

### Excecutable virus
Propagation through excecutable file. 
Infection when the infected program is excecuted (games, utilities).

### Macro virus
Propagation through Word, Excel, Access. 
Infection when file is opened with the associated application. 
Parade : desactivate macro

### Worm
Propagation through mails in messages and attached pieces.
Use a secure mail and browser. Forbied attached mails and excecutable attachments. 

__Components to struggle virus :__

### Enduser equipment security
Secure OS, email and browser.
Apply patches, don't install unnecessary products and utilities, minimize started services.

### User awareness
Sensitization : sessions, flyers, etc.

Teach best practices to follow :
- Don't all documents,
- Care to downloading,
- Read the security charts and know the punishments.

### Antivirus
_Scanner method_ - scan signatures

_Heuristic Method_ - Look for abnormal behavior

_Generic Method_ - Have a reference (clean file) and compare others files to it. A virus modify the objects he infects.

_Behavior analisis in Sandboxes_ - Best way but expensive.

### Watch about antivirus news & Update
Updates and test. Read the news.

## Cross Site Request Forgery Attack

An attacker executes un solicited action by a client on a site thanks to `cookies`. This attack is commonly called "Sea-surfing".

*example :*

> "Consider that a user “John” browses through a legitimate website “www.example.com” and has a valid cookie on his hard disk. Meanwhile, an attacker, “Crusoe,” embeds a link to perform some delete action of “www.example.com” in an image and posts it on a site known as “www.exploit.com.” When the user John visits “www.exploit.com,” the webpage loads the image and in turns gives a delete request to “www.example.com.” When the web server receives the request, it looks for the cookie. It then finds John’s cookie, interprets this as a valid request, and performs the delete action."
> 
> *from* infosecinstitute.com

# Phishing & BYOD

## Phishing

> To find an example of phishing technique, [look here](https://github.com/godfreybrew/security/tree/master/phishing)

The link to the false web site can be displayed in an e-mail, or on a popular website.

__usurp link__
DNS spoofing, DNS cache poisoning

Approaching DNS name, example : www.go0gle.com

Link alteration : www.google.dangerous.com/

__Some steps to conduct phishing attack :__
1. Create a similar web page as an official one,
2. Listen good music (it is important), 
3. Create a mail similar to an official mail of the site,
3. Send an email to someone and try to do him click on YOUR website (the wrong one),
4. Get the identifiers and  passwords/credit cards.

__Counter Measures :__
* Buy the domain name close to yours.
* User's awarness about strange mails (from the boss, or a friend, asking to typing password or to connect)
* Inform the visiter about "nobody will ask about your password or credentials"
* Watch matching with DNS server


## BYOD

**B**ring **Y**our **O**wn **D**evice

__Risks__
* Data losses due to equipment loss/theft
* Accidental data evasion
* Phishing
* Malevolent application stealing data
* Fake Wifi point
* User spying (software tool)
* malware against smartphone banking app

__Prevention__
* Activate automatic terminal locking
* Take care of the good reputation of applications to be installed
* Assess application demand to data access
* Reset and erase content before recycling
* Allow only known applications to be installed (White List)
* Consider ciphering storage for confidential data
* Consider end-to-end ciphering to protect data transfers

# Cloud Computing & ISMS

## ICMP

Internet Control Message Protocol, usefull to debug !

A ping uses ICMP.

/!\ ICMP Packets have priority on other packets.

__Risks__:

* DOS by saturation 1 - sending to the target ICMP requests with size packets larger than expected. Ping of the Death attack.
* DOS by saturation 2 SMURF - Massive send of ICMP requests towards a host, can be distributed and using broadcast to multiply the attack. --> Forbid broadcast request from external network.
* DOS by saturation 3 SMURF - SMURF attack consists on sending an ICMP Echo Request packet to a network broadcast address. The attacker indicates as the source address in the ICMP request packet, the address of the host he wants to attack. All the hosts of the network receive the packet and answer to the sender with ICMP Echo Reply
* DOS by Redirection - Massive sends of ICMP Redirect to a routing equipment with erroneous addresses. To force the equipment to modify its routing table. The goal is to make the traffic go through a route where a sniffing element
* Packets dissimulation. Use of ICMP as a transport protocol, Any IP traffic may be included (encapsulated) within ICMP packets.

## Services

### SAAS

Software As A Service, the application is hosted in the Cloud. Access possible with a web browser.

All is included

> Examples : Google apps, paypal, stripe

### PAAS

Platforme As A Service

Middlewares where devs can deploy applications. You have YOUR application on the cloud and you can manag with only your application.

> Examples : Google App Engine (java, python, Go), Microsoft Azure (.NET, java, php), Heroku (Java, ruby)