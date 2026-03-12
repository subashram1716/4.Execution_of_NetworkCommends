# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
##program

client.py

```
import socket
# Create UDP socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server_address = ("127.0.0.1", 15353)

# Get domain name from user
domain = input("Enter domain name: ")

# Send request to server
client_socket.sendto(domain.encode(), server_address)

# Receive response
ip_address, server = client_socket.recvfrom(1024)

print("IP Address:", ip_address.decode())

client_socket.close()
```
server.py
```
import socket

# DNS records (simulated database)
dns_table = {
    "google.com": "142.250.190.78",
    "yahoo.com": "98.137.11.163",
    "openai.com": "104.18.12.123",
    "example.com": "93.184.216.34"
}
# Create UDP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

# Bind server to localhost and port
server_socket.bind(("127.0.0.1", 15353))

print("DNS Server running on port 5353...\n")

while True:
    # Receive domain request from client
    message, client_address = server_socket.recvfrom(1024)
    domain = message.decode()
    print("Request received for:", domain)
    # Check DNS table
    ip = dns_table.get(domain, "Domain not found")
    # Send response back to client
    server_socket.sendto(ip.encode(), client_address)
```
## Output
<img width="1919" height="1021" alt="Screenshot 2026-03-12 112917" src="https://github.com/user-attachments/assets/5de2df00-3ad3-4147-bf6d-3d1e246790a3" />

## Result
Thus Execution of Network commands Performed 
