# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## Name: Shreenidhi
## Reg.NO:212225040410
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
server
~~~
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
~~~
client
~~~
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('mytext.txt', 'wb') as f:
 while True:
    print('receiving data...')
    data = s.recv(1024)
    print('data=%s', (data))
    if not data:
        break
    f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
~~~
## OUPUT
server

![WhatsApp Image 2026-03-11 at 2 22 12 PM](https://github.com/user-attachments/assets/0a50fa97-f58b-4749-8059-05306544e309)
client

![WhatsApp Image 2026-03-11 at 2 21 15 PM](https://github.com/user-attachments/assets/46c84194-14b6-4a97-9f69-61ad94439d1f)



## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
