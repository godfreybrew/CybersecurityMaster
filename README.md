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

### IAAS

Infrastructure as a Service : Rent and deployment of servers (OS), and infrastructure elements (Amazon S3, Microsoft Azure)

They give the network with the machine but you choose the confirguration.

## ISMS

Information Security Management System

An SMSI is intended to choose adapted security means to protect and keep protected sensitive assets on a defined perimeter of the company.

Based on the quality model : __PDCA__

* __PLAN__: plan security actions to undertake
	* _"I say what I do"_
	* Define parameter
	* Define policy
	* Deal with the risk and identify uncovered risks. Risk management includes 4 possible treatments for each identified risk. Acceptation - Avoidance - Transfer - Reduction
* __DO__: realize what has been planed
	* _"I do what I say"_
* __CHECK__: assess that there is no gap between what was planed and what is realized
	* _"I control what I do"_
* __ACT__: undertake corrective actions plan for gaps
	* _"I correct and improve what I did and what I said"_

# Security Network Architecture & Filtering

## DMZ

**D**eMilitarized **Z**ones are networks with more or less public accesses, added network(s) between a protected network and an external one to provide an additional layer of security

> Partition the network to confine the risk

The correct approach in filtering is : everything is forbidden, just permit the flow you know (kinda ACL).


## Firewall & Router

Partition the network: IP packets examination and able to examine until application layer.

Keeps the logs and alerts, and furtermore : User friendly interface !

About the __Router__, it is a security until Routing layer. It can filter packet headers such as :
origin address, destination address, origin service port, destination service port, bits mask.

Using ACL allows to write specific rules. But a router doesn't log traffic easily.

> If a filtering equipment needs to filter on port numbers, in which headers will it find them ?
>
> *Application Layer in the TCP-IP Model*

> To define if the crossing traffic is the beginning of a TCP connection, which header should consider an equipment of filtering ? Do you know what bit/flag must be examined in this header ?
>
> *TCP-IP header : ACK bit is set to 0, it means that the first connection to a server.*

## Intrusion Detection Systems

__Principle:__ watch traffic and events in a real-time or on differed-time to detect abnormal behaviour and attacks. Sys Admin must regularly check the logs and reports.

__Goal:__ Alert and restrict the time delay for the hacker to act.

* HIDS: Host IDS -> resources, logs, ...
	* files/folders missing, moved, modified altered
	* problems with logs (missing, altered, etc)
	* user profile modification, new User id
	* user abnormal activity (i.e. accounting who launches coding environment)
	* resources over consumption (consommation) : disk space, CPU time...
	* nightly use

* NIDS: Network IDS -> Packet analysis
	* Unexplained significant level of traffic
	* unusual ingoing or outgoing accesses with unusual sites
	* over busy networks links
	* complaining from users or from remote systems
	
	* __Passive NIDS__: watch and alert,
	* __Active NIDS__: watch and may interrupt suspected sessions. Use this way when false positive are rare.
	
__Why looking for detect intrusions ?__

Not possible to stop all intrusions (cost, complex), and difficulties to keep up to date EACH equipments. Furthermore, firewall can't see every danger.

__Two approaches :__

* _Modeling behavior_, understand a routine to detect deviating events.
* _Vunerabilities knowledge_, search for common and latest vulnerabilities usage.

__Two problems :__

* Up-to-date signature bases (exhaustivity of attacks)
* Efficiency of packets capture

## Internet Access Point

### Principles

* __Deny all__ access unless the access is proved to be needed and agreed
* __The security means must be redundant__, multiples IAP, hardrives, etc
* __Confining the risk__, the architecture of the access point have to distinguish the different security levels. It is the _onion rings_ principle (public DMZ, private DMZ, legacy systems).
* __Content analysis__, Traffic must be analyzed and logged.
* __Restrain the number of channels__ : The strength of the break is equal to the
weakest channel passing through, *The strength of the break is equal to the
weakest channel passing through*. It is very important.
* Protect your IAP against adapted threats.
* Upholding conformity to the Security Policy
* Vigilance principle : Security components must be able to help us answer the question : Are we under attack ?
* Set to production only what you may operate
* Systematic agreement before operational usage (Tests, audits, pentests)

> Give three technical actions to follow in order to protect a web server faces internet risks.
>
> Set to production only what you may operate, Systematic agreement before operational usage (Tests, audits, pentests) & Upholding conformity to the Security Policy

> In order to protect from danger coming with mobile codes describe three main content filtering priciples that may be employed
>
> {todo}

# How to etablish trust ?

## Logs & Security Qualification

### Logs

Logs permits to keep trace of activity and understand an attack.
Also it can be usefull to detect something wrong happening.

### Security Qualification

__Black box__

Audit without adding information

__Grey box__

Audit with specifics perimeter and informations

__White/Crystal box__

Acces to all informations and components (architectures, config, codes, ...) 

## Remote Accesses

### Authentification

**P**oint to **P**oint **P**rotocol allows to send data over a serial connection.

There are 2 authentification protocols :

* __PAP__ - **P**assword **A**uthentification **P**rotocol. The client sends username and pass, they may be hijacked
* __CHAP__ - **C**hallenge **H**andshake **A**uthentification **P**rotocol. The server sends a challenge to the client who ciphers it and sends it
back to the server. The server does the same ciphering of the
challenge and compare the two.  CHAP requires that both the client and server know the plaintext of the secret, although it is never sent over the network
* __TACACS__ - A auth server answering to the access server if the user has the rights.
* RADIUS
* TACACS +

## VPN

**V**irtual **P**rivate **N**etworks

VPN allows to create a virtual path between a source and a destination. Thanks to tunneling principle, each extremity is authenticated. Data are exchanged after have been ciphered. It allows to realize private networks at a very interesting cost on leaning on Internet. It works on IP from server to server or from a server to a workstation.

### IP tunneling

In IP tunnelling, every IP packet, including addressing information of its source and destination IP networks, is encapsulated within another packet format native to the transit network.

__Advantages :__ Extremities are authenticated --> Confidentiality

__Disadvantages :__ Go through a firewall

It allows to interconnect Intranets of the same company.

### VPN for nomad accesses

* Nomad asks the provider to establish a ciphered connection towards the remote server {todo explain}

* Nomad has its own VPN client software {todo explain}

### VPN client protection

To counter hijacking or malware on client VPN, install a personal firewall on the client device. {a preciser et expliquer / trouver autre solution (poly ) - slide 27}

### Implementation VPN

1. Encapsulation : the payload with a supplementary header
2. Transmission through an intermediary network
3. De-encapsulation : recovering payload

## Cryptography

To be trusted a cryptographic algorithm must be
intensely challenged

__Symmetric algorithms :__ the same key is shared between the sender and the receiver

__Asymmetric algorithms :__ Algorithms using a pair of keys : a public key and a private key

### IPsec (Internet Protocol Security)

Set of protocols using algorithms to convey securely data over IP. 
Works on the layer 3. Implemented in about 40 RFCs.

__Where is that implemented ?__

On the equipment, on modifying its kernel IP stack. May be complex
 
On the equipment but with separation of IPsec processing routines from IP routines. Ipsec code inserted bewteen layer liaison and layer network.

__Various services__

Extremities authentification (level 3, not user), data confidentiality, data integrity, protection against listening and against replay.

2 protocols using different algorithms (SHA, AES, 3DES):

__Authentification Header Protocol (AH)__ : authentification extremities & integrity
> Counter *IP spoofing* (cause need Authentification / integrity confidentiality)

__Encapsulated Security Payload (ESP)__ : hold data/headers confidentiality, extremities authenticity.
> Counter *IP Sniffing* (cause need confidentiality) & *IP spoofing* (cause need Authentification / integrity confidentiality)

#### 2 protection modes

__Transport mode__: Protect data -> encapsulation

__Tunnel mode__: Protect Original Ip header & data --> encapsulation

### Symmetric ciphering Secret keys systems

The ciphering key is identical to the deciphering key

> Each partner's network as to have : n(n-1)/2 keys

__Problems :__ Partners must agree upon the key, key must be exchanged and key must be kept secret.

#### 3DES (Data encryption Standart)

DES : 56 bits key

Triple DES : 
	
	3 distinctive keys (168 bits) : K1 --> K2 --> K3

	2 distinctive keys (168 bits) : K1 --> K2 --> K1

#### AES (Advanced Encryption Standart)

Replace DES.

128 bits block ciphring with 128, 192 or 256 bits keys.

### Asymmetric ciphering Public keys systems

Each person has his private key AND his public key.

> N actors mean N differents keys

There are different usages :

__ciphering to ensure confidentiality__

The message is ciphered with the public key of Bob. The public key of Bob is previously known by Alice. Only Bob the holder of the associated private key will be able to decipher the message.

__For signing to ensure message origin__

The sender (Alice) ciphers her message with her own private key. Only Alice is able to employed her private key. The receiver (Bob) checks the sender signature by deciphering the message with the public key of the sender (Alice). This public key is the only key able to deciphered messages that have been previously ciphered with the private key of Alice.

Everyone knowing the public key of the sender (Alice) may decipher the message and so verify the signature.

#### RSA

RSA is a kind of encryption.

RSA security depends on the difficulty to factorize big prime numbers. 
Public and private keys are function of a big prime numbers pair. 
2 big prime numbers are chosen : p & q. 
n = pq is calculated. 
Given n, it’s difficult to recover p et q (n prime numbers factorization)

**Number e is chosen with the following properties :**
e is an integer ranging between 2 and φ(n)= (p-1)(q-1)
Euler’s indicating function, it’s the number of integers inferior to n and who are prime with n
so that e and (p-1)(q-1) are mutually prime.

**Number d is calculated from e,p and q**

Numbers e AND n constitute the public key. 
Numbers d AND n constitute the private key. 

## PKI

**P**ublic **K**ey **I**nfrastructure

The problem with the Asymetric cyphering is the following : "How can I be sure that I'm sending my private message to Alice and not to some Hackers ? Is the public key the Alice one ?"

> PKI is a networked system that enables companies and users to exchange information and money safely and securely.

### Digital Certificates

**D**igital **C**ertificates are data packages that identify a person that is associated with his public key. A digital certificate is protected with asymetric cryptography and hold by a trusted authority (**C**ertificate **A**uthority).

Imagine that Alice got a digital certificate. 
So when Bob wants to send confidential informations to Alice, he can ask at a **CA** the Alice's digital certificate, compare it with the public key Alice is sending. Then he sends the encrypted message with the public key to Alice.

It is very important in Commercial transactions to make sure you are sending your informations to the right web site.

### Certificate Authority

Entity in the PKI who generates and signs the certificates. Certificates contain the public keys. The CA is the trusted third party whose signature appears on the certificate.

### Registration Authority

**R**egistration **A**uthority verifies the prospective key owner's identify and sends it to the CA to issue a certificate.
It is a kind of secretary of CA. It verifies your informations before get certified by the PKI. Different authentification modes are possible : face-to-face, sending ID card copy.

**RA** interacts with the subscribers for providing **CA** services and the **RA** is subsumed (included) in the **CA**, which takes total responsibility for all action of the **RA**.

### Other terms

**C**ertificate **R**evocation **L**ists are lists of certificates that are no longer useable. The list is frequently up-to-date and contains serial numbers of CA.

**R**ecovery **A**gent : a person who is authorized to recover lost private key.

**K**ey **E**scrow : Keeping secured copies of private keys for law enforcement purposes.

__2 Documents describe a PKI foundation :__

**C**ertificate **P**olicy: gives the rules on how to use the certificate and formalize the guarantees it offers. The authentification control level. Public document.

**C**ertificate **P**ratice **S**tatement (CPS): describes means installed by the PKI to reach guarantees as announced in the CP. Private document. Processes details on the way CA, RA and other PKI components work certificate life-cycle description, CRLs management

### LDAP repository

Employed to store CR Lists (CRL) and certicates.

__Main attacks :__
* Denial of service with overloaded traffic
* Spoof client identity
* Identity server usurpation

__ACL__ control the access and the rights specify to clients (rw)

__Several Authentification :__
* Anonymous authentification - without pass
* Root DN authentification
* Simple authentification
* Simple authentification with TLS/SSL
* Auth with Certificates exchanges

### X509 certificate

X509 is the most employed standard in PKI. This standard allows applications use as SSL, IPSec, S/MIME.

Main elements :

* Certificate Version
* Certificate Serial number
* CA signature algorithm description (ex: RSA with MD5)
* name of the CA who generate the certificate
* Validity dates
* User name
* __public Key__
* CA digital signature

### Certificate Trust Level

A PKI may define several certificate level depending on the required level of trust needed.

Differences between the trust levels frequently concern:
* level of control followed during the registering process
* the keys and certificate delivering process
* the medium employed to store private keys and certificates
* The certificate purposes (signature, ciphering …)

__Class 1 - Low level__ : link email and public key, without legal/commercial value

__Class 2 - Medium level__: Link between an identity and a public key done through the network, Common transaction : digital trade (commerce)

__Class 3 - High level__: Link between a physical identity and a public key, Certificate delivered by the PKI on a face to face process

> Give the two techniques a PKI can use to implement the revocation mechanism.

## SSL / TLS

1. Client connects to the HTTPS server
2. Server sends back its certificate
3. server asks for the client's certificate
4. Client checks server certificate
5. Client sends back its certificate
6. Client sends a pre-secret(PreMasterSecret) cyphers with the server's public key
7. Server checks client'scertificate.
8. Server calculates the secret (MasterSecret) thanks the PreMasterSecret (step 6)
	* Client & Server are going to generate the MasterSecret (with the PreMasterSecret and 2 random sequences : server_random & client_random) and the session keys.
	* MasterKey is calculated while etablishing a session and each new connection.

9. Session enabled. Server sends the first secured message