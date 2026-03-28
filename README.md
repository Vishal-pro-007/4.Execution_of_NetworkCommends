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

##Program:
Server:
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

Client.py:
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

Server:
<img width="750" height="234" alt="4A" src="https://github.com/user-attachments/assets/47536c24-0780-4e49-b19d-1175c59ceb58" />

Client:
<img width="750" height="179" alt="4B" src="https://github.com/user-attachments/assets/e5d99903-2650-4012-a017-f40e90542103" />

Netstat:
<img width="463" height="518" alt="4C" src="https://github.com/user-attachments/assets/9f307f3b-5b77-4fda-a888-7f0ad5e3fd39" />

Ipconfig:
<img width="467" height="347" alt="4D" src="https://github.com/user-attachments/assets/802fe6fd-c0a8-44e7-932e-aa98e76a9f01" />

nslookup:
<img width="389" height="290" alt="4E" src="https://github.com/user-attachments/assets/680982e9-d257-417d-b7f1-a9e04c047010" />

traceroute:
<img width="732" height="315" alt="4F" src="https://github.com/user-attachments/assets/f632d2d9-50c9-4f9d-ab83-d74498bd0372" />

tcp dump:
<img width="745" height="457" alt="4G" src="https://github.com/user-attachments/assets/3be13822-b3ec-4aa4-9ba2-fc095ac05a83" />




## Result
Thus Execution of Network commands Performed 
