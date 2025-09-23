Natürlich! Hier sind zwei vollständige Beispiele für eine `docker-compose.yml` mit Umgebungsvariablen für **Development** und **Production** – inklusive `.env` Dateien und typischer Unterschiede 🧪🛠️

---

## 📁 Projektstruktur

```plaintext
my-app/
├── docker-compose.yml
├── .env.development
├── .env.production
├── app/
│   └── app.py
```

---

## 🧾 `docker-compose.yml` mit Umgebungswahl

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "${PORT}:${PORT}"
    environment:
      - ENV=${ENV}
      - DEBUG=${DEBUG}
    volumes:
      - .:/app
    command: python app.py

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: ${DB_USER}
      POSTGRES_PASSWORD: ${DB_PASS}
      POSTGRES_DB: ${DB_NAME}
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:
```

---

## 🧪 `.env.development`

```dotenv
ENV=development
DEBUG=True
PORT=5000
DB_USER=devuser
DB_PASS=devpass
DB_NAME=devdb
```

## 🚀 `.env.production`

```dotenv
ENV=production
DEBUG=False
PORT=8000
DB_USER=produser
DB_PASS=prodpass
DB_NAME=proddb
```

---

## ▶️ Verwendung

### Development starten:

```bash
docker-compose --env-file .env.development up --build
```

### Production starten:

```bash
docker-compose --env-file .env.production up -d
```

---

## 🧠 Unterschiede zwischen Dev & Prod

| Merkmal     | Development        | Production                        |
| ----------- | ------------------ | --------------------------------- |
| Port        | 5000               | 8000                              |
| Debug-Modus | Aktiv (`True`)     | Deaktiviert (`False`)             |
| Volumes     | Lokale Bind-Mounts | Meist keine oder nur Datenvolumes |
| Logs        | Konsole            | Hintergrund (`-d`)                |
| Sicherheit  | Gering             | Hoch (z. B. TLS, Secrets)         |

---

