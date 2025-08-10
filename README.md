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

    A -- Отправка списка любимых тайтлов\n(например: 'Berserk, Vagabond, Vinland Saga') --> B
    B -- Передача запроса через Webhook (HTTPS) --> D
    D -- Сохранение предпочтений\nв SQLite (TCP/IP) --> F
    D -- Поиск характеристик манг\nпо векторным эмбеддингам (HTTPS) --> J
    D -- Запрос рекомендаций\nс контекстом (HTTPS) --> G
    G -- Использование контекста\nиз базы знаний (HTTPS) --> J
    D -- Формирование персонализированной\nподборки рекомендаций --> B
    B -- Отправка пользователю\nсписка похожих манг --> A
```
