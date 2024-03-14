# Must use tools
#Linpeas
#Winpeas

Allowed TOOLS checked:  
BloodHound  
SharpHound  
PowerShell Empire
Powerview  
Rubeus  
evil-winrm 
Crackmapexec  
Mimikatz    
https://github.com/AonCyberLabs/Windows-Exploit-Suggester  
https://pentestbook.six2dez.com/recon/public-info-gathering  
https://github.com/six2dez/OSCP-Human-Guide  

# OSCP
1.
Scanning:
enum.py IP  
reconmultiple.py IP IP IP  
nmap -p 445 -vv --script=smb-vuln-cve2009-3103.nse,smb-vuln-ms06-025.nse,smb-vuln-ms07-029.nse,smb-vuln-ms08-067.nse,smb-vuln-ms10-054.nse,smb-vuln-ms10-061.nse,smb-vuln-ms17-010.nse 10.10.10.10  
nmap -sV -sT -p445 --script vuln <ip>
nmap -sV -sT -p445 --script safe <ip>
nmap -sV -sT -p445 --script "vuln and safe" <ip>

File upload:
python2 -m SimpleHTTPServer ---80 Spins up a webserver in the directory you are located on port 80.  
python3 -m http.server --- 80 Spins up a python version 3.X web server in the directory you are located on port 80.  

#Privelage Escalation:
  ## Windows Privilege Escalation Guides:
Fuzzysecurity Windows Privilege Escalation Fundamentals: Shout out to fuzzysec for taking the time to write this because this is an amazing guide that will help you understand Privilege escalation techniques in Windows. http://www.fuzzysecurity.com/tutorials/16.html    
Pwnwiki Windows Privilege Escalation Commands: http://pwnwiki.io/#!privesc/windows/index.md    
Absolomb’s Security Blog: Windows Privilege Escalation Guide https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/    
Pentest.blog: Windows Privilege Escalation Methods for Pentesters https://pentest.blog/windows-privilege-escalation-methods-for-pentesters/    
PayloadAllTheThings: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md  
SharpAllTheThings: https://github.com/N7WEra/SharpAllTheThings  
LOLBAS (Created by Oddvar Moe): https://lolbas-project.github.io/  

## Windows Privilege Escalation Tools:
JAWS (Created by 411Hall): A cool windows enumeration script written in PowerShell. https://github.com/411Hall/JAWS/commits?author=411Hall  
Windows Exploit Suggester Next Generation: https://github.com/bitsadmin/wesng  
Sherlock (Created by RastaMouse): Another cool PowerShell script that finds missing software patches for local privilege escalation techniques in Windows. https://github.com/rasta-mouse/Sherlock  
WinPeas: https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/winPEAS  
Watson: https://github.com/rasta-mouse/Watson  
Seatbelt: https://github.com/GhostPack/Seatbelt  
Powerless: https://github.com/M4ximuss/Powerless  
Powerview: https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon  
  
## Token Manipulation:
Rotten Potato: https://github.com/breenmachine/RottenPotatoNG  
Juicy Potato: https://github.com/ohpe/juicy-potato  

## Linux Privilege Escalation Guides:
Linux Privilege Escalation Guides: The only guide I probably ever used to help me understand privilege escalation techniques in Linux systems was from g0tmi1k post. This blog is a must that everyone should have for preparing for the OSCP in my opinion. You can find his guide here: https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/  
GTFOBins (I have to thank Ippsec for sharing this with me): Contains a curated list of Unix binaries that that have the ability to be exploited by an attacker to bypass local security restrictions on a Linux system. https://gtfobins.github.io/  

## Linux Privilege Escalation Tools:  
LinEnum: A great Linux privilege escalation checker that is still maintained by the guys at rebootuser.com. You can find there tool here: https://github.com/rebootuser/LinEnum  
Linux Exploit Suggester 2: https://github.com/jondonas/linux-exploit-suggester-2  
LinPEAS: [https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS]   

I highly recommend you take a look at Lin.Security vulnerable box created by in security.

Main Link: https://in.security/lin-security-practise-your-linux-privilege-escalation-foo/  
Backup: https://www.vulnhub.com/entry/linsecurity-1,244/ 
  
## Sudo Privelage Escalation:
  https://www.hackingarticles.in/linux-privilege-escalation-using-exploiting-sudo-rights/ 

## Offline Tools for Password Cracking:  
Hashcat: https://hashcat.net/hashcat/ Sample Hashes to test with Hashcat: https://hashcat.net/wiki/doku.php?id=example_hashes  
John the Ripper: https://www.openwall.com/john/  
Metasploit Unleashed using John the Ripper with Hashdump: https://www.offensive-security.com/metasploit-unleashed/john-ripper/   

## Online Tools for Password Cracking:  
THC Hydra: https://github.com/vanhauser-thc/thc-hydra  
Crowbar: https://github.com/galkan/crowbar  

## Wordlist generators:
Cewl: https://digi.ninja/projects/cewl.php  
Crunch: https://tools.kali.org/password-attacks/crunch  
Cupp (In Kali Linux): https://github.com/Mebus/cupp   

Tools to check the hash type:

Hash-Identifier: https://github.com/psypanda/hashID

## Tools to dump for hashes:
Mimikatz: https://github.com/gentilkiwi/mimikatz  
Mimipenguin: https://github.com/huntergregal/mimipenguin  
Pypykatz: https://github.com/skelsec/pypykatz  
  
# Spawning Ineractive shell
###Using python  

  python -c 'import pty; pty.spawn("/bin/sh")' 

###Echo

  echo 'os.system('/bin/bash')'

###sh

  /bin/sh -i 

###bash

 /bin/bash -i 

###Perl

 perl -e 'exec "/bin/sh";' 

###From within VI

 :!bash 

  
# Port Redirection and Pivoting

Depending on your scope, some of the machines may not be directly accessible. There are systems out there that are dual homed, which allow you to connect into an internal network. You will need to know some of these techniques in order to obtain access into there non-public networks:

Abatchy’s Port Forwarding Guide: https://www.abatchy.com/2017/01/port-forwarding-practical-hands-on-guide  
Windows Port Forwarding: http://woshub.com/port-forwarding-in-windows/  
SSH Tunnelling Explained: https://chamibuddhika.wordpress.com/2012/03/21/ssh-tunnelling-explained/  
Understanding Proxy Tunnels: https://www.offensive-security.com/metasploit-unleashed/proxytunnels/  
Understanding Port forwarding with Metasploit: https://www.offensive-security.com/metasploit-unleashed/portfwd/  
Explore Hidden Networks with Double Pivoting: https://pentest.blog/explore-hidden-networks-with-double-pivoting/  
0xdf hacks stuff. Pivoting and Tunnelling: https://0xdf.gitlab.io/2019/01/28/pwk-notes-tunneling-update1.html  

## Tools to help you with Port Forwarding and Pivoting:
Proxychains: https://github.com/haad/proxychains  
Proxychains-ng: https://github.com/rofl0r/proxychains-ng  
SSHuttle (Totally Recommend learning this): https://github.com/sshuttle/sshuttle  
SSHuttle Documentation: https://sshuttle.readthedocs.io/en/stable/  
Chisel https://github.com/jpillora/chisel  
Ligolo: https://github.com/sysdream/ligolo  

## Online Tunnelling Services:

Ngrok: https://ngrok.com/  
Twilo: https://www.twilio.com/  

## Vulnerable systems to practice pivoting:

Wintermute: https://www.vulnhub.com/entry/wintermute-1,239/
  
# Active Directory Attacks:
Fundamentals of Active Directory: https://www.youtube.com/watch?v=GfqsFtmJQg0&feature=emb_logo  
  
## Enumerating Active Directory:

Active Directory Enumeration with Powershell: https://www.exploit-db.com/docs/english/46990-active-directory-enumeration-with-powershell.pdf  
Active Directory Exploitation Cheat Sheet: https://github.com/S1ckB0y1337/Active-Directory-Exploitation-Cheat-Sheet#domain-enumeration  
Powersploit: https://github.com/PowerShellMafia/PowerSploit  

## Understanding Authentication protocols that Active Directory Utilizes:

NTLM Authentication: https://docs.microsoft.com/en-us/windows-server/security/kerberos/kerberos-authentication-overview  
Kerberos Authentication https://docs.microsoft.com/en-us/windows-server/security/kerberos/kerberos-authentication-overview  
Cache and Stored Credentials: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh994565(v=ws.11)  
Group Managed Service Accounts: https://adsecurity.org/?p=4367  

## Lateral Movement in Active Directory:

Paving the Way to DA: https://blog.zsec.uk/path2da-pt1  
Pass the Hash with Machine Accounts: https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/pass-the-hash-with-machine-accounts  
Overpass the hash (Payload All the things): https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Active%20Directory%20Attack.md#overpass-the-hash-pass-the-key  
Red Team Adventures Overpass the Hash: https://riccardoancarani.github.io/2019-10-04-lateral-movement-megaprimer/#overpass-the-hash  
Pass the Ticket (Silver Tickets): https://adsecurity.org/?p=2011  
Lateral Movement with DCOM: https://www.ired.team/offensive-security/lateral-movement/t1175-distributed-component-object-model  
 
## Active Directory Persistence:

Cracking Kerberos TGS Tickets Using Kerberoast: https://adsecurity.org/?p=2293  
Kerberoasting Without Mimikatz: https://www.harmj0y.net/blog/powershell/kerberoasting-without-mimikatz/  
Golden Tickets: https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/kerberos-golden-tickets  
Pass the Ticket (Golden Tickets): https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Active%20Directory%20Attack.md#pass-the-ticket-golden-tickets  
Understanding DCSync Attacks: https://attack.stealthbits.com/privilege-escalation-using-mimikatz-dcsync  

## Tools for Active Directory Lateral Movement and Persistence:

ADRecon: https://github.com/sense-of-security/ADRecon  
Kerbrute: https://github.com/ropnop/kerbrute  
Rubeus: https://github.com/GhostPack/Rubeus  
Impacket: https://github.com/SecureAuthCorp/impacket  


# CHECK:
## Pentest Cheat sheet
https://github.com/21y4d/nmapAutomator  
https://sushant747.gitbooks.io/total-oscp-guide/content/port_scanning.html  
https://johnjhacking.com/blog/the-oscp-preperation-guide-2020/  
https://scund00r.com/all/oscp/2018/02/25/passing-oscp.html  
https://www.netsecfocus.com/oscp/2021/05/06/The_Journey_to_Try_Harder-_TJnull-s_Preparation_Guide_for_PEN-200_PWK_OSCP_2.0.html#overview  

## AD cheat sheet
https://github.com/Tib3rius/Active-Directory-Exploitation-Cheat-Sheet  
Kerberos  
Mimkiz

PayloadsAllTheThings Linux Priv Esc Guide: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md  

Other sites with good information
https://defaultcredentials.com/oscp/best-active-directory-practice-for-oscp/  
https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_windows.html  
https://fareedfauzi.gitbook.io/oscp-notes/general/learning-tips 
https://parzival.sh/posts/OSCP-Notes/  
https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Fwww.offensive-security.com%2Fpwk-online%2FOSCP-Exam-Report.odt&wdOrigin=BROWSELINK  
https://johnjhacking.com/blog/the-oscp-preperation-guide-2020/  
