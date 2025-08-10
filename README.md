```mermaid
graph TD
    subgraph "Клиент"
        A[Пользователь Telegram]
    end

    subgraph "Telegram"
        B[Telegram Bot]
        I[Telegram API]
    end

    subgraph "Backend"
        D[AI Agent <i>Python</i>]
    end

    subgraph "Хранилища"
        F[(SQLite <i>User Preferences</i>)]
        J[RAG Knowledge Base <i>MangaDB</i>]
    end

    subgraph "Внешние сервисы"
        G{{LLM <i>GigaChat</i>}}
    end

    A -- "MTProto/TCP" --> B
    B -- "HTTPS (Webhook)" --> D
    D -- "SQL over TCP/IP" --> F
    D -- "HTTPS/REST или gRPC" --> J
    D -- "HTTPS/GigaChat API" --> G
    G -- "HTTPS (Embeddings)" --> J
    D -- "HTTPS/Telegram Bot API" --> B  %% Ключевое изменение!
    B -- "MTProto/TCP" --> A
```
