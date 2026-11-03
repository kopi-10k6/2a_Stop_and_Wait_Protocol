# 2a_Stop_and_Wait_Protocol

## AIM:
To write a python program to perform stop and wait protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program

## SERVER PROGRAM:
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
## CLIENT PROGRAM:
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

## SERVER OUTPUT

<img width="942" height="1037" alt="Screenshot 2026-11-03 133928" src="https://github.com/user-attachments/assets/299ecc18-1fd9-47ed-bc57-261f97c7c717" />

## CLIENT OUTPUT:

<img width="949" height="1009" alt="Screenshot 2026-11-03 133948" src="https://github.com/user-attachments/assets/b5c38f5a-b3b3-46ad-960e-46fc3586c3d5" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
