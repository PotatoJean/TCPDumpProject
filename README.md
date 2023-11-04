<h1>Analyze Network Traffic with TCPDump</h1>

<h2>Description</h2>
TCP dump is a popular networking utility used by IT and networking professionals worldwide to capture and analyze TCP traffic within a network.

Goal of Project: to create a script to monitor the traffic of a particular website, analyze the traffic coming in and out between that particular website and your workstation.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Wireshark</b>
- <b>Linux Terminal</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Create a shell script file in vs code with the name watchdog.sh: <br/>
<p>
-enter the following command: sudo tcpdump -#XXtttt host skyroute66.com -c10<br/>
-this command is used to capture 10 packets from skyroute66.com with readable date and time format arranged properly.<br/>
-the shell script is not executable at first (evident in the screenshot below)<br/>
-it is only after we change the modification with the command “chmod +x watchdog.sh”, it becomes executable afterwards (watchdog.sh turns green)<br/>
 </p> <br/>
<img src="https://i.imgur.com/7tw448f.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />
Running the execution:  <br/>
<p>To run the execution, we enter the command “./watchdog.sh”, and refresh the skyroute66.com to enable the traffic. We will get the sample output below.</p> </br>
<img src="https://i.imgur.com/NrsKKvr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
