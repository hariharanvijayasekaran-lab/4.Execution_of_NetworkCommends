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

## Program
## Client.py
~~~
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    h = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(h.encode())
    if h == 'exit': break
    print(s.recv(4096).decode())

s.close()
~~~
## Server.py
~~~
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
c, _ = s.accept()

while True:
    h = c.recv(1024).decode()
    if h == 'exit': 
        print("Client disconnected.")
        break
    try: c.send(str(ping(h, count=4)).encode())
    except: c.send(b"Ping error")

c.close()
~~~
## Output
<img width="1245" height="292" alt="506486016-c6b9352d-f6ad-437c-9161-02fcc8ec757c" src="https://github.com/user-attachments/assets/d2dfd48d-78c9-46f6-8f46-0cdadaff97a1" />


## Result
Thus Execution of Network commands Performed 
