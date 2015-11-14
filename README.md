# Poaching: Hunting without Permission#

 This is the code that goes along with the paper "Poaching: Hunting without
 Permission".

 Thanks to Joff Thyer for his sample Scapy code.  Heavily used in the
 Karma tests.

 These tools are all set to take an argument on command line for interface,
 or default to an internally set interface if nothing is provided.

------------------------------------------------------------------

- option252_check.py - 
This python script uses the Scapy library to send “DHCPINFORM” broadcast messages to see if a WPAD response is returned.  This would be a response with a URL in the option 252 area of the DHCP response.

- nbns_check.py - 
This Python script uses the Scapy library to send NetBIOS Name Service broadcast messages to attempt to resolve the host “WPAD”, then another message trying to resolve a random hostname.

- llmnr_mdns_check.py - 
This Python script uses the Scapy library to send LLMNR and mDNS broadcast messages, first to try to resolve the host “WPAD”, then another message trying to resolve a random hostname.

- karma_check.py - 
This Python script uses the Scapy library to send out 802.11 Probe Request packets from multiple MAC addresses set up to look like a variety of cell phones looking for a known wifi network.  It loops through the list of MAC addresses and each one requests a unique random 16bit long SSID.   Each MAC address is set so the last 4 bits are uniform to allow for the tester to watch for the packets and any responses via “Tshark” or “TCPdump”.

Note: The "karma_check.py" scrip expects the mon-int to be "mon0".  This
is set internally and can easily be changed if the interface you plan to use
can't be "mon0" for any reason.

------------------------------------------------------------------

Other files:

- sample_wpad.dat -
This is the sample wpad.dat PAC file referenced in the paper.  

- simple_http_wpad.py -
This is a simple web server based on Python's "SimpleHTTPServer" to serve a wpad.dat with the appropriate file/stream type.

- channel_hopper.sh -
A straight forward bash script for Linux to loop through channels and run the karma_check.py script.
