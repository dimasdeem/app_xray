# Xray-Core Raw Payload Bypass & TCP-in-TCP Optimizer

This repository contains a highly customized and modified version of **Xray-core v25.10.15**. It is specifically engineered to bypass **Deep Packet Inspection (DPI)** on restrictive networks (e.g., educational data plans) using a **Raw Payload Camouflage** technique. 

Furthermore, this project includes advanced *TCP-in-TCP* optimizations to eliminate **Bufferbloat (Burst Upload)** and **Loop Retry issues** when uploading large files (such as on WhatsApp and Telegram) over a WebSocket tunnel.

## ✨ Key Features

1. **DPI Bypass (Raw Payload)**: Camouflages the connection as standard HTTP traffic (e.g., `edu.ruangguru.com`) by utilizing a custom `GET` and `PATCH` handshake sequence.
2. **Gorilla WebSocket Patch**: The server-side Gorilla library is modified to accept the non-standard `PATCH` method and cleanly discard the "Spoof Marker" (`HTTP/ 200 OK`) from the TCP buffer.
3. **Cloudflare & NAT Compatible**: Successfully bypasses Cloudflare Origin Rules and VPS NAT limitations by utilizing optimal stream handling.
4. **Anti-Bufferbloat (OS-Level Backpressure)**: Utilizes a custom `SetWriteBuffer(512KB)` in the dialer to prevent fake "Burst Upload" illusions, ensuring large file uploads are stable, fluctuating naturally with the real network speed, and never timing out.

---
