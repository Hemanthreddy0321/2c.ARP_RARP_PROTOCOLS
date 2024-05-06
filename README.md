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

Client.py:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```
server.py
```
 import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP

Client:

![image](https://github.com/Hemanthreddy0321/2c.ARP_RARP_PROTOCOLS/assets/150005937/6b57c2c7-fd1b-4e75-8d6e-0822d3b4679d)

Server:

![image](https://github.com/Hemanthreddy0321/2c.ARP_RARP_PROTOCOLS/assets/150005937/79c2f622-0511-4c93-8360-bccb36952e70)




## PROGRAM - RARP

Client.py:
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
    c.send("Not Found".encode()
```
server.py:
```
 import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```


## OUPUT -RARP

Client:

![image](https://github.com/Hemanthreddy0321/2c.ARP_RARP_PROTOCOLS/assets/150005937/b0f24f38-995c-4f59-b0f3-bdddf3b1b4f0)

Server:

![image](https://github.com/Hemanthreddy0321/2c.ARP_RARP_PROTOCOLS/assets/150005937/e37f5841-e078-433e-95c8-3dfa8fbabbbe)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
