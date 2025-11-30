**Install Wireshark:**

sudo apt update

sudo apt install wireshark -y



**Allow non root users to capture packets:**

sudo dpkg-reconfigure wireshark-common

sudo usermod -aG wireshark $USER



**Verify Installation:**

wireshark --version





Display Filters:

SYN Flood:  tcp.flags.syn == 1 \&\& tcp.flags.ack == 0 

SYN/ACK:  tcp.flags.syn == 1 \&\& tcp.flags.ack == 1

ICMP Flood:  icmp.type == 8

UDP Flood: udp



