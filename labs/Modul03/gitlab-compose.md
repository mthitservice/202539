Hier ist eine vollständige Anleitung als Markdown-Datei zur Einrichtung von **GitLab mit Docker** – ideal für lokale Entwicklung oder als Basis für produktive Deployments. Du kannst diese Datei direkt kopieren und als `gitlab-docker-setup.md` speichern:

---

```markdown
# 🧰 GitLab mit Docker einrichten – Schritt-für-Schritt Anleitung

Diese Anleitung zeigt dir, wie du GitLab lokal mit Docker betreibst – inklusive Konfiguration, Volumes und Portfreigabe.

---

## 📦 Voraussetzungen

- Installiertes Docker & Docker Compose
- Mindestens 4 GB RAM empfohlen
- Freier Port 80 oder 8080

---

## 📁 Projektstruktur

```plaintext
gitlab-docker/
├── docker-compose.yml
```

---

## 🧾 docker-compose.yml

```yaml
version: '3.8'

services:
  gitlab:
    image: gitlab/gitlab-ce:latest
    container_name: gitlab
    restart: always
    hostname: 'gitlab.local'
    environment:
      GITLAB_OMNIBUS_CONFIG: |
        external_url 'http://localhost:8080'
        gitlab_rails['gitlab_shell_ssh_port'] = 2222
    ports:
      - '8080:80'     # Webinterface
      - '443:443'     # HTTPS (optional)
      - '2222:22'     # SSH für Git
    volumes:
      - gitlab-config:/etc/gitlab
      - gitlab-logs:/var/log/gitlab
      - gitlab-data:/var/opt/gitlab

volumes:
  gitlab-config:
  gitlab-logs:
  gitlab-data:
```

---

## ▶️ GitLab starten

```bash
docker-compose up -d
```

GitLab wird nun im Hintergrund gestartet. Der erste Start kann einige Minuten dauern.

---

## 🌐 Zugriff auf GitLab

Öffne im Browser:

```
http://localhost:8080
```

Beim ersten Login wirst du nach einem **Root-Passwort** gefragt. Dieses findest du im Container-Log:

```bash
docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
```

---

## 🔧 Git konfigurieren (optional)

```bash
git config --global user.name "Dein Name"
git config --global user.email "dein@email.de"
```

---

## 🧠 Tipps

- Du kannst `external_url` auf deine IP oder Domain setzen
- Für produktive Nutzung: HTTPS aktivieren, Backups einrichten
- GitLab CE = Community Edition (kostenlos)

---

## 🧹 GitLab stoppen & entfernen

```bash
docker-compose down
```

→ Container wird gestoppt, Daten bleiben erhalten (durch Volumes)

---

## 📚 Weiterführende Links

- [GitLab Docker Docs](https://docs.gitlab.com/omnibus/docker/)
- [GitLab CE Features](https://about.gitlab.com/features/)
```

---

