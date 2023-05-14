# ForensicMemoryAnalysis

<h2>Description</h2>
Performing live system forensics requires precision to avoid losing crucial evidence. In this project, industry-standard forensic recovery tools were utilized to conduct a live system memory analysis. The process involved capturing a live image of the host system's RAM using AccessData FTK imager on a Windows 10 VM, followed by an analysis of the captured memory image using Volatility on a SIFT VM. The investigation focused on the operating system's processes, registries, log files, and HASHs, among other things. Detailed methodology and findings were documented in a Microsoft Word report, including screen captures of each step taken. The report serves as complete forensic lab notes, qualifying the investigator as an expert witness in court if needed.
<br />



<h2>Environments Used </h2>

- <b>Windows 10 enterprise </b> 
- <b>SANS forensics SIFT workstation VM</b>
<h2>IMPORTANT NOTE!</h2>
For security reasons, IP addresses and other sensitive information in screenshots have been blurred out. 

<h2>Lab walk-through:</h2>

<h2>Screenshot 1:</h2>
<p align="center">
Step 1: <br/>
An IP filter was applied using Wireshark to isolate traffic from Ann's computer. The filter used was 'ip.addr==IP1 && tcp.flags.syn', where IP1 was the IP address associated with Ann's computer.
</p>
<img src="https://i.imgur.com/BpoKmnD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
- <b> This filter will display the TCP SYN packets that were transmitted from Ann's computer.</b>

<h2>Screenshot 2:</h2>
<div align="center">
  <p>Step 2:</p>
  <p>Screenshot 2 displays the TCP stream of a conversation that Ann's computer is having with another device on the network. The conversation partner's IP address has been redacted for security reasons. To access the TCP stream, the first packet was selected, and then right-clicked on it to access the 'Follow' option. From there, the 'TCP Stream' option was selected to view the entire conversation.</p>
  <img src="https://i.imgur.com/aQ2Nydl.png" height="80%" width="80%" alt="Disk Sanitization Steps" />
  <p><strong>Note:</strong> After following the TCP stream as described in the previous step, a conversation between Ann's computer and another device was captured. The content of the conversation has been analyzed and notes have been taken. Additionally, the timeline of the conversation has been noted for further investigation.</p>
</div>

<br />
<br />

<h2>Screenshot 3:</h2>
<div align="center">
  <p>Step 3:</p>
  <p>The data of the selected packet was saved in raw format by choosing the "Show data as" option and selecting "raw" from the drop-down menu.</p>
  <img src="https://i.imgur.com/VC7mbcl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p><strong>Note:</strong> The transferred file and its associated magic number have been extracted and saved in a file that contains binary data.</p>
</div>
<br />
<br />
  
<h2>Screenshot 4:</h2>
<div align="center">
  <p>Step 4:</p>
  <p>After identifying a file transfer in Wireshark, the TCP stream was analyzed by selecting the 'Follow' option and then choosing 'TCP Stream' after right-clicking on any packet in the transfer. The entire conversation was then selected, copied, and pasted into Notepad before being saved as a separate file. This file contains the full conversation between Ann's computer and the device she was communicating with during the file transfer.</p>
  <img src="https://i.imgur.com/VC7mbcl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p><strong>Note:</strong> 
By performing the previous steps, it was possible to generate a saved file containing the transferred binary data and its associated magic number. The md5 checksum of the saved file was then calculated using a suitable tool to verify its integrity and authenticity.</p>
</div>
<br />
<br />
 
<h2>Screenshot 5:</h2>
<div align="center">
  <p>Step 5:</p>
  <p>I then proceeded to upload the file to an MD5 checksum tool available on the web to perform the necessary checksum verification.</p>
  <img src="https://i.imgur.com/K8uYJFd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p><strong>Note:</strong> 
The MD5 checksum value of the file is displayed here.</p>
</div>
<br />
<br />


<h2>Conclusion</h2>
A standard intrusion detection system (IDS) would have detected the malicious behavior observed in this case through various methods. Firstly, the appearance of an unknown laptop on the company's wireless network would have triggered an alarm. Secondly, any unusual activity from Ann's computer, such as sending messages to an unfamiliar device, would have been identified and flagged by the IDS. Additionally, the network transmission of a file named "recipe.docx" would have been analyzed by the IDS. An effective IDS would have also continuously monitored the network for any signs of unusual activity or traffic patterns and alerted security personnel of potential threats. It would have detected any additional network artifacts left by the attacker, such as unusual outbound traffic or unexpected connections to external devices or servers. In summary, a competent intrusion detection system would have been able to detect and prevent this attack before any harm was caused.
