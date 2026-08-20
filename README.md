# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
# Client
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000))
while True: 
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```

# Server
```
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
size=int(input("Enter number of frames to send : ")) 
l=list(range(size)) 
s=int(input("Enter Window Size : ")) 
st=0 
i=0 
while True: 
    while(i<len(l)): 
        st+=s 
        c.send(str(l[i:st]).encode()) 
        ack=c.recv(1024).decode() 
        if ack: 
            print(ack) 
            i+=s
```
## OUPUT
# Client
<img width="816" height="1030" alt="Screenshot 2026-08-20 214736" src="https://github.com/user-attachments/assets/45f9913b-3cff-42ef-99c6-943a2396aa17" />

# Server
<img width="998" height="977" alt="Screenshot 2026-08-20 214744" src="https://github.com/user-attachments/assets/0c98c46c-18f5-4c95-af18-224bf8263b47" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
