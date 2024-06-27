DISPLAY FILTERS
--
tcp.port== 21 ## ftp traffic

tcp.port== 22 ##ssh traffic

tcp.port== 443##https traffic

ip.dst== 172.20.10.8 ##filter with 172.20.10.8 being the destination ip address

ip.src== 172.20.10.8 ##filter with 172.20.10.8 being the source ip address.

ip.addr== 172.20.10.8 ##provide traffic with 172.20.10.8 ip address.

ip addr== 172.20.10.8 && tcp.port 443 ##172.20.10.8 traffic and https

tcp.port== 443 or tcp.port== 80 ##filter on https or http

tcp.dstport== 80 ## traffic on http being the destination port/service 

tcp.srcport== 443 ##traffic on https being the source port

tcp.port !=80 ##exclude http traffic

tcp.port== 443 and !(arp && ftp)

Hack to get user or account name in wireshark:

filter for dhcp, nbns(netbios network service ) or bootp(also dhcp).

HTTP FILTER
--

HTTP.REQUEST.METHOD== "GET"

HTTP.REQUEST.METHOD== "HEAD"

HTTP.REQUEST.METHOD== "POST"

HTTP.FILE_DATA CONTAINS "PASS"

HTTP.FILE_DATA CONTAINS "UNAME" - TO CHECK FOR USERFIELD IN HTTP TRAFFIC

HTTP.USER_AGENT CONTAINS "MOZILLA"

HTTP.FILE_DATA CONTAINS "HTML" ## YOU CAN COPY TO A FILE TO MAKE A TEMPLATE OF THAT WEBSITE

NMAP SCAN WIRESHARK
--
DURING A NMAP SCAN IN WIRESHARK, IF A STEALTHY SCAN OR SYN SCAN IS PERFORMED, IT DOESNT MAKE A FULL TCP HANDSHAKE, ATTACKER SENDS SYN PACKET, TARGET RESPONDS WITH SYN,ACK AND THE ATTACKER STOPS RESPONDING. IF THE TARGET PORT RESPONDS WITH A SYN/ACK, IT MEANS THE PORT IS OPEN. 

IN THE CONVERSATIONS TAB, UNDER BYTES, 5 MEANS THE PORT IS OPEN, 2 MEANS IT IS CLOSED, 1 MEANS FILTERED

