# Wireshark Lab

## Project Description


This project demonstrated how I used Wireshark to investigate network traffic data as a security analyst for a hypothetical company. The primary focus was to analyze a network packet capture file to identify source and destination IP addresses, inspect protocols used during web browsing sessions, and analyze data packets to understand the information exchanged between systems. To achieve this, I applied various filters to view specific types of traffic and used Wireshark's graphical user interface for detailed packet analysis. This hands-on experience was designed to deepen my understanding of network traffic analysis and the use of Wireshark to monitor and investigate security issues.

### Skills Learned


- Proficiency in capturing and analyzing network traffic
- Ability to inspect individual network packets to extract detailed information such as IP addresses, protocol details, and payload content
- Enhanced understanding of using packet sniffing tools for security purposes
- Learned to apply and customize display filters in Wireshark to focus on specific types of traffic such as TLS handshakes

## Procedure

### Demonstrating Filters on an Ethernet Port Capture

For my first task, the IT manager wanted me to visit a few websites and demonstrate how to create a capture file. Once created, I needed to demonstrate using various display filters to find important packet information. This task is broken down into the following steps: 
 
1. I began by clearing the browser cache. This way, I would not view any cached websites in my packet capture and would only view the most recent version of any websites from which I intended to capture packets.
![image](https://github.com/user-attachments/assets/84caa565-d76f-4959-b054-ba807d50af21)

2. Once the cache was cleared, I started a new packet capture by opening Wireshark and selecting the ethernet option, ens5. After this, I clicked on the blue shark fin in the upper left corner to capture packets.
   
     ![image](https://github.com/user-attachments/assets/e2bf70c3-b0c6-4c3f-9cca-305fd881b4db)

4. Next, I visited two websites in the browser: Google.com and http://cygwin.com (unsecured). 
Then, I returned to Wireshark and stopped the packet capture after a few seconds to avoid running out of memory on the application. I saved the capture as “task2.pcapng” for future analysis. To prevent any confusion, it is worth mentioning that I intended to save this capture as “task1.pcapng”.
![image](https://github.com/user-attachments/assets/dea9af89-9033-4140-a97b-95505c5b086f)

5. I needed to find the “Client Hello” response from the website, so I entered the display filter shown below to view only HTTPS traffic.
![image](https://github.com/user-attachments/assets/c11bed33-cf17-4655-b4b0-b9f678de502d)

    Below is another way I could have searched for this information. In this example, I filtered all the packets where a TLS handshake would be of type 1 (“Client Hello”).
![image](https://github.com/user-attachments/assets/c8b02be7-b6d1-4152-a4b1-2c7d05f489ac)


7. The next step of my task required me to demonstrate how to filter packets to view traffic only involving a specific address. I chose to only filter for Google.com. I filtered for any traffic involving Google’s IP address in the first screenshot. In the second one, I looked for any packets received from Google itself. Finally, the third screenshot demonstrates how I looked for any packets sent to Google.
![image](https://github.com/user-attachments/assets/59c1816c-6ad2-40be-8211-51ce77a1be1f)
![image](https://github.com/user-attachments/assets/572e07d3-0f5e-4dc7-a670-6a9d3f4aa139)
![image](https://github.com/user-attachments/assets/c499f85a-4985-493d-8b11-1d44203e078a)

8. 

Wireshark uses coloring rules to provide visual cues that help find packets quicker. In this example, the blue packets all contained DNS traffic, and the green packets contained TCP and HTTP/S protocol traffic. 

### Basic Packet Inspection 
For the next task, I wanted to demonstrate that I could inspect the information in captured packets. More specifically, I wanted to investigate DNS and HTTP packets. I knew that DNS uses UDP port 53 for the most part, so I began my task by entering the following display filter: <b>udp.port == 53</b>. From the list of blue packets returned, I clicked on the first one and found the information in the screenshot below. Upon further investigation, I discovered that the website queried in this piece of traffic was opensource.google.com. 

![image](https://github.com/user-attachments/assets/76ed016b-8be4-403e-90ef-8badb385f937)

Then, to check the data involved with HTTP packets, I entered the following display filter query: <b>tcp.port == 80</b>. As mentioned before, the packets shown displayed a green color. I clicked on the first packet that appeared. As seen again below, much information can be gathered from individual packets. From this packet, I learned that it had a default time-to-live value of 64 hops, its header length was 20 bytes (meaning it had no options), and its destination address was 172.21.224.2. 

![image](https://github.com/user-attachments/assets/283d65d7-7f50-4cee-9f00-cebc10cfb7ed)

### Filtering through MAC Address
My final task was to demonstrate how to select traffic sent to or from a specific ethernet MAC address. The following display filter shows I searched for any traffic related to a MAC address regardless of protocols: <b> eth.addr == 42:01:ac:15:e0:02</b>


## Summary
In this project, I demonstrated using Wireshark to capture and analyze network traffic. The tasks included creating a packet capture file featuring specific websites, applying display filters to identify relevant packet information, and inspecting individual packets to understand the protocols and other information included. This process involved filtering for TLS handshakes, DNS and HTTP packets, and analyzing traffic by IP and MAC addresses. The project highlights the practical application of Wireshark in monitoring and investigating network security events.
