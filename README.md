# LogAnalysis-PrivilegeEscalation
BlueTeams Lab Log Analysis - Privilege Escalation retired lab
For this lab, we will be doing a lab with a file called bash history where we will be analyzing commands.
SUMMARY - [A server with sensitive data was accessed by an attacker and the files were posted on an underground forum. This data was only available to a privileged user, in this case the ‘root’ account. Responders say ‘www-data’ would be the logged in user if the server was remotely accessed, and this user doesn’t have access to the data. The developer stated that the server is hosting a PHP-based website and that proper filtering is in place to prevent php file uploads to gain malicious code execution. The bash history is provided to you but the recorded commands don’t appear to be related to the attack. Can you find what actually happened?]
First question askes what other user than root is present. daniel is the other user.
<img width="1111" height="633" alt="Screenshot 2026-08-28 192903" src="https://github.com/user-attachments/assets/75300388-f5ff-401c-b1fd-a21da29afc17" />
Question 2: What script did the attacker try to download to the server?
We see that the attacker downloaded linux-exploit-suffester.sh and output it on les.sh 
We would be looking for a file les.sh on the machine
<img width="1131" height="638" alt="Screenshot 2026-08-28 192903" src="https://github.com/user-attachments/assets/2e67ee40-d25e-4d26-9bf9-7a94c53669c5" />
3rd Question: What packet analyzer tool did the attacker try to use?
Going down the history we see that they used TCPdump which is a data-network packet analyzer.
<img width="892" height="370" alt="Screenshot 2026-08-28 192903" src="https://github.com/user-attachments/assets/c45fbd58-a562-4d78-9f70-727c4a5b4ad7" />
