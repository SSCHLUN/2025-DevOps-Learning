# Professor Messer Notes
# Hardware Vulnerabilities 2.3
### Firmware
- The software inside of hardware.
- Vendors are the only people who can really upgrade these devices.
- Most of these companies don't really have a focus on IT security.
### End of Life
- abbreviated as EOL they stop selling a product
- may continue short term support
- EOSL is the end of that support 
- May have a premium support option
- Good indication that you should look into replacing that device
### Legacy Platforms
- Devices that run old apps and OSs that have been running for a long time.
- May be running EOL software or be at EOSL
- May need to apply extra security practices to the device manually.
- Additional policies and firewall rules can help limit who can access this specific legacy device.
# Virtualization Vulnerabilities 2.3
### Virtualization Security
- Very different from a physical device logistically
- Quantity of resources isn't static
- Many similarities in how they function to a physical device 
### VM Escape Protection
- The VM should be self contained
- Breaking out of the VM and interact with the Hypervisor
- Accessing the hyper visor would give you access to many systems at the same time and their data
- March 2017 - Pwn2Own 
	- Java script engine bug in Microsoft Edge
	- Windows kernel bug compromise OS
	- Hardware simulation bug in VMWare which allowed for access to the whole hyper visor.
### Resource Reuse
- The hyper visor manages the relationship between physical and virtual resources
- These resources can be reused between VMs
- 4 GB on machine hosts 3 VMs means that they must be sharing some of that RAM
- Data can inadvertently be written to memory in between various VMs
- This means actions on one machine can leave for risks on the other devices
# Cloud Specific Vulnerabilities 2.3 
### Security In The Cloud
- Cloud adoption is basically universal
- We put a lot of incredibly sensitive data here
- 76% of companies don't use MFA
- 63% of companies don't patch code in production 
- We rate this vulnerability scale as a CVSS many companies has a risk factor of >= 7.0 our of 10.0
### Attack the Service
- DoS attacks can hit the service provider in turn bringing down your platform.
- Authentication bypass can be on the end of the service provider.
- Directory Traversal - A common vulnerability on web based servers that allows for people to move in and out of directories they shouldn't have access to.
- Remote code execution can give people access to functions that aren't authorized to use.
### Attack the Application
- Web application attacks have increased
	- Lof4j and Spring Cloud Function are common
- XSS attacks against poor input validation
- Out of bounds writing
	- writing data to memory when you realistically shouldn't be able to.
	- SQL injections on db's connected to the same web server opens you up to SQL injections as well.
# Supply Chain Vulnerabilities 2.3
### Supply Chain Risk
- many moving part in many parts of the world.
- any attack along the way can pose a risk to the entire supply chain
### Service Providers
- You cant always protect your security posture
- Service providers often have access to internal services
- Many service providers can be used at the same time for various logistical issues
- Employ Service Provider audits to ensure they are safe
### Target the Service Provider
- Target had a large breach
- Their HVAC and cash registers were on the same open network.
- This meant access to the HVAC infected every single register in their store.
- Put malware on every cash register and were stealing credit card numbers
### Hardware Providers
- Can you trust HW providers for switches, aps, and stations
- Use a small provider base
- Strict controls over the policies and procedures.
- Security should be part of the overall design there's no one you should trust inherently.
- DHS arrested a CEO of a cisco reseller selling counterfeit cisco devices.
### Software Providers
- trust is the foundation of security
- Digital signatures should allow us to validate the sender 
- Auto updates and patches can leave us vulnerable 
- Even open source code is not immune to these changes either
- Solar Winds Orion had insecure software.
- Bundled and Digitally Signed with updates which sent it to any device that updated or used Solar Winds Orion
- Very large private and public institutions were hit.
# Misconfiguration Vulnerabilities 2.3
### Open Permissions
- Very easy for people to leave a door open
- Becoming more and more common with the use of cloud infrastructure
- June 2017 Verizon records
	- Third-party left an Amazon data repository open
	- So it is an issue of both service providers and their misconfiguration.
### Unsecured Admin Accounts
- Linux Root or Windows Admins
- Can be misconfigured
	- provides a easy to brute force password.
- Instead give a user access to run as admin
- dont allow for people to just straight up login into root
### Insecure protocols
- Some protocols aren't encrypted
	- telnet, ftp, http, imap
- Verify with a packet capture
- Use the encrypted versions instead
### Default Settings
- Every application and network has a default login
- Mirai Botnet
	- Takes advantage of default creds.
	- Takes over IoT devices
- Mirai is open source so it is used by both attackers and researchers.
### Open Ports and Services
- Services will always open ports
- usually this is managed by a firewall which prevents port access
- Firewall rulesets can be complex in large scale applications so its easy to make mistakes
# Mobile Device Vulnerabilities 2.3
### Jailbreaking and Rooting
- Mobile devices are made with a specific purpose
- Typically have obfuscated OSes
- Install custom firmware
- Uncontrolled access 
### Sideloading
- Malicious Apps can be a significant concern.
- Manage installation sources
- Sideloading circumvents that managed installation process.
	- Typically works against the MDM
	- Apps can also be installed manually using another device
### Perception
- Devices are small
- constantly connected to the internet
- So if an individual were to gain remote access to the device it can hard track down and could have really large sweeping ramifications.
# Zero Day Vulnerabilities
### Vulnerabilities
- Most applications we use have vulnerabilities
	- Just haven't been found yet
- Someone is working hard to find the next big issues
- Attackers keep these to themselves to then leverage the issues.
### Zero Day Attacks
- The vendor has no clue so there is no patch
- Zero-day-attacks are when a system is vulnerable and the attacker hits before the owner knows.
- This leaves people in a constant arms race to limit these threats and also patch them.
- CVE can let us see some of these attacks.
# Malware Overview 2.4

