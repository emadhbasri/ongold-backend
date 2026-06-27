# ⚙️ Ongold - Backend API (Go)

> **Private Repository** · Source code is proprietary

![Go](https://img.shields.io/badge/Go-1.22+-00ADD8?style=flat&logo=go)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16.x-4169E1?style=flat&logo=postgresql)
![Redis](https://img.shields.io/badge/Redis-7.x-DC382D?style=flat&logo=redis)
![WebSocket](https://img.shields.io/badge/WebSocket-Go--gorilla-010101?style=flat)
![Status](https://img.shields.io/badge/Status-Production-success?style=flat)

---

## 📖 About The Project

High-performance backend for **Ongold** gold trading platform.

### Core Features
- 👤 **User Management** — Registration, KYC, authentication (JWT)
- 💰 **Wallet System** — Deposits, withdrawals, balance tracking
- 🥇 **Gold Trading Engine** — Spot & pending orders
- 📊 **Portfolio Management** — Auto-close on stop-loss (SL)
- 🛑 **SL/TP System** — Configurable per order
- 📈 **Multiple Lots** — Trade with adjustable lot sizes
- 👥 **Referral System** — Commission on downline trades
- 🔄 **Real-time Updates** — WebSocket for live prices & orders

---

## 🏗️ System Architecture

```mermaid
graph TB
    subgraph Clients
        A[Next.js Web]
        B[Admin Dashboard]
    end
    
    subgraph Backend
        C[Go API Server<br/>Gin/Echo]
        D[WebSocket Hub<br/>gorilla/websocket]
        E[Order Engine<br/>Matching Logic]
    end
    
    subgraph Data
        F[(PostgreSQL<br/>Users/Wallets/Orders)]
        G[(Redis<br/>Cache/Session/Locks)]
    end
    
    subgraph External
        H[Gold Price API]
        I[Payment Gateway]
    end
    
    A --> C
    B --> C
    A --> D
    B --> D
    C --> E
    C --> F
    C --> G
    D --> G
    E --> F
    E --> G
    C --> H
    C --> I