# 2c.SIMULATING ARP /RARP PROTOCOLS
## DATE: 12-05-26
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
## SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## CLIENT
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
## OUPUT - ARP
![IMAGE](https://github.com/VGSAIRAIMA/2c.ARP_RARP_PROTOCOLS/blob/main/Screenshot%202026-05-12%20112219.png)
![IMAGE](https://github.com/VGSAIRAIMA/2c.ARP_RARP_PROTOCOLS/blob/main/Screenshot%202026-05-12%20112235.png)

## ALGORITHM - RARP
## Client
Start the program.
Create a socket and establish a connection with the server.
Enter the MAC address to be converted into an IP address.
Send the MAC address to the server.
Receive the corresponding IP address from the server.
Display the IP address.
## Server
Start the program.
Create a socket, bind it to a port, and listen for incoming connections.
Accept the connection request from the client.
Maintain a table containing MAC addresses and their corresponding IP addresses.
Receive the MAC address sent by the client.
Search for the MAC address in the table.
If found, send the corresponding IP address to the client.
Otherwise, send "Not Found".

## PROGRAM - RARP
## SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    mac=input("Enter Physical Address : ")
    s.send(mac.encode())
    print("MAC Address",s.recv(1024).decode())
```
## CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"FC:6D:77:6D:AA:7E":" 169.254.65.147","10:94:BB:EB:44:34":"169:254:201:22"};
while True:
    mac=c.recv(1024).decode()
    try:
       c.send(address[mac].encode())
    except KeyError:
       c.send("Not Found".encode())
```
## OUPUT -RARP
![IMAGE](https://github.com/VGSAIRAIMA/2c.ARP_RARP_PROTOCOLS/blob/main/Screenshot%202026-05-12%20114258.png)
![IMAGE](https://github.com/VGSAIRAIMA/2c.ARP_RARP_PROTOCOLS/blob/main/Screenshot%202026-05-12%20114308.png)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
