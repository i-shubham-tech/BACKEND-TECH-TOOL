# 1-Socket.IO

Socket.IO is a JavaScript library that helps you build real-time features easily.

## Examples of Real-Time Features

- Live chat
- Live notifications
- Online/offline live status
- Live updates (like counting likes instantly)
- Multiplayer games
- Live location sharing

# 2-How Socket.IO Works (Beginner Diagram)

```plaintext
Client (Browser / Mobile App)
        ⇅
   Socket.IO Connection
        ⇅
Server (Node.js)
```

# 3-Installation 

## Install Server (Node.js)
```bash
npm install socket.io
```

## Install Client (Browser)

**Use CDN:**
```html
<script src="https://cdn.socket.io/4.7.2/socket.io.min.js"></script>
```

**OR for React/Vue projects:**
```bash
npm install socket.io-client
```

#  4-Basic Setup

## 4.1 Server Code (Node.js)

Create a file named `server.js`:

```js
const express = require("express");
const http = require("http");
const { Server } = require("socket.io");

const app = express();
const server = http.createServer(app);
const io = new Server(server);

io.on("connection", (socket) => {
    console.log("A user connected:", socket.id);
// rest listener function will create here
});
 
server.listen(3000, () => {
    console.log("Server running on port 3000");
});
```

### 4.2 Client Code (HTML)

Create a file named `index.html`:
```html
<script src="https://cdn.socket.io/4.7.2/socket.io.min.js"></script>
<script>
    const socket = io("http://localhost:3000");

    socket.on("connect", () => {
        console.log("Connected to server:", socket.id);
    });
</script>
```

# 5. What Are Events?

Socket.IO works using events.  
Events allow the client and server to send messages to each other.

Think of events like labels.

Examples:
- "message"
- "join_room"
- "send_notification"
- "typing"

We use:
- `socket.emit("eventName", data)` → Send data
- `socket.on("eventName", callback)` → Receive data


# 6. Send Data From Client → Server

**Client (browser):**
```js
socket.emit("hello", "I am the client");
```

**Server:**
```js
io.on("connection", (socket) => {
    socket.on("hello", (data) => {
        console.log("Client says:", data);
    });
});
```

**Output:**
```
Client says: I am the client
```

---

# 7. Send Data From Server → Client
**Server:**
```js
io.on("connection", (socket) => {
    socket.emit("welcome", "Welcome to the server!");
});
```

**Client:**
```js
socket.on("welcome", (msg) => {
    console.log(msg);
});
```

**Output (browser):**
```
Welcome to the server!
```

---

# 7. Sending Objects (not just strings)
Socket.IO can send any JavaScript object.

**Client:**
```js
socket.emit("user_details", {
    name: "Shubham",
    class: "IT",
    year: 2025
});
```

**Server:**
```js
socket.on("user_details", (user) => {
    console.log(user.name);   // Shubham
});
```

---

# 8. Broadcasting Messages

Broadcasting = send message to all clients except the sender.

**Example:** When one person sends a message, others get it.

**Server-side Broadcasting:**
```js
socket.on("chatMsg", (msg) => {
    socket.broadcast.emit("receiveMsg", msg);
});
```

**Client:**
```js
socket.on("receiveMsg", (msg) => {
    console.log("Someone said:", msg);
});
```

**Use cases:**
- Chat apps
- “User typing…” message
- Online/offline status

---

# 9. Send Message to ALL Clients (including sender)
**Server:**
```js
io.emit("notification", "New user joined!");
```

**Client:**
```js
socket.on("notification", (msg) => {
    console.log(msg);
});
```

---

# 10. Acknowledgements (Confirmation Response)

Acknowledgement = server sends a callback response to client.

**Client:**
```js
socket.emit("sendMsg", "Hello server", (response) => {
    console.log("Server replied:", response);
});
```

**Server:**
```js
socket.on("sendMsg", (msg, callback) => {
    console.log(msg);
    callback("Message received!");
});
```

**Output:**
```
Hello server
Server replied: Message received!
```

---

# 11. Disconnect Event

Server detects when a user leaves.

**Server:**
```js
socket.on("disconnect", () => {
    console.log("A user disconnected", socket.id);
});
```

# 12. How to Join a Room

## Server Side
```js
io.on("connection", (socket) => {
    socket.on("join_room", (roomName) => {
        socket.join(roomName);
        console.log(`${socket.id} joined room ${roomName}`);
    });
});
```

## Client Side
```js
socket.emit("join_room", "RoomA");
```

### Output:
```
User zse78js joined room RoomA
```

---

# 13. Send Message ONLY Inside a Room

### Server
```js
socket.on("send_room_msg", ({ room, message }) => {
    io.to(room).emit("room_msg", message);
});
```

### Client
```js
socket.emit("send_room_msg", {
    room: "RoomA",
    message: "Hello Room!"
});
```

### Client (to listen)
```js
socket.on("room_msg", (msg) => {
    console.log("Room message:", msg);
});
```

### Note:
- Only users inside **RoomA** get this message.
- Other rooms do **not** receive it.

---

# 14. Leave a Room
```js
socket.leave("RoomA");
```

---

# 15. Private Messaging (User to User)

Each socket has a unique ID, e.g.,  
`socket.id = "xa93js8d"`

This ID can be used as a private room.

### Server – Send private message
```js
socket.on("private_msg", ({ to, message }) => {
    io.to(to).emit("private_msg", {
        from: socket.id,
        message
    });
});
```

### Client – Send message to someone
```js
socket.emit("private_msg", {
    to: "xa93js8d",
    message: "Hello privately!"
});
```

### Client – Receive private message
```js
socket.on("private_msg", (data) => {
    console.log("Private message:", data);
});
```

---

# 16. How to Know All Connected Users

### Server
```js
io.on("connection", (socket) => {
    console.log("User connected:", socket.id);
    console.log("All connected users:", [...io.sockets.sockets.keys()]);
});
```
```
