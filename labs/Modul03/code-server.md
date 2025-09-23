 Hier ist eine vollständige Anleitung als Markdown-Datei zur Einrichtung von **Code Server** (Visual Studio Code im Browser) mit Docker – ideal für lokale Entwicklung, Unterricht oder Remote-Projekte. Du kannst sie direkt kopieren und als `code-server-docker.md` speichern:

---

```markdown
# 🧰 Code Server mit Docker einrichten – Schritt-für-Schritt Anleitung

Diese Anleitung zeigt dir, wie du [code-server](https://github.com/coder/code-server) lokal mit Docker betreibst – eine browserbasierte Version von Visual Studio Code.

---

## 📦 Voraussetzungen

- Installiertes Docker
- Freier Port (z. B. 8080)
- Optional: Docker Compose

---

## 🧾 Variante 1: Direkt mit Docker CLI

```bash
docker run -d \
  --name code-server \
  -p 8080:8080 \
  -v "$HOME/code-server-data:/home/coder/project" \
  codercom/code-server:latest
```

**Zugriff:**  
Öffne im Browser: [http://localhost:8080](http://localhost:8080)

**Standard-Passwort:**  
Wird beim ersten Start im Container-Log angezeigt:

```bash
docker logs code-server
```

---

## 🧾 Variante 2: Mit Docker Compose

### 📁 Projektstruktur

```plaintext
code-server/
├── docker-compose.yml
```

### Inhalt der `docker-compose.yml`

```yaml
version: '3.8'

services:
  code-server:
    image: codercom/code-server:latest
    container_name: code-server
    ports:
      - "8080:8080"
    volumes:
      - ./workspace:/home/coder/project
    environment:
      PASSWORD: "meinpasswort"
    restart: unless-stopped
```

### Starten

```bash
docker-compose up -d
```

→ Zugriff unter [http://localhost:8080](http://localhost:8080)

---

## 🔐 Sicherheit

- Setze ein sicheres Passwort über die `PASSWORD`-Umgebungsvariable
- Für produktive Nutzung: HTTPS aktivieren oder hinter einen Reverse Proxy (z. B. Traefik, Nginx) stellen
- Du kannst auch einen **Token-basierten Login** verwenden

---

## 🧠 Tipps

- Der Ordner `workspace` ist dein Projektverzeichnis
- Du kannst Extensions direkt im Browser installieren
- Nutze `--user` oder `UID:GID`, wenn du Dateirechte anpassen willst

---

## 📚 Weiterführende Links

- [Code Server GitHub](https://github.com/coder/code-server)
- [Docker Hub Image](https://hub.docker.com/r/codercom/code-server)
- [TLS Setup Guide](https://coder.com/docs/code-server/latest/guide#using-https)

```

---

