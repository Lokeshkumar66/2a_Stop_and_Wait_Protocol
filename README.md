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
server side:
~~~
import socket

s = socket.socket()
s.bind(('localhost', 1234))
s.listen(1)

print("Server started, waiting for client...")
conn, addr = s.accept()
print("Connected with", addr)

while True:
    frame = conn.recv(1024).decode()
    if frame == "END":
        print("Transmission completed")
        break

    print("Frame received:", frame)
    conn.send("ACK".encode())

conn.close()
s.close()
~~~
client side:
~~~
import socket

c = socket.socket()
c.connect(('localhost', 1234))

frame_size = int(input("Enter number of frames: "))

for i in range(frame_size):
    frame = f"Frame {i+1}"
    print("Sending:", frame)
    c.send(frame.encode())

    ack = c.recv(1024).decode()
    print("Received:", ack)

c.send("END".encode())
c.close()
~~~
## OUTPUT
server side:
<img width="1037" height="740" alt="Screenshot 2026-02-11 105950" src="https://github.com/user-attachments/assets/f63a5b70-3c4f-44b5-a53d-4c8804ef7430" />

client side:
<img width="1037" height="740" alt="Screenshot 2026-02-11 105950" src="https://github.com/user-attachments/assets/be9ee539-7aef-418f-b905-0e15e00bea17" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
