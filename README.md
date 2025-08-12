# File-Transfer-using-TCP-Sockets

CREATION FOR FILE TRANSFER USING TCP SOCKETS

EXP: 10

DATE: 08.05.23

AIM:

To write a python program for creating File Transfer using TCP Sockets Links.

ALGORITHM:

1. Start the program.
2. Get the frame size from the user.
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server, it will send ACK signal to client otherwise it
will sendNACK signal to client.
6. Stop the program
 
PROGRAM:

CLIENT:

```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    while True:
        print('Receiving data...')
        data = s.recv(1024)
        print('data=%s' % data)
        if not data:
            break
        f.write(data)

print('Successfully got the file')
s.close()
print('Connection closed')

```
SERVER:

```
import socket 

port = 60000
s = socket.socket() 
host = socket.gethostname() 

s.bind((host, port)) 
s.listen(5)

print(f"Server listening on {host}:{port}...")

while True:
    conn, addr = s.accept()
    print(f"Got connection from {addr}")

    data = conn.recv(1024)
    print('Server received:', repr(data))

    filename = 'mytext.txt'  # File to send
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)

    print('Done sending file')
    conn.send('Thank you for connecting'.encode())
    conn.close()

```

OUTPUT:

CLIENT:
![WhatsApp Image 2023-05-28 at 9 46 33 PM](https://github.com/Harsayazheni/File-Transfer-using-TCP-Sockets/assets/118708467/77f9108e-2306-4886-b745-86268c63ab42)

SERVER:

![WhatsApp Image 2023-05-28 at 9 46 26 PM](https://github.com/Harsayazheni/File-Transfer-using-TCP-Sockets/assets/118708467/52993de4-ac72-4434-a9e2-dd6714c14f8e)

RESULT:

Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
