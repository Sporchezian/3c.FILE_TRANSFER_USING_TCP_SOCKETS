# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## FILE TRANSFER SERVER PROGRAM:
```
import socket

# Create socket
server = socket.socket()

# Bind IP and port
server.bind(("127.0.0.1", 5555))

# Listen for client
server.listen(1)

print("Server waiting for connection...")

# Accept client
client, addr = server.accept()

print("Connected to:", addr)

# Ask filename
filename = input("Enter file name to send: ")

# Open and send file
with open(filename, "rb") as file:
    data = file.read()
    client.send(data)

print("File sent successfully")

# Close connections
client.close()
server.close()
```
## FILE TRANSFER CLIENT PROGRAM:
```
import socket

# Create socket
client = socket.socket()

# Connect to server
client.connect(("127.0.0.1", 5555))

# Save file name
save_name = input("Enter name to save file: ")

# Receive data
data = client.recv(1000000)

# Save file
with open(save_name, "wb") as file:
    file.write(data)

print("File received successfully")

# Close connection
client.close()
```
## FILE TRANSFER SEREVR OUTPUT:
<img width="1423" height="174" alt="Screenshot 2026-05-26 142825" src="https://github.com/user-attachments/assets/0fbb8e6e-ed8d-4020-a134-cd8e85b955c2" />

## FILE TRANSFER  CLIENT OUTPUT:
<img width="1423" height="125" alt="Screenshot 2026-05-26 142529" src="https://github.com/user-attachments/assets/f7fbc4a3-ef53-43a5-a327-93d519be4a36" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
