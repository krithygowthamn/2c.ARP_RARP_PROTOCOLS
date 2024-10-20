# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name: Gowtham N
## REg no:212222220013
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

## PROGRAM - ARP
## Client:
```
import socket
s=socket.socket()
s.bind(('localhost',80))
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
## Server:
```
import socket
s=socket.socket()
s.connect(('localhost',80))
while True:
   ip=input("Enter logical Address : ")
   s.send(ip.encode())
   print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
## Client:
![image](https://github.com/user-attachments/assets/47a17248-ed44-44fa-a9b5-2e3919027d1b)

## Server:
![image](https://github.com/user-attachments/assets/ecff9b51-8db1-40fb-a579-317f5da00edc)

## PROGRAM - RARP
## Client:
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
## Server:
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
## Client:
![image](https://github.com/user-attachments/assets/9b324977-1e52-4cf1-98b4-bc7cc55a4663)

## Server:
![image](https://github.com/user-attachments/assets/630d8e9d-8ed8-4db6-8319-f45cd894e550)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
