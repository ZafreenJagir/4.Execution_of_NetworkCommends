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
## PROGRAM
CLIENT.PY

```
import socket
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
   c,addr=s.accept()
   print("Connection from",addr)
   try:
      hostname=c.recv(1024).decode().strip()
      if hostname:
         try:
            response=str(ping(hostname,verbose=False))
            c.send(response.encode())
         except Exception as e:
            c.send("Ping failed: {}".format(e).encode())
      else:
               c.send("Hostname not provided".encode())
   except Exception as e:
     print("Error:",e)
   finally:
     c.close() 
#s.close()            
```



SERVER.PY


```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
   while True:
      ip=input("Enter the website you want ti Ping:")
      s.send(ip.encode())
      response=s.recv(1024).decode()
      if response:
         print("Ping Result:",response)
      else:
         print("No response frm server.")
except Exception as e:
   print("Error:",e)
finally:
   s.close()

```



## Output
CLIENT.PY

![Screenshot 2024-04-27 185019](https://github.com/ZafreenJagir/4.Execution_of_NetworkCommends/assets/144870573/93927203-9d10-4d69-b9c6-fc7ade595e90)



SERVER.PY



![Screenshot 2024-04-27 185034](https://github.com/ZafreenJagir/4.Execution_of_NetworkCommends/assets/144870573/be41d11c-7177-4c5b-a696-d1175c987555)

## Result
Thus Execution of Network commands Performed 
