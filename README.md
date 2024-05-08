1. Terminal view from each client/server:
-   Server: ![alt text](image.png)
-   Client 1: ![alt text](image-1.png)
-   Client 2: ![alt text](image-2.png)
-   Client 3: ![alt text](image-3.png)
Explanation: Each time a client is ran using run cargo --bin client, it will search for a connection to port 2000 where the server is listening. If the server wasn't found, it crashed. So to run the program, always activate the server first with cargo run --bin server. Here is how the interactions work: the server is set up with a WebSocket-based chat application that uses a broadcast channel to manage messages between clients. When a client sends a message, the server receives it through its WebSocket connection and broadcasts it to all clients, including the sender, via the bcast_tx channel. Each client has an active listener for incoming messages (bcast_rx.recv()) in their concurrent loop, so when a message is broadcasted by the server, all connected clients receive and display it, resulting in the messages from each client being seen by all others.
