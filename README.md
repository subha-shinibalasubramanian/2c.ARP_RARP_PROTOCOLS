# 2c.SIMULATING ARP /RARP PROTOCOLS
**NAME : SUBHASHINI.B** 
**REGISTER NUMBER : 212223040211**
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
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"BA:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("not found".encode())
```
## SERVER

```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("ENTER LOGICAL ADDRESS : ")
    s.send(ip.encode())
    print("MAC ADDRESS",s.recv(1024).decode())
```
## OUPUT - ARP

![image](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/164154478/1bd9896d-3e34-4986-a628-d66a2ad3cfa8)


## PROGRAM - RARP

## CLIENT 

```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```

## SERVER

```
import socket 
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC address: ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP

![Screenshot 2024-04-01 213555](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/164154478/f7d63800-4dbb-4987-bbdd-bc43fa9a0d8d)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
