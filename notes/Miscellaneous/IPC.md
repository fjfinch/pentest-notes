# IPC
Inter-Process Communication (IPC) refers specifically to the mechanisms an operating system provides to allow the processes and applications to manage shared data to other processes and applications. Typically, applications can use IPC, categorized as clients and servers, where the client requests data and the server responds to client requests. Many applications are both clients and servers, as commonly seen in distributed computing. There are multiple types of IPCs.

## Pipes
A pipe is a type of IPC. It is a section of shared memory that processes use for communication. One process writes information to the pipe, then the other process reads the information from the pipe. One-way (simplex) pipe: allows a process at one end to write to the pipe, and allows a process at the other end to read from the pipe. Two-way (duplex) pipe: allows a process to read and write from its end of the pipe.

* Anonymous pipe: an unnamed, one-way pipe that typically transfers data between a parent process and a child process. Anonymous pipes are always local; they cannot be used for communication over a network. Anonymous pipes are implemented using a named pipe with a unique name.
* Named pipe (FIFO): a named pipe is a named, one-way or duplex pipe for communication between the pipe server and one or more pipe clients. Named pipes can be used to provide communication between processes on the same computer or between processes on different computers across a network. Named pipes are being used over [[139,445 NetBIOS & SMB|SMB]].

Named pipes are created on the SMB server side by applications and tools that are willing to provide specialized services. A named pipe is a logical connection, similar to a TCP session, between a client and server that are involved in a SMB connection. The name of the pipe serves as the endpoint for communication in the same way that a port number serves as the endpoint for TCP sessions. The IPC$ share is not a directory, but it is used to create named pipes.

With an anonymous null session you can access the IPC$ share and interact with services exposed via named pipes.