# Dockerfile und Docker-Compose

---

```markdown
# 🐳 Dockerfile & Docker Compose – Beispiel & Erklärung

## Dockerfile – Was ist das?

Ein Dockerfile ist eine Textdatei, die beschreibt, wie ein Docker-Image gebaut wird. Du definierst darin die Basis, installierst Abhängigkeiten, kopierst Dateien und legst Startbefehle fest.

### Beispiel: Dockerfile für eine Python-App

```Dockerfile
# Basis-Image
FROM python:3.11-slim

# Arbeitsverzeichnis im Container
WORKDIR /app

# Anforderungen installieren
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# App-Dateien kopieren
COPY . .

# Startbefehl
CMD ["python", "app.py"]
```

##Ausführen
Um ein Dockerfile „aufzurufen“, also daraus ein Docker-Image zu erstellen und es auszuführen, gehst du in zwei Schritten vor:

---

## 🛠️ 1. Docker-Image aus dem Dockerfile bauen

Navigiere im Terminal in den Ordner, wo sich dein `Dockerfile` befindet, und führe folgenden Befehl aus:

```bash
docker build -t mein-image-name .
```

**Erklärung:**
- `docker build`: Baut ein Image
- `-t mein-image-name`: Vergibt einen Namen für das Image
- `.`: Bedeutet „aktuelles Verzeichnis“, wo das Dockerfile liegt

---

## ▶️ 2. Container aus dem Image starten

Nachdem das Image gebaut wurde, kannst du es mit folgendem Befehl starten:

```bash
docker run -p 5000:5000 mein-image-name
```

**Erklärung:**
- `docker run`: Startet einen Container
- `-p 5000:5000`: Verbindet Port 5000 des Containers mit Port 5000 deines Rechners
- `mein-image-name`: Name des zuvor gebauten Images

---

## 🔁 Optional: Interaktiv oder im Hintergrund

- **Interaktiv mit Terminalzugriff:**
  ```bash
  docker run -it mein-image-name /bin/bash
  ```

- **Im Hintergrund (Detached Mode):**
  ```bash
  docker run -d mein-image-name
  ```

---




## Docker Compose – Was ist das?

Docker Compose ist ein Tool, mit dem du mehrere Container (z. B. App + Datenbank) in einer einzigen YAML-Datei definieren und gemeinsam starten kannst.

### Beispiel: `docker-compose.yml` für Python-App + PostgreSQL

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/app
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:
```

## ▶️ Verwendung

1. Dockerfile erstellen → z. B. `Dockerfile` im Projektordner
2. Compose-Datei erstellen → `docker-compose.yml`
3. Starten mit:

```bash
docker-compose up --build
```

Die App läuft dann z. B. unter `http://localhost:5000`.

---

```

