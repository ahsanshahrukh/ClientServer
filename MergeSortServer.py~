#importing all libraries
import socket
import json
import os 
import sys  

def mergeSort(arr): 
    if len(arr) >1: 
        mid = len(arr)//2 #Finding the mid of the array 
        Left = arr[:mid] # Dividing the array elements  
        Right = arr[mid:] # into 2 halves 
  
        mergeSort(Left) # Sorting the first half 
        mergeSort(Right) # Sorting the second half 
  
        i= j = k = 0
          
        while i < len(Left) and j < len(Right): 
            if Left[i] < Right[j]: 
                arr[k] = Left[i] 
                i+=1
            else: 
                arr[k] = Right[j] 
                j+=1
            k+=1
          
        # Checking if any element was left 
        while i < len(Left): 
            arr[k] = Left[i] 
            i+=1
            k+=1
  	# Checking if any element was Right
        while j < len(Right): 
            arr[k] = Right[j] 
            j+=1
            k+=1
    return arr   	

 
if __name__ == '__main__':        
	serversocket = socket.socket()          
	print "Socket has been Created successfully"
              
	port = int(sys.argv[1])
	serversocket.bind(('', port))         


	serversocket.listen(10) #Listening maximum of 10 clients.     
	print " listening............."            
	ClientCount=0

	while True:  
		conn, address = serversocket.accept()      
		print 'Connected to', address 
		pid=os.fork()
		ClientCount=ClientCount+1
		if (pid)==0:
		
			print "Child Process is created"
			print "Client Count is",ClientCount
			serversocket.close()
		
			while True:
				received = conn.recv(1024)
				sortingArray=[]
				for item in received.split(" "):
					sortingArray.append(item)
				sorted = mergeSort(sortingArray)
				if not received:
					break
				conn.send(json.dumps(sorted))
			os. _exit(0)
		pid,status=os.waitpid(0,os.WNOHANG)
	
	
# Close the connection with the client 
	conn.close()




