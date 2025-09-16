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


## PROGRAM - ARP
CLIENT
```

import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"255.255.255.240":"68:34:21:81:42:EB","172.20.10.2":"8A:BC:E3:FA"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())
```

SERVER
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

<img width="1027" height="378" alt="Screenshot 2025-09-08 111224" src="https://github.com/user-attachments/assets/4c5c5796-51d0-4349-93dc-698c9f683142" />
<img width="1022" height="369" alt="Screenshot 2025-09-08 111239" src="https://github.com/user-attachments/assets/45c05f76-b0f4-48da-a529-2d8a6b57540e" />
<img width="1020" height="373" alt="Screenshot 2025-09-08 111248" src="https://github.com/user-attachments/assets/c8a9b6b2-eb5c-4c35-bbab-8f3f5f227b15" />
<img width="1028" height="357" alt="Screenshot 2025-09-08 111300" src="https://github.com/user-attachments/assets/f28ae1d5-741b-4491-98c3-fd5bca3c31bc" />






## PROGRAM - RARP

CLIENT
```
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"68:34:21:81:42:EB":"255.255.255.240","8A:BC:E3:FA":"192.168.1.99"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())
```

SERVER
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

<img width="1022" height="379" alt="Screenshot 2025-09-08 111457" src="https://github.com/user-attachments/assets/c61503da-9570-4ea3-bf4c-76bf3c8798fe" />
<img width="1014" height="352" alt="Screenshot 2025-09-08 111535" src="https://github.com/user-attachments/assets/7e6898e8-3583-4402-8d61-f9875098d824" />
<img width="1018" height="310" alt="Screenshot 2025-09-08 111541" src="https://github.com/user-attachments/assets/cdf83ac6-1d2a-4e96-81e7-4f13cd28139f" />
<img width="1022" height="312" alt="Screenshot 2025-09-08 111548" src="https://github.com/user-attachments/assets/67979a21-0f73-42ef-bfdc-cbe787d0a035" />




## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
