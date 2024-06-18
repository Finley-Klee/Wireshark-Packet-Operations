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
<br />
<br />
- <b>Packet Filtering</b>
<p>In task 4, packet filtering principles, I learned that filters can be used both during the capture phase and at the display level. One must be careful when using capture filters because misuse of filters can result in important packets related to the incident not being captured at all, and so TryHackMe recommended to start with capturing without filters and then filtering the packet capture later in the display. There is a syntax used to write filters in Wireshark comparison and logical operators, and the filtering principles task teaches how to use that syntax. Following this instruction phase I put that knowledge to work in the packet filtering | protocol filters task.</p>
<br>
<p align="center">It started simple with the filter "ip" to find the number of Internet Protocol packets in the capture. We can see at the bottom of the page that this filter applies to 99.9% of the packets, resulting in a total of 81420 ip packets.<br/>
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/b7376a7d-6419-4fdb-bede-42c8e6a2458c" height="80%" width="80%" alt="the wireshark overview page is shown with the letters i p in the filter box."/>
  <br />
  <br />
 Next, I used the comparison operator less than to filter based upon the time to live value of ip packets and find the number of packets where the ttl is less than 10.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/e0803afd-4aea-4182-923a-0aa32c9008be" height="80%" width="80%" alt="the wireshark packet capture page with 'ip.ttl < 10' in the filter bar."/>
  <br />
  <br />
  Then I filtered by tcp port 4444 using the equal to operator.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/3f51f0d8-ec52-432d-b06b-a8f228f2bc1b" height="80%" width="80%" alt="the wireshark packet capture page with 'tcp.port == 4444' in the filter bar."/>
   <br />
  <br />
  The next filter gets slightly more complicated. I needed to use the '&&' operator to combine two filters. The first filter selects all of the http packets based upon their request method, selecting only the get requests, and the and operator further narrows that selection to those requests that had a tcp destination port of 80.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/dd4cf9a8-ce93-4871-b0cd-cf742acd32f2" height="80%" width="80%" alt="the wireshark packet capture page with 'http.request.method == GET && tcp.dstport ==80' in the filter bar."/>
<br />
<br />
Lastly, I used the knowlege that I could create a filter by selecting it in the "Display Filter Expression" menu to find the filter for DNS type A queries.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/4e49c226-9792-44eb-ab7a-b3a08a57e2c8" height="80%" width="80%" alt="Within the display filter expression window the row dns.a Address is highlighted and to othe right a section showing the options is present, ==, !=, <, etc. has the is present option selected."/>
  <br />
  <br />
  It turned out that the filter was simply dns.a, but since I didn't know that initially, I was able to find that information. As a result I was able to discover 51 DNS type A queries.
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/f3da3781-83b7-4cf9-b3a5-820057d6d048" height="80%" width="80%" alt="the wireshark packet capture page with 'dns.a' in the filter bar."/>
</p>
<br />
<br />
- <b>Advanced Filtering</b>
<p>In this last section I stretched my filtering skills by adding terms like "matches", "contains" and "string" to really refine the filter options.</p>
<br>
<p align="center">First, I searched for the http servers that contained "Microsoft" to find the Microsoft-IIS servers and added the does not equal comparison filter to exclude any that had a source port of 80. <br/>
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/4de92679-79b7-4e0d-be28-7fe4c63d2943" height="80%" width="80%" alt="At the top of the wireshark window, the filter bar is yellow and shows the filter 'http.server contains "Microsoft" && tcp.srcport != 80'"/>
  <br />
  <br />
 Then I narrowed in on only the Microsoft-IIS servers which were version 7.5 by adding a "matches" filter.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/2556dae8-e4dc-4bd2-a42b-2c132a73f8f6" height="80%" width="80%" alt="The wireshark window is shown with a green filter bar at the top containing the filters 'http.server contains "Microsoft-IIS" && http.server matches "7.5"'"/>
  <br />
  <br />
 Next, to search for any packets that used one of a number of tcp ports, I used the "in" filter and a set containing the ports to include.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/34011ed6-52ba-4502-90b0-969b1a0bdd4b" height="80%" width="80%" alt="The wireshark window with the filter 'tcp.port in {3333, 4444, 9999}' shown at the top."/>
   <br />
  <br />
  To filter only the packets with even valued time to live, I first had to convert those values into a string using the "string" filter, then match the last number to a set of even numbers.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/a12bf547-f638-4164-a59e-e98eae1dc56c" height="80%" width="80%" alt="The wireshark window with the filter 'string(ip.ttl) matches "[02468]$"' shown at the top."/>
<br />
<br />
In the last two questions I used a previously created "Checksum Control" profile. I, once again, used the "Display Filter Expression" menu to find the filter for bad checksum values.<br />
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/5cab6b11-c809-48fe-aeb8-552e5048cdd7" height="80%" width="80%" alt="The Display Filter Expression menu is shown with the TCP field name expanded and the sub field "bad checksum" highlighted. To the right of this, in the relation section, the value "is present" is highlighted."/>
  <br />
  <br />
  This allowed me to see only the packets with bad checksum values, which had a black custom highlight color associated with the Checksum Control profile.
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/c595cc27-c956-42cb-906e-cd4330757fc4" height="80%" width="80%" alt="At the top of the wireshark window, the green filter bar is seen with the filter 'tcp.checksum_bad.expert' and below that all of the packets have a black background with red font color."/>
  <br />
  <br />
  Lastly, I clicked on the bookmarked filter button to the right of the filter bar to find the number of packets with http response code 200 that also contained gif or jpeg image content.
  <img src="https://github.com/Finley-Klee/Wireshark-Packet-Operations/assets/171582741/011422d1-7e4c-4a6c-945a-2d4aacdb089a" height="80%" width="80%" alt="The wireshark window is shown with the filters '(http.response.code == 200) && (http.content_type matches "image(gif||jpeg)")' at the top."/>
</p>

