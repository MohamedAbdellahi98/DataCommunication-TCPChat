# DataCommunication-TCPChat
This project appears to be a simple client-server chat application implemented in C using the Winsock library for Windows systems. The server allows multiple clients to connect, exchange public and private messages, list online users, and handle special commands. Additionally, the project includes error handling, multi-threading for concurrent client connections, and message integrity verification through checksums and CRC.

Here is a brief description of the key components:

Server (server.c):
Server Initialization:

The server initializes Winsock, creates a socket, and binds it to a specified port.
It listens for incoming connections and accepts clients.
User Handling:

Each connected client is represented by a struct User, which stores information such as IP address, socket, and username.
A maximum of MAXUSER clients can connect simultaneously.
Client Threads:

Each client connection is managed by a dedicated thread (ServiceClient).
The thread handles public and private messages, user exits, and listing online users.
Message Corruption Handling:

If a client detects a corrupted message, it requests the server to resend the corrected message (MERR command).
Logging:

Private messages are logged to files with filenames based on the date, time, and usernames involved in the conversation.
Client (client.c):
Client Initialization:

The client initializes Winsock, creates a socket, and connects to the server using the specified hostname and port.
User Registration:

The client registers its username with the server upon connection.
Message Handling:

The client has a dedicated thread (ReceiveChat) for continuously receiving and processing messages from the server.
Messages may include public, private, and corrected messages.
Message Integrity Verification:

The client verifies the integrity of received messages using checksums and CRC8.
If a message is detected as corrupted, the client requests a corrected message from the server.
User Input:

The client continuously reads user input from the console and sends messages to the server.
Overall Description:
The project allows multiple clients to connect to a server, exchange public and private messages, and perform basic chat functionalities. Message integrity is ensured through checksums and CRC, and special commands such as listing users and exiting the chat are supported. The server handles multiple client connections concurrently using threads.
