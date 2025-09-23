Natürlich! Hier ist eine erweiterte Markdown-Datei mit allen wichtigen `docker-compose` Befehlen, ausführlichen Erklärungen und praktischen Beispielen – ideal als Hilfeseite oder Cheatsheet. Du kannst sie direkt kopieren und als Datei speichern, z. B. unter dem Namen `docker-compose-hilfe.md`.

---

```markdown
# 🐳 Docker Compose – Befehle, Beispiele & Erklärungen

Eine umfassende Übersicht aller wichtigen `docker-compose` Befehle mit praktischen Beispielen für Entwicklung, Debugging und Deployment.

---

## 🔧 Grundbefehle

### Dienste starten

```bash
docker-compose up
```
Startet alle Dienste laut `docker-compose.yml`. Baut Images, falls nötig.

```bash
docker-compose up --build
```
Erzwingt Neubau der Images vor dem Start – nützlich nach Änderungen am Dockerfile.

```bash
docker-compose up -d
```
Startet Dienste im Hintergrund (Detached Mode), ideal für Serverbetrieb.

**Beispiel:**
```bash
docker-compose up -d --build
```
Startet alles im Hintergrund und baut neu.

---

### Dienste stoppen und entfernen

```bash
docker-compose down
```
Stoppt alle Container und entfernt Netzwerke, Volumes und Images (optional).

```bash
docker-compose stop
```
Stoppt laufende Container, ohne sie zu entfernen.

```bash
docker-compose start
```
Startet gestoppte Container erneut.

```bash
docker-compose restart
```
Startet alle Dienste neu – nützlich nach Konfigurationsänderungen.

**Beispiel:**
```bash
docker-compose down --volumes
```
Entfernt zusätzlich alle Volumes (Daten!).

---

## 📋 Status & Logs

### Status anzeigen

```bash
docker-compose ps
```
Zeigt Status der Dienste (Container, Ports, Zustand).

### Logs anzeigen

```bash
docker-compose logs
```
Zeigt Logs aller Dienste.

```bash
docker-compose logs -f
```
Live-Logs wie `tail -f`.

**Beispiel:**
```bash
docker-compose logs web
```
Zeigt nur die Logs des Dienstes `web`.

---

## 🏗️ Images & Registry

### Images bauen

```bash
docker-compose build
```
Baut alle Images laut Compose-Datei.

```bash
docker-compose build <dienst>
```
Baut nur das Image eines bestimmten Dienstes.

### Images holen & pushen

```bash
docker-compose pull
```
Holt Images aus Registry (z. B. Docker Hub).

```bash
docker-compose push
```
Schiebt Images in Registry – nützlich für Deployment.

---

## 🧪 Interaktion mit Containern

### Befehle im Container ausführen

```bash
docker-compose exec <dienst> <befehl>
```
Führt einen Befehl im laufenden Container aus.

**Beispiel:**
```bash
docker-compose exec web bash
```
Öffnet eine Bash-Shell im `web`-Container.

### Temporäre Container starten

```bash
docker-compose run <dienst> <befehl>
```
Startet einen temporären Container für einmalige Tasks.

**Beispiel:**
```bash
docker-compose run web python manage.py migrate
```
Führt eine Django-Migration aus.

---

## 🛠️ Diagnose & Konfiguration

### Konfiguration prüfen

```bash
docker-compose config
```
Validiert und zeigt die effektive Compose-Konfiguration.

### Prozesse anzeigen

```bash
docker-compose top
```
Zeigt Prozesse in den Containern.

### Version anzeigen

```bash
docker-compose version
```
Zeigt die Version von Docker Compose.

---

## 📦 Praktische Beispiele

### Beispiel 1: Flask-App starten

```bash
docker-compose up -d --build
```

### Beispiel 2: Datenbank-Logs prüfen

```bash
docker-compose logs db
```

### Beispiel 3: Bash im Container öffnen

```bash
docker-compose exec web bash
```

### Beispiel 4: Container stoppen und alles entfernen

```bash
docker-compose down --volumes --remove-orphans
```

---

## 🧠 Tipps

- Nutze `--build`, wenn du Änderungen am Dockerfile gemacht hast.
- `exec` ist ideal für Debugging oder manuelle Befehle im Container.
- `run` ist gut für einmalige Tasks (z. B. Migrationen).
- `down` entfernt auch Netzwerke und Volumes – Vorsicht bei persistenten Daten!
- Nutze `.env`-Dateien für Umgebungsvariablen in Compose-Projekten.

---

```
