# 4.Execution_of_NetworkCommands
## NAME : A K PREETHI
## REGISTER NO :212223230156
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

## PROGRAM:
## CLIENT
import socket 

from pythonping import ping

s = socket.socket()

s.bind(('localhost', 8000))

s.listen(5)

while True:

    c, addr = s.accept()
    
    print("Connection from", addr)
    
    try:
    
        hostname = c.recv(1024).decode().strip()
        
        if hostname:
        
            try:
            
                response = str(ping(hostname, verbose=False))
                
                c.send(response.encode())
                
            except Exception as e:
            
                c.send("Ping failed: {}".format(e).encode())
                
        else:
        
            c.send("Hostname not provided".encode())
            
    except Exception as e:
    
        print("Error:", e)
        
    finally:
    
        c.close()
## SERVER
import socket

s = socket.socket()

s.connect(('localhost', 8000))

try:

    while True:
    
        ip = input("Enter the website you want to ping: ")
        
        s.send(ip.encode())
        
        response = s.recv(1024).decode()
        
        if response:
        
            print("Ping Result:", response)
            
        else:
        
            print("No response from server.")
            
except Exception as e:

    print("Error:", e)
    
finally:

    s.close()


## Output
![image](https://github.com/PREETHI3312/4.Execution_of_NetworkCommends/assets/151625222/4a52ab17-4603-4345-8ff1-bc2d243d70be)

## TRACEROUTE COMMAND

from scapy.all import *
target = ["www.google.com"]
result, unans= traceroute(target,maxttl=32)
print(result,unans)

## OUTPUT
## CLIENT AND SERVER
![image](https://github.com/PREETHI3312/4.Execution_of_NetworkCommends/assets/151625222/1d0ce382-02bd-4141-a6e1-24dd8e2cce8e)




## Result
Thus Execution of Network commands Performed 
