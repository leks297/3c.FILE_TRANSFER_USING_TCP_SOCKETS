# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## server.py
```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()

s.bind((host, port))
s.listen(1)

print("Server listening...")

while True:
    conn, addr = s.accept()
    print('Connected with', addr)

    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = 'mytext.txt'
    
    with open(filename, 'rb') as f:
        while True:
            l = f.read(1024)
            if not l:
                break
            conn.send(l)
            print('Sent', repr(l))

    print('Done sending')
    conn.close()
```
## client.py
```
import socket

s = socket.socket()
host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('received.txt', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)

        if not data:
            break

        f.write(data)

print('Successfully got the file')

s.close()
print('connection closed')
```
## OUPUT
<img width="1275" height="192" alt="image" src="https://github.com/user-attachments/assets/242b79cb-4d83-4ebd-ae87-9bac2153e69b" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
