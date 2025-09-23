
---

## 🧰 Voraussetzungen

- Deine lokale Registry läuft unter `localhost:5000`
- Du hast ein Image gebaut, z. B. mit:

```bash
docker build -t mein-image .
```

---

## 🏷️ 1. Image taggen für die lokale Registry

Du musst das Image so taggen, dass Docker weiß, wohin es gepusht werden soll:

```bash
docker tag mein-image localhost:5000/mein-image
```

---

## 🚀 2. Image pushen zur Registry

```bash
docker push localhost:5000/mein-image
```

Wenn alles klappt, ist das Image jetzt in deiner lokalen Registry gespeichert.

---

## 📥 3. Image von der Registry ziehen

Auf demselben oder einem anderen Rechner (sofern erreichbar):

```bash
docker pull localhost:5000/mein-image
```

---

## 🔍 Registry-Inhalte prüfen

Du kannst die verfügbaren Images in deiner Registry anzeigen lassen:

```bash
curl http://localhost:5000/v2/_catalog
```

Und die Tags eines bestimmten Images:

```bash
curl http://localhost:5000/v2/mein-image/tags/list
```

---

## 🛡️ Hinweis zu Sicherheit

Standardmäßig ist die lokale Registry **nicht TLS-gesichert**. Wenn du sie produktiv nutzen willst, solltest du HTTPS aktivieren oder in deiner Docker-Konfiguration (`/etc/docker/daemon.json`) den Zugriff auf unsichere Registries erlauben:

```json
{
  "insecure-registries": ["localhost:5000"]
}
```

Danach Docker neu starten.

---

Um ein Image von **Docker Hub** in deine **lokale Registry** (z. B. auf `localhost:5000`) zu übertragen, gehst du in drei einfachen Schritten vor:

---

## 🔁 Schritt-für-Schritt: Docker Hub → Lokale Registry

### 🧱 1. Image von Docker Hub ziehen

Zuerst holst du dir das gewünschte Image von Docker Hub:

```bash
docker pull nginx:latest
```

Du kannst jedes öffentlich verfügbare Image verwenden – z. B. `python`, `redis`, `mysql`, `ubuntu`, etc.

---

### 🏷️ 2. Image umbenennen (taggen) für lokale Registry

Damit Docker weiß, dass du es in deine Registry pushen willst, musst du es neu taggen:

```bash
docker tag nginx:latest localhost:5000/nginx
```

Das neue Tag zeigt auf deine lokale Registry unter Port 5000.

---

### 🚀 3. Image in die lokale Registry pushen

Jetzt kannst du es hochladen:

```bash
docker push localhost:5000/nginx
```

Wenn alles klappt, ist das Image jetzt lokal verfügbar.

---

## 📥 Bonus: Image aus der lokalen Registry wieder ziehen

Du kannst es jederzeit wieder verwenden:

```bash
docker pull localhost:5000/nginx
```

---

## 🔍 Registry-Inhalte anzeigen

Du kannst prüfen, ob das Image drin ist:

```bash
curl http://localhost:5000/v2/_catalog
```

Und die verfügbaren Tags:

```bash
curl http://localhost:5000/v2/nginx/tags/list
```

---

