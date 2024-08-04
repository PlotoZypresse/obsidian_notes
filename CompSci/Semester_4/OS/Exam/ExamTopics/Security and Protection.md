The security Problem
- A system is secure if all resources are used and accessed as intended. This though is unachivabel. We would be restricting so many things that computers would become unusable
- Intruders attempt to breach security of the system
- A threat is a potential security violation
- An attack is an attempt to breach security. They can be intended or accidental
- Its much easier to protect against accidental attacks than intended malicious attacks

Categories
- Breach of confidentiality
	- Unauthorized reading of data
- Breach of integrity
	- Unauthorized modification of data
- Breach of availability
	- unauthorized destruction of data
- Theft of service
	- unauthorized use of service
- Denial of service
	- Preventing legitimate use

System protection
- Absolute protection from attacks is impossible and or infeasible. So we use the same method as with locking a bike. We make it so hard to steal the bike that it takes to longe and/or another bike is easier to steal. We do the same with here. To protect a system we need to protect
	- The physical system must be secured against intruders
	- The network bust be secured from intruders
	- The OS must be kept secure by using the right security settings and keeping it up to date to minimize the risk of bugs that can be exploited
	- Third party applications also pose risks either through bugs or they are intended for malicious use. 
	- Another and probably the most important one is the human factor. As in almost all cases the problem sits in front of the computer. The users of the system must learn to see phishing attempts or learn waht social engineering is

Program threats
- Programms can also be threat
- Maleware
- Maleware is software that is written to exploit disable or damage systems. There are a lot of ways to do these kinds of thing
	- Trojan horse
		- Like the myth. The maleware is packaged in normal software. Maybe a person wanted to download some software but klicked on the wrong link. THe person maybe got the desired software. But inside the software  is code that will escelate its privileges to access more information
	- Spyware
		- Spyware is sometimes also delivered in form of a trojan horse. In recent years phones for example could be infected without the owner noticing through Zero day exploits. There are hole comapnies that develop spyware and sell it. A zero day exploit is a bug or vulnarbility in a system that has not been detected by the provider and can thus be exploited without anyone knowing how to portect them self. 
	- Ransomware
		- Ransomware is farily new. Ransomware is not always made to steal information but can do it in some cases. Most often ransomware encrypts the data on the machine and then demands a ransom from the owner to decrypt the data again.
- Principal of least privilege
	- Maleware thrives in enviroments where the system is sat up in a way where the user has more privilges than needed. A good way of stopping security breaches is to give every user, application or other things only as much access to things as they require. This might be a bit teadiuos. Thats why many people just give application on there phone access to everything instead of carefully selectiong what the application can access
- Code injection
	- Most software is not malicious but it can be missused intentionaly by bad actors. Code injection is almost always the result of bad programming. The simplest way to inject code is through a buffer overflow
	- Buffer overflow: Here we write more to the buffer than intended. If the code does not check this we can write into memory that was not intended for our programm. This can lead to unexpected behaviour. such as crashes or even execution of arbitrary code
- Viruses and worms
	- Viruses are fragments of code imbedded into a  legitimate program. Viruses are self replicating. They try to infect as many machines as possible throug one or multiple attack vectors. For example through the network. A popular way of infecting computers is through malicious email. Viruses require human activitiy to spread. 
	- Worms on the other hand do not require human help to spread

Cryptograhpy
We send a lot of messages over the internet today. But how do we keep the content of the message secure so that no other than the intended reciver can read the message. How do we guaranty that the intended reciver recived the message. THis is where we use encryption.
- encryption
	- The basic idea of encryption is that we encrypt the data so that only the desired reciver can decrypt it and read it. A very basic example is a ceasar cypher.
	- The basic methode for encryption is a s follows. 
		- The sender encrypts the tekst to be send with an encryption algorithm and an encryption key.
		- The encryption algoritm creates a cypher tekst that can only be deciphert with the key
		- The cypher tekst can be send over an unsecured network as no one knows how to decrypt it
		- The intended recipient can now decrypt the message with the decryption key
- Symmetric encryption
	- In symmetric encrytpion the same key is used to encrypt and decrypt the message. This obviusly brings other problems into the mix. We need to keep the key secure so that no bad actor can get access to it
- Asymmetric encryption
	- With Asymetric encryption the Encryption and decryption keys are not identical. This is obviusly much safer as a threat actor can not interfer with the key exchange like in symmetric encryption.

Protection
+ the need to protect computer systems has only become larger in recent years. Not only do we have almost all of our personal data on our computers but also almost all of our infrastrucutre runs on computers.
- Principals of Protection
	-  A key principle is of protection is the principle of least privilege. Every user process or system should only get access and privileges to the things they actually need to prevent privilage escalation. If malicious code cant get root access it will be limited in the damage it can do. So permissions should be defined adequately
	- Another important principal is COmpartmentalization. The goal is to have processes or even systems in their compartment. Why should the warehouse managment computer where employes go to look up stock have access to the same things as the finance department
