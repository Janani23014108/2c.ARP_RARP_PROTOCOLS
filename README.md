# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP

## CLIENT
```
import socket
s = socket.socket() 
s.connect(('localhost', 8000))  
while True:
    ip = input("Enter logical Address: ")  
    s.send(ip.encode())  
    print("MAC Address", s.recv(1024).decode())
```

## SERVER
```
import socket
s = socket.socket() 
s.bind(('localhost', 8000)) 
s.listen(5)  
c, address = s.accept()  
address = {"10.239.83.23": "E0:2E:0B:37:CE:F9", "192.168.0.117": "E0:2E:0B:30:28:11"}  
while True:
    ip = c.recv(1024).decode()  
    try:
        c.send(address[ip].encode())  
    except KeyError:
        c.send("Not Found".encode())
```
## OUPUT - ARP
<img width="476" height="167" alt="image" src="https://github.com/user-attachments/assets/dbe3e43f-8825-4b72-adc4-78d78acc9c00" />


## PROGRAM - RARP

## CLIENT

```
import socket
s = socket.socket() 
s.connect(('localhost', 8000))  
while True:
    ip = input("Enter Physical Address: ")  
    s.send(ip.encode())  
    print("IP Address", s.recv(1024).decode())
```

## SERVER
```
import socket
s = socket.socket() 
s.bind(('localhost', 8000)) 
s.listen(5)  
c, address = s.accept()  
address = {"E0:2E:0B:37:CE:F9": "10.239.83.23" , "E0:2E:0B:30:28:11": "192.168.0.117"}  
while True:
    ip = c.recv(1024).decode()  
    try:
        c.send(address[ip].encode())  
    except KeyError:
        c.send("Not Found".encode())
```
## OUPUT -RARP

<img width="538" height="195" alt="image" src="https://github.com/user-attachments/assets/dd59cdba-ca75-41f5-add4-40491119959b" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
