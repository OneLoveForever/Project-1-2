# Project-1-2
Final
Questions 

What is WannaCry? 
WannaCry was a ransomware worm that caused a nationwide incident in 2017. It affected 200,000 computers in over 150 companies. These attacks affected major businesses, including FedEx, Honda, Nissan, and the National Health Service(NHS). This attack lasted 3 days before the kill switch was created to shut it out of the computer (Cloudflare).

How does the attack work? Why DID it work in the first place? 
The WannaCry attack worked by infecting PCs with malware without the need for social engineering. It starts by compromising the endpoint, exploits unpatched vulnerabilities, initiates rapid propagation, halts business operations, and finally extorts via Cryptocurrency (fortinet.com). This process worked because many businesses didn't follow safe practices, such as regularly updating the OS and running the latest Version of Windows. It also worked because the Shadow Brokers stole the NSA-developed exploit.

What protocol does this attack exploit? Why is this the target in the first place? The protocol that was attacked by the exploit was TCP port 445. TCP port 445 is used by SMBv1, which supports file and printer sharing and Active Directory communication. This was targeted because it directly enables SMB over IP without NetBIOS. This creates a high risk for the company when it is exposed to the internet (securityscorecard.com) 

Provide a link to the exploit code. What can you infer from the code that causes the exploit? malware/WannaCry-master/README.md. What I can infer from this code is that the exploit is caused by malformed packages that trigger a buffer overflow vulnerability in Windows SMB. This allows the remote code to be triggered without authentication. After execution, the attacker can then initiate the ransomware protocol.(Cloud.Google.com)

Where the main action call of this code? Why? 
The main action call to the code is sock.send(packet) or send(sock, buffer, size, 0). This is the main action code because it uses port 445. This way, the EternalBlue relies on the malformed SMB. I also identified this port through the network functions within the flow of the exploit. This is how the code was used to damage multiple computers.

What portion of the code actually sends the connection packet? Provide a screenshot and a written justification of how you derived that answer. 
The portion of the code that attacks the system is the Sock.connect((target, 445) sock.sendall(packet) section. I justify this by identifying how the code is used. This code clearly targets the port with the specified name and code. I would send the screenshot; however, the code I looked up for the project is highly dangerous, so unfortunately, I couldn't share it.

Lets analyze this deeper. What Windows driver does this code use that allows a computer to communicate with hardware or other connected devices?
The driver that the code uses to allow a computer to communicate with other hardware or devices is srv.sys. This driver is a part of the SMB service responsible for file sharing between systems. This is how the EthernalBlue got in. Because the driver operates in the kernel, it allows a hacker to escalate privileges to the highest level. 

What is this driver used for?
The srv.sys driver is used to manage SMB network connections within the Windows OS. It's the main source of file sharing, printer sharing, and other resources on the network. It processes the incoming request and directs the information to the correct destination. This is how WannaCry was able to get into the system through this driver. 


What detective measures can be used to prepare for this attack? One way to prepare for the attacks is by putting a network monitoring system in place for any unusual traffic over TCP port 445. Another detective measure is to initiate vulnerability scanning to scan for any vulnerabilities in the system. Last measure: dedicating a team to protect against any ongoing cybercrime. 

What are three defensive actions an organization can take to prevent similar exploits in the future? Explain your justification by quoting and providing sources. 
First defensive action organizations can take is to apply regular updates to all computers. According to Microsoft, "Customers who applied the security update, or who had Windows Defender Antivirus enabled, were protected from the attack." Second Defense action is disabling SMBv1 as it is not required in this day and age. CISA recommends this by saying "disable SMBv1 and block TCP port 445 when possible." Last defense action is to implement network segmentation and access controls. Network segmentation prevents malware from spreading across the entire organization. NIST backs this up by saying that layered security controls and restricted network access are critical for preventing ransomware attacks.
