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

## 🏗️ System Architecture (Monolithic)

> **Monolithic Architecture** — Single deployable unit with modular internal layers.

## 🏗️ System Architecture (Monolithic)

```mermaid
graph TB
    subgraph Clients
        A[Next.js Web]
        B[Admin Dashboard]
    end
    
    subgraph "Monolithic Go Server"
        C[API Layer<br/>Gin/Echo Routes]
        D[Service Layer<br/>Business Logic]
        E[Repository Layer<br/>Data Access]
        F[WebSocket Hub]
        G[Order Engine]
    end
    
    subgraph Data
        H[(PostgreSQL)]
        I[(Redis)]
    end
    
    subgraph External
        J[Gold Price API]
        K[Payment Gateway]
    end
    
    A --> C
    B --> C
    C --> D
    D --> E
    D --> G
    C --> F
    E --> H
    E --> I
    G --> I
    G --> H
    F --> A
    F --> B
    C --> J
    C --> K
```