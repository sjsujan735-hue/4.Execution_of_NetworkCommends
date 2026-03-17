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

## Program::
## SERVER:
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```
## CLIENT:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
## Output
## SERVER:
<img width="1204" height="233" alt="image" src="https://github.com/user-attachments/assets/45972d25-c766-4914-9ac6-f64693700520" />



## CLIENT:

<img width="1217" height="271" alt="image" src="https://github.com/user-attachments/assets/544f1a61-d927-4569-9b4b-4fc5dedf12cc" />


tracert
<img width="1089" height="415" alt="Screenshot 2026-03-15 112340" src="https://github.com/user-attachments/assets/a3e66078-5cdd-4061-b604-5ef61520829b" />

ipconfig
<img width="1044" height="716" alt="Screenshot 2026-03-15 112359" src="https://github.com/user-attachments/assets/ddf9e6d6-1b1d-40fc-8108-7f2c955a87c1" />

nslookup
<img width="478" height="648" alt="Screenshot 2026-03-15 112411" src="https://github.com/user-attachments/assets/acc089be-5cae-46be-9463-24faea9463a8" />

netstat
<img width="914" height="927" alt="Screenshot 2026-03-15 112442" src="https://github.com/user-attachments/assets/2e4f907d-77e0-435d-aff2-2088a76c59c9" />


## Result
Thus Execution of Network commands Performed 
