
---

## 🧑‍🏫 Unterrichtseinheit: Docker Build & Docker Compose


---

## 📦 Teil 1: Einstieg – Docker Build Basics

### Aufgabe 1: Hello World mit Dockerfile
- Erstelle ein Verzeichnis `hello-docker`
- Schreibe ein einfaches Python-Skript `app.py`:
  ```python
  print("Hello from Docker!")
  ```
- Erstelle ein `Dockerfile`, das dieses Skript ausführt
- Baue das Image mit `docker build`
- Starte den Container mit `docker run`

**Reflexion:**  
Was passiert beim Build? Was ist der Unterschied zwischen Image und Container?

---

### Aufgabe 2: Webserver mit Flask
- Erstelle eine kleine Flask-App mit `app.py`
- Erstelle ein `requirements.txt`
- Baue ein Dockerfile, das die App startet
- Teste die App lokal im Container

**Erweiterung:**  
Füge Umgebungsvariablen hinzu (z. B. Port, Debug-Modus)

---

## 🧩 Teil 2: Docker Compose – Mehrere Dienste

### Aufgabe 3: Compose für Flask + PostgreSQL
- Erstelle ein `docker-compose.yml` mit zwei Diensten:
  - `web`: Flask-App
  - `db`: PostgreSQL mit Umgebungsvariablen
- Nutze Volumes für persistente Daten
- Starte alles mit `docker-compose up`

**Reflexion:**  
Wie kommunizieren die Dienste? Was passiert beim Neustart?

---

### Aufgabe 4: Trennung von Umgebungen
- Erstelle `.env.development` und `.env.production`
- Nutze `--env-file` beim Start
- Passe `docker-compose.yml` so an, dass Variablen verwendet werden

**Erweiterung:**  
Logik in der App, die sich je nach Umgebung anders verhält

---

## 🔐 Teil 3: Sicherheit & Secrets

### Aufgabe 5: Docker Secrets im Swarm
- Initialisiere Swarm mit `docker swarm init`
- Erstelle ein Secret (z. B. DB-Passwort)
- Integriere das Secret in `docker-compose.yml`
- Deploye mit `docker stack deploy`

**Reflexion:**  
Warum sind Secrets sicherer als ENV-Variablen?

---

## 🧠 Teil 4: Erweiterung & Kreativität

### Aufgabe 6: Eigene Microservice-Anwendung
- Plane eine Anwendung mit mindestens 3 Diensten (z. B. Web, DB, Cache)
- Erstelle Dockerfiles für jeden Dienst
- Baue ein `docker-compose.yml` mit Netzwerken, Volumes, Healthchecks
- Dokumentiere dein Setup in einer `README.md`

**Optionale Ideen:**
- Node.js + MongoDB + Redis
- FastAPI + PostgreSQL + Adminer
- Frontend + Backend + Datenbank

---

## 📋 Bonus: Reflexionsfragen für Gruppenarbeit

- Was sind die Vorteile von Docker gegenüber klassischer Installation?
- Wie hilft Compose bei der Teamarbeit?
- Welche Sicherheitsaspekte sind bei Secrets und Volumes zu beachten?
- Wie würdet ihr euer Projekt in der Cloud deployen?

---

