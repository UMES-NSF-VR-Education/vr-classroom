# 3D Multiplayer Classroom Game

A real-time, multiplayer 3D classroom environment built with Three.js, WebXR, and Socket.IO. This project features synchronized player movement, collision detection, spatial tracking, text chat, and WebRTC-based voice broadcasting.

This repo is now organized as a simple **client + server** project and no longer depends on Vagrant, Docker, or nginx configs.

---

## 📁 Folder Structure

- **`server/`** – Node.js backend (Socket.IO server)
  - `server/server.js`
  - `server/package.json`
  - `server/node_modules/`
- **`client/`** – Frontend (HTML + JavaScript)
  - `client/index.html`
  - `client/main.js`
  - `client/player.js`
  - `client/chat.js`

You only need these two folders to run the app locally.

---

## 🛠 Prerequisites

To run this project locally, you will need:

- **Node.js** (LTS recommended): `https://nodejs.org/`
- A modern browser with WebXR support (for VR features).
- Optional but convenient: **VS Code** + **Live Server** extension, or any static file server.

---

## 🚀 How to Run Locally

This project is divided into two main parts: a Node.js backend (Socket.IO server) and a vanilla JavaScript frontend (Three.js client). You need to run both for the game to work.

### 1. Start the Backend Server

The backend handles all the real-time player data and WebRTC signaling.

From a terminal:

```bash
cd server
npm install        # first time only
node server.js
```

The Socket.IO server will start on **`http://localhost:3000`**.

Leave this terminal window open while you play.

### 2. Start the Frontend (Client)

Open a **second** terminal and serve the `client/` folder.

#### Option A – Using VS Code Live Server

1. Open the project in VS Code:
   ```bash
   code .
   ```
2. Install the **Live Server** extension (if you don't have it).
3. Open `client/index.html` in VS Code.
4. Right-click the file and choose **"Open with Live Server"**.
5. Your browser will open at a URL like `http://127.0.0.1:5500/client/index.html`.

The client JS (`main.js`) connects to `http://localhost:3000` for real-time updates.

#### Option B – Using a simple static server (no VS Code)

From the project root or another terminal:

```bash
cd client
npx serve .
# or
npx http-server .
```

Then open the URL shown in the terminal (for example `http://localhost:3000` or `http://localhost:5000`, depending on the tool).

As long as the **server** is running on `localhost:3000`, player movement, chat, and voice should sync correctly.

---

## 🌐 Notes

- **Vagrant / Docker / nginx**: All VM/container configs have been removed. You don’t need VirtualBox, Vagrant, or Docker to run this project.
- **WebXR / HTTPS**: Some browsers require HTTPS for full WebXR or microphone features. For local testing, Chrome/Edge usually allow `http://localhost` with appropriate flags; if you need remote access or HTTPS, you can later add a reverse proxy or tunneling tool.

