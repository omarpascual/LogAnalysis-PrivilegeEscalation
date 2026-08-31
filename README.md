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
Question 3: What packet analyzer tool did the attacker try to use?
Going down the history we see that they used TCPdump which is a data-network packet analyzer.
<img width="892" height="370" alt="Screenshot 2026-08-28 192903" src="https://github.com/user-attachments/assets/c45fbd58-a562-4d78-9f70-727c4a5b4ad7" />
Question 4: What file extension did the attacker use to bypass the file upload filter implemented by the developer?
The file extension that was removed to bypass the developers filter is .phtml
<img width="970" height="309" alt="Screenshot 2026-08-28 192903" src="https://github.com/user-attachments/assets/82c61631-3823-44bf-98e4-0e0244486c81" />
Question 5: Based on the commands run by the attacker before removing the php shell, what misconfiguration was exploited in the ‘python’ binary to gain root-level access? 1- Reverse Shell ; 2- File Upload ; 3- File Write ; 4- SUID ; 5- Library load
First we need to look at the previous commands that was ran. It was the find command. The find command is telling us to find anything under the root directory "/" but only look at files "-type f" that are owned by root "-user root" with -perm which means permissions and looking for -4000. The -4000 is saying to only include files with the set uid bit.
If any files are found with this command then the user would be able to execute that file as root because root is the owner of that such file
<img width="956" height="310" alt="Screenshot 2026-08-28 192903" src="https://github.com/user-attachments/assets/56329313-61fa-42c8-98ce-23cb48702412" />
