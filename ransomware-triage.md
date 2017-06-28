## Dealing with ransomware?
This might be somewhat useful for general triag
Revision 1.4
Distribution: public
Revision will stay the same unless major changes are added to the content

Immediate Action (Containment)
* Disconnect affected systems
* Utilise information contained within the ransomware warning to search online (using a non-affected computer)for further information. E.g if it says send a mail to “ransomware@gmail.com” do a search for this. 
* Only do what you need to do on the infected computer. Some ransomware doesn't block your computer but replaces folders and files with malicious links that take further actions on clicking (e.g. Spora)
* Don't reboot. The ransomware might encrypt further files if the computer is rebootet (e.g. Petya).
* Don't reboot/shutdown - Forensics artifacts residing in memory are likely to be lost in the case of a reboot/shutdown.
* Attempt to identify which strain of ransomware is responsible and check if a decryption tool is available:
https://id-ransomware.malwarehunterteam.com
https://www.nomoreransom.org/crypto-sheriff.php
* Image each drive and store (there might not be a file decryptor available publically now but there might be in future)
* If possible, take a memory dump
* Identify initial compromise vector
* Setup triggers based on IOCs to detect new affected systems — Usually some exe file that was downloaded. Often, the exe files containing the actual malware have been downloaded by another script (wsf, vbe, excel/word macro, javascript)
* Corporate comms to send out notification organization wide to raise awareness among user base not to click on suspicious attachments or plug in random USB drives found in the carpark into the computers
* On the fly defence to be deployed to reduce the threat surface - eg: mailflow rules in exchange
* Notify insurance company and ask what their support is for cyber-security incidents
* Consider notifying appropriate authorities (if relevant)


Mid-incident Action (Assessment & Recovery)
* Identify type and sensitivity of data which has been compromised
* All egress/ingress traffic to be SPAN’ed to a separate switch port and analysed. All other logs should be correlated and threat hunting to be performed. — Ensure that timestamps are not out of sync
* Set up IOC trigger list on alerting mechanism 
* Roll out the tape backups or whatever backups there are if a decision is made to restore
* Assume all passwords on the affected devices have been compromised and change them using a non-affected device
* Remote Access Protocol is common threat entry point. Suggest shutdown or more secure implementation measure such as two factor authentication
* In few cases, malware fails to disable windows restore mechanisms and shadowcopies, so you might be able to restore files. If you export any restored files from the system, treat them with caution and check them for infection.
* If other restore attempts do not work, attempt to recover using tools such as:
http://www.shadowexplorer.com (free)
http://www.easeus.com/ad/data-recovery-wizard.htm


* If in doubt, wipe the disk clean and reload the OS — Don’t take chances here
-----PII affected-----
* If PII is involved, consider personnel data breached - All affected tokens, passwords, etc MUST be reset or re-issued immediately
* If personnel is breached, organization should watch out for fraud or impersonation. Some level of fraud detection/control must be implemented
* Appropriate regulators to be informed (if necessary)

Post-incident Action (Long term remediation)
* Set up a proper backup strategy and test it
* Security awareness training for end users
* Segmentation of the network; this isn’t 1980
* Penetration Tests/Red Team exercise
* Incident Response planning and assessment
* On-going threat hunting
* Identification and classification of data within the organization
* Identification of technical controls and their respective effectiveness
* Utilise playbooks for response and hardening such as https://www.demisto.com/playbook-for-handling-ransomware-infections/
* Get some workable threat intelligence or at least, data from abuse.ch, alienvault, etc.

NOTE: If the data must be recovered (ie: mission critical), ensure that the systems are hardened and defences are working prior to paying the ransom; you don’t want to get blindsided by another attack the moment you pay. 

Be aware that when you pay ransom, you are supporting ransomware distribution.
