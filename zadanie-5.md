Stwórz prosty diagram ASCII Art przedstawiający połączenie klienta, serwera aplikacji i bazy danych.

   🌐 [Klient]
      Browser
         |
         | HTTP/HTTPS (port 80/443)
         |
    +----▼-----+
    |          |
    |  Serwer  |
    |   App    |
    |          |
    +----┬-----+
         |
         | TCP/IP (np. port 5432 dla PostgreSQL)
         |
    +----▼-----+
    |          |
    |   DB     |
    |          |
    +----------+



Dodaj do diagramu opisy elementów i kierunki przepływu danych.

                  🌐 [KLIENT]
                  Przeglądarka/Aplikacja
                        ║
   ┌─────────────Żądania/Odpowiedzi────────────┐
   │                    ║                       │
   │            (HTTP/HTTPS REST)              │
   │                    ║                       │
   │                    ▼                       │
   │            +---------------+               │
   │            │    SERWER    │               │
   │            │  APLIKACJI   │               ▲
   │            │              │               │
   │            │ - API        │               │
   │            │ - Logika     │          Odpowiedzi
   │            │ - Cache      │               │
Żądania        +---------------+               │
   │                    ║                       │
   │                    ║                       │
   │            (TCP/IP, SQL)                  │
   │                    ║                       │
   │                    ▼                       │
   │            +---------------+               │
   │            │     BAZA     │               │
   │            │    DANYCH    │               │
   │            │              │               │
   │            │ - Storage    │               │
   └────────────► - Queries    │───────────────┘
                +---------------+

Legenda:
═══════════════════════════════════
║  - Główny przepływ danych
│  - Kierunek przepływu
►  - Kierunek żądania
▼  - Przepływ w dół
▲  - Przepływ w górę

Przepływ danych:
1. Klient wysyła żądanie HTTP/HTTPS
2. Serwer przetwarza żądanie
3. Serwer komunikuje się z bazą danych
4. Baza zwraca dane do serwera
5. Serwer przetwarza odpowiedź
6. Klient otrzymuje odpowiedź