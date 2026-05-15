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
import socket

server = socket.socket()
server.bind(('localhost', 8000))
server.listen(5)

print("ARP Server Waiting...")
client, addr = server.accept()
print("Connected with", addr)

address_table = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = client.recv(1024).decode()

    if not ip:
        break

    mac = address_table.get(ip, "Not Found")
    client.send(mac.encode())
## OUPUT - ARP
<img width="1366" height="768" alt="Screenshot 2026-05-15 122234" src="https://github.com/user-attachments/assets/642eb026-9a01-40b7-804a-637b60eb25bc" />

## PROGRAM - RARP
import socket

client = socket.socket()
client.connect(('localhost', 8000))

while True:
    ip = input("Enter Logical Address: ")

    if ip.lower() == 'exit':
        break

    client.send(ip.encode())
    print("MAC Address:", client.recv(1024).decode())

## OUPUT -RARP
<img width="1366" height="768" alt="Screenshot 2026-05-15 122221" src="https://github.com/user-attachments/assets/5208b50c-768b-4a7a-9a12-e5f76783f947" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
