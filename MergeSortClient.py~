
import socket
import time, sys             
  
ip = sys.argv[1]   #ip address of client
          
port = int(sys.argv[2])

ServerSocket = socket.socket()  
print "Client Socket has been Created successfully"  
      
ServerSocket.connect((ip, port))
#opening a file

Input= open("infile.dat", "r") 
#running a loop for all lines
for sendline in Input: 
	print "\nSent -",sendline
	#Sending a line to the server
	ServerSocket.send(sendline.strip())
	#Receiving the Sorted line to the server
	receivedline = ServerSocket.recv(1024)
	#Making it sleep before sending another line
	time.sleep(3)
	print 'Received', receivedline


ServerSocket.close()


