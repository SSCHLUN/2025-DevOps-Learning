# Professor Messer Notes
# Buffer Overflows 2.3
- Overwriting a buffer of memory
- Fairly complex as failure rides between crashing apps all together or not getting the specific expected output. 
- Stopped by bounds checking
- When variables are being written into memory excess bytes in previous variables can over flow when the values in a previous variable exceed whats allowed. Ie If a hacker were to try and have some application run and get saved to memory they could have a 9byte variable that over flows its 9th byte into variable 2. That extra byte chnages how the permissions run for both variables A and B due to elevated permissions.
# Race Condition 2.3
- On occasion having two different things happen at the same time can leave room for vulnerabilities in software.
- TOCTOU(Time of Check to Time of Use Attack)
	- In the time between the system check for a certain value on a variable and the actual use of that variable if the system doesn't re-check before the use of the variable than there's no way to know if that value is being changed somewhere in between those two points in time.
- In circumstances where two seperate entities are making changes to a system and their is potential for this to happen simultaneously we can create race conditions. If we had 2 people trying to make money between bank account and additions to one bank account happen instantly but the withdraws from the preceding account doesn't happen you can create a race condition. Both parties will see the initialized value but if we pull money from one account and add it to the other account twice in one instance we can end up moving values excessively from one point to another. This can leave you with larger total sums of value than the initial total sum and misrepresent the true values on everyone's end.
# Malicious Updates 2.3
- Keeping software up to date can sometimes have malicious code embedded in these updates.
- Back ups before major software updates is very important.
### Downloading and Updating
- Validate the source of the download of the site.
- Check the applications dev site before going through with any update that seems non mandatory.
- Check to see if there are Digital Signatures from the applications source most OSs wont even let you download non-signed applications.
### Automatic Updates
- The app is updating itself
- Relatively trustworthy as it had to check for its own signature
- SolarWinds Orion had a supply chain attack.
- Many points of infrastructural software can be used by a single company make sure that the protection is strong on each weak link.
# Operating System Vulnerabilities 2.3
### Operating Systems 
- The foundation of the computing platform.
- OSes are universal so everyone has one which means vulnerabilities here are wide sweeping
- More code means more opportunities for a security issue.
- The vulnerabilities already exist.
### A Month of OS Updates
- Normal windows update month happen on the second Tuesday of each month
- Most companies align with this pattern especially if they utilize windows systems.
- After this patch users begin to test and deploy these updates across their machines.
- After this Microsoft will do rolling security updates for all of these vulnerabilities until the next patch Tuesday.
### Best practices
- Always be planning for that update.
- Monthly / On Demand Updates
- May be worth investing into a test if in enterprise scale organizations.
- Many patches that require restarts can mess with unsaved data.
- BACK UPS prevent these unstable patches from causing more damage.
# SQL Injection 2.3
- Code injection is pushing your own code into a data stream
- Applications should follow some specific protocol with its interactions to INPUTS and OUTPUTS.
- HTML, SQL, SML, LDAP, etc. all fall under this larger umbrella of typical issues.
### SQL Injection
-  most common dbms language
- Allows a user to put their own sql requests into an existing applications.
- Can often be executed in a web browser.
### Building a SQL Injection
- an example of website code
	- "SELECT * FROM users WHERE name = '+ username'"
	- first level is "SELECT * FROM users WHERE name = '(SOME KNOWN USERNAME)' "
	- second level is "SELECT * FROM users WHERE name = '(SOME KNOWN USERNAME)' OR '1' = '1'  "
- This 1 = 1 returns true so it would give all data available in the Data Base
# Cross Site Scripting 2.3



