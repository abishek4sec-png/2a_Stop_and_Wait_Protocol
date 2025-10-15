# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Create a socket at both sender and receiver sides.
3. The receiver (server) binds to a port and waits for connection; the sender (client) connects to it.
4. The sender takes input data from the user and sends it to the receiver.
5. The receiver receives the data, displays it, and sends back an acknowledgment message (“Acknowledgement Recived”).
6. The sender waits to receive this acknowledgment:If acknowledgment is received
7.  → continue to send the next data.If no acknowledgment
8.  → close the connection and stop.
9. Repeat until all data is sent, then close the connection on both sides.
## PROGRAM
## Client Side:
```
import socket
s=socket.socket()
s.bind(('localhost', 8001))
s.listen(5)
c,addr=s.accept()
while True:
    i=input("Enter a data: ")
    c.send(i.encode())
    ack=c.recv(1024).decode()
    if ack:
        print(ack)
        continue
    else:
        c.close()
        break
```
## Server Side:
```
import socket
s=socket.socket()
s.connect(('localhost', 8001))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement Recived frome the server".encode())
```
## OUTPUT
<img width="1036" height="371" alt="image" src="https://github.com/user-attachments/assets/ceda281f-01d3-4902-9af9-9f18013abc66" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
