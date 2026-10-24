# Group Cam Chat

Multi-room group chat with optional webcam streaming.

**Stack**
- Backend: Python (FastAPI + python-socketio)
- Frontend: React (Vite) + native WebRTC
- Signaling & text chat over Socket.IO
- Peer-to-peer video (mesh)

## Features
- Multiple named rooms
- Real-time text chat
- Optional camera + microphone publishing
- Live user list with camera status
- Works in modern browsers (Chrome, Firefox, Edge, Safari)

## Quick start

### 1. Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
python main.py
```

Server runs at **http://localhost:8000**

### 2. Frontend

```bash
cd frontend
npm install
npm run dev
```

Open **http://localhost:5173**

### 3. Test with multiple clients
Open the app in two (or more) browser windows / tabs / devices on the same network.
Join the same room name. Enable camera on one or both.

## Environment

Optional: set the Socket.IO server URL for the frontend:

```bash
# frontend/.env
VITE_SOCKET_URL=http://localhost:8000
```

## Notes / Limitations (MVP)
- Mesh WebRTC – best for small groups (≤ 6–8 people). Larger groups need an SFU (e.g. mediasoup, LiveKit).
- Rooms are in-memory (lost on server restart).
- No authentication / private rooms yet.
- STUN only (works on most networks; strict NATs may need TURN).

## Next ideas
- Add TURN server for better connectivity
- Persistent rooms + message history (Redis / Postgres)
- Screen sharing
- Mute / video mute per peer
- Room passwords or invite links
- Deploy backend + frontend (Render, Fly.io, Vercel, etc.)
