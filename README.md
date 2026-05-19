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
~~~
server.py
import socket
s = socket.socket()
s.bind(('localhost', 9999))
s.listen(1)
print("Server waiting...")
c, addr = s.accept()
print("Connected:", addr)

while True:
    data = c.recv(1024).decode()
    if data == "exit":
        break
    print("Client:", data)
    c.send("ACK".encode())
c.close()
s.close()

client.py
import socket
s = socket.socket()
s.connect(('localhost', 9999))

while True:
    msg = input("Enter message: ")
    s.send(msg.encode())
    if msg == "exit":
        break
    ack = s.recv(1024).decode()
    print("Server:", ack)
s.close()
~~~
## OUTPUT
<img width="572" height="213" alt="image" src="https://github.com/user-attachments/assets/5984d73b-c163-41bf-b7a6-c975ab38089e" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
