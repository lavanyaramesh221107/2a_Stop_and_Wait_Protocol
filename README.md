# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## server
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
## CLIENT
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT
## server

<img width="1841" height="956" alt="Screenshot 2026-05-11 083157" src="https://github.com/user-attachments/assets/7713ee2b-73d1-4186-b3fd-99b55f566364" />

## client

<img width="1850" height="979" alt="Screenshot 2026-05-11 083140" src="https://github.com/user-attachments/assets/a575df80-7945-45d6-9606-1f215173cc27" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
