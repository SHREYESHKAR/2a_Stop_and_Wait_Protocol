# 2a_Stop_and_Wait_Protocol
# SHREYESHKAR SEKAR
# 212224220099

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
```
SERVER.PY
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Server listening...")

c, addr = s.accept()
print("Connected:", addr)

while True:
    data = c.recv(1024)
    if not data: break
    msg = data.decode()
    print("Client:", msg)
    c.send(b"ACK")
    if msg.lower() == "exit": break

c.close()
s.close()

```
```
CLIENT.PY
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    msg = input("Enter message for server: ")
    s.send(msg.encode())
    data = s.recv(1024).decode()
    print("Server:", data)

    if msg.lower() == "exit":
        break

s.close()
```
## OUTPUT

<img width="1918" height="1137" alt="exp 2a 1st" src="https://github.com/user-attachments/assets/142299b6-638d-4557-b190-5941e1505130" />

<img width="1918" height="1140" alt="exp 2a 2nd" src="https://github.com/user-attachments/assets/3bfe6ee2-9162-4510-9622-c4c16b31e5b8" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
