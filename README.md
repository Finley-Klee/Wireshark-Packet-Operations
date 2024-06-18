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
Then I searched for the number of IP addresses linked with Kansas City by navigating to the endpoints window, and then clicked on the IPv4 tab. I scrolled through the list focusing on the city column until I found 4 IP addresses with Kansas City listed as their location.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/306c576c-bd05-4841-8dbe-0926f4ccbfad" height="80%" width="80%" alt="the endpoints window in wireshark is shown with a list of IPv4 hosts and various data about them. The highlighted row shows the first of four hosts with IP addresses that are located in Kansas City"/>
<br />
<br />
Lastly, for this section, I stayed in the endpoints window but scrolled horizontally to find the AS Organization column. I searched for the "Blicnet" organization and discovered that it has the IP address 188.246.82.7<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/fb2eb599-fb42-49be-9357-580f8612c94c" height="80%" width="80%" alt="A highlighted row in the endpoints window showing an IP address associated with Blicnet in the AS organization column."/>
</p>
<br />
<br />
- <b>Statistics | Protocol Details</b>
<p>The next section focuses on observing trends through the IPv4 and IPv6 Statistics menus.</p>
<br>
<p align="center">First I found the most used IPv4 destination address by navigating to the IPv4 statistics menu, then to the source and destination addresses.<br/>
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/6313bda8-759d-4827-abb2-e2251c94f293" height="80%" width="80%" alt="the menu navigation from statistics to IPv4 statistics to source and destination addresses in wireshark."/>
  <br />
  <br />
  Once in the source and destination addresses window, I collapsed the source IPv4 addresses and expanded the destination IPv4 addresses. Then I sorted them by count descending so that the destination address with the most connections would be listed first.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/5fca248f-1500-4aba-aa01-1573b9fb867f" height="80%" width="80%" alt="The wireshark window shows the source and destination IPv4 addresses for all of the endpoints involved in the packet capture. The highlighted row shows the top result for destination IP address when sorted by count."/>
  <br />
  <br />
  Next, I investigated the DNS activity using the DNS menu under statistics. The DNS window shows both minimum and maximum values for each topic. I sorted the topics alphabetically and scrolled down to the service stats to find the request-response time max value.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/8dccd323-feff-4a46-8d05-83fd5931dfcb" height="80%" width="80%" alt="the DNS window of wireshark with a highlighted line for request response time."/>
   <br />
  <br />
  Finally, I used the load distribution to find the number of successful HTTP requests by rad[.]msn[.]com<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/7bb123b9-800a-40ff-baef-f53019647fcc" height="80%" width="80%" alt="various domain names are listed to the left with rad.msn.com highlighted showing 39 requests in the count column."/>
</p>

