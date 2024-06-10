# Wireshark-Packet-Operations
This is a walkthrough of my work on the TryHackMe lab (https://tryhackme.com/r/room/wiresharkpacketoperations)

<h2>Description</h2>
This lab is designed to build upon the skills learned in the Wireshark basics lab. In this continuation the focus is placed on packet-level details with statistics, filters, operations, and functions.

<h2>Utilities Used</h2>

- <b>Wireshark</b> 

<h2>Environments Used </h2>

- <b>Linux Ubuntu</b>

<h2>Project walk-through:</h2>

- <b>Statistics | Summary</b>
<p>This task used various tools in the statistics menu to investigate trends in the packet capture by things such as endpoints, conversations, and protocols.</p>
<br>
<p align="center">I navigated to the resolved addresses under the statistics menu<br/>
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/15298c58-61e9-4750-a689-85aa399607e3" height="80%" width="80%" alt="the wireshark window with the drop down statistics menu highlighting the resolved addresses option"/>
  <br />
  <br />
  Within the resolved addresses I searched for bbc to find the hostname that begins with bbc, and found its IP address<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/84ca9bce-3d3c-4faf-a77e-5cca7c52a2b4" height="80%" width="80%" alt="a small wireshark window with resolved addresses at the top and bbc in the search bar with a single entry listed"/>
  <br />
  <br />
  Next, to find the number of IPv4 conversations, I navigated to the conversations window under the statistics menu. I can see from the numbers associated to the different tabs along the top that there are 435 IPv4 conversations.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/37a5dca4-16c1-4c14-b921-0e1dd53761c2" height="80%" width="80%" alt="the conversations window in wireshark is shown with a red rectangle around the number 435 which is located on the tab titled IPv4"/>
   <br />
  <br />
  The next question asks for the number of bytes transfered from the "Micro-St" MAC address, which I found by navigating to the conversations window, and then enabling name resolution so that the MAC addresses associated to known manufacturers would have the manufacturer's name displayed in place of their unique identifier.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/e72e84e3-eb35-459b-93d5-eb2039c8eade" height="80%" width="80%" alt="the wireshark endpoints window shows a list of endpoints listed by their MAC address. The line with a Micro-St MAC address is highlighted and a red rectangle surrounds the number of bytes which reads 7474k"/>
<br />
<br />
Step Four: <br />
  <img src="" height="80%" width="80%" alt="image four"/>
</p>
<br />
<br />
- <b>Section Name</b>
<p>Description</p>
<br>
<p align="center">Step One: <br/>
  <img src="" height="80%" width="80%" alt="image one"/>
  <br />
  <br />
  Step Two: <br />
  <img src="" height="80%" width="80%" alt="image two"/>
  <br />
  <br />
  Step Three: <br />
  <img src="" height="80%" width="80%" alt="image three"/>
   <br />
  <br />
  Step Four: <br />
  <img src="" height="80%" width="80%" alt="image four"/>
   <br />
  <br />
  Step Five: <br />
  <img src="" height="80%" width="80%" alt="image five"/>
</p>
