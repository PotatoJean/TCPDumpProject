<h1>Analyze Network Traffic with TCPDump</h1>

<h2>Description</h2>
TCP dump is a popular networking utility used by IT and networking professionals worldwide to capture and analyze TCP traffic within a network.</br>
</br>
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
 <p align="center">
<img src="https://i.imgur.com/7tw448f.png" height="80%" width="80%" alt="Change mod of shell script"/>
<br />
<br />

<p align="center">
Running the execution:  <br/>
<p>To run the execution, we enter the command “./watchdog.sh”, and refresh the skyroute66.com to enable the traffic. We will get the sample output below.</p> </br>
<p align="center">
<img src="https://i.imgur.com/NrsKKvr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <p>Highlighted in (from left to right):</br>
Pink- packet number</br>
Yellow- readable date and time format</br>
Blue- source IP address</br>
Purple- destination IP address</br>
Orange- packet content in hexadecimal format</br>
Green- packet content in ASCII format</br></p>

<br />
<br />

 <p align="center">
Save the file for later: <br/>
   <p>To save the script for later use, we need to dump the captured packets into a dump file. To do that, we have to change the command inside the script by adding -w capture.pcap. Run it in the terminal using “./watchdog.sh” again, a capture.pcap file will be created.</br></p>
 <p align="center">
<img src="https://i.imgur.com/4pQHfSK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

  <p align="center">
Open the file in Wireshark:  <br/>
  
   <p> Wireshark is basically tcpdump with a user interface, it displays the packets captured in a more appealing way for the ease of users.</br></p>
   <p align="center">
<img src="https://i.imgur.com/wvXs5LB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
     <p>Wireshark can also displays the hexadecimal and ASCII format packet content in a human readable format. We can click on each piece of to display the information behind it.</br></p>
   <p align="center">
<img src="https://i.imgur.com/MI2aAMT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
    
   <p align="center"> 
Adding options(limits) for packet capture:  <br/>
     <p>To limit the seconds of packet capture, we can use the command “sudo tcpdump -#XXtttt host skyroute66.com -c 10 -w capture.pcap -G 15”. The number after -G is in the format of seconds, so -G 15 means the script will capture the packets for 15 seconds, after that the packets captured will be wiped out until new traffic is presented again.</br></p>
     <p align="center">
<img src="https://i.imgur.com/VXnVFnD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
        <p>The other option is -C, which limits the byte size of the dump file. Let’s say we do -C 1, what we are trying to do is limiting the dump file to be under 1 million byte (close to a megabyte). Now, we will try the script with the following command: “sudo tcpdump -#XXtttt -w capture.pcap -C 1” (host and number of packet are removed to generate more traffic).</br></p>
     <p align="center">
<img src="https://i.imgur.com/1rhNJ72.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
       <p>On the left, new pcap files are created after we execute the script. As highlighted in yellow, we can see that each pcap file is approximately a million byte each. Once the size is surpassed, a new pcap file will be created.</br></p>
<br />
<p>We can combine both options together as follows, “sudo tcpdump -#XXtttt host skyroute66.com -w capture.pcap -C 1  -G 600”. This will capture the packets for 10 minutes and put them into individual pcap files that is under a million bytes.</br></p>
<br />
<br />
<p align="center">
What if you want more options?:  <br/>
 <p>Moving on, if the options mentioned above do not satisfy your needs. TCPdump also comes with expressions, advanced version of options to extract information from a packet. Let’s create a new shell script named “advanced.sh” and insert the command below: br>
sudo tcpdump -#XXtttt 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x47455420' -w advanced.pcap</br>
  -this command catches all the tcp traffic for a GET operation in stores them into advanced.pcap file
</br></p>
 <br />
 <p align="center">
<img src="https://i.imgur.com/XpYpHNX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>To simulate the tcp traffic with GET operation, we will submit the link below on recipepuppy.com.</br></p>
<br />
<p align="center">
<img src="https://i.imgur.com/47gSeqp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>If we open the advanced.pcap file in Wireshark, we can see that only one packet is captured and it is a GET operation.</br></p>
<br />
<p align="center">
<img src="https://i.imgur.com/5Vq5Fxo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<br />

<p>That's all for this project, thanks for reading this far. If you wish to read a more detailed explaination regarding this project, check out the documentation below:</br></p>
[Documentation in Google Docs](https://docs.google.com/document/d/1GVlrx7c03vUXn6UAFxx7FCCVUQibGFbpjqL4QeZ32tM/edit?usp=sharing)


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
