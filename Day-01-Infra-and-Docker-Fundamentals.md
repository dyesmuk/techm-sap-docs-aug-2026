# Day 1 — Setting the Stage: Cloud Infra + Docker 🐳

**Duration:** 2.5 hrs
**Vibe check:** Today we zoom out and look at *where* SAP Commerce actually lives (spoiler: the cloud), then get hands-on with Docker — the tech that makes "works on my machine" a non-issue.

> Your lab environment already has Docker up and running — no setup grind here, straight to building stuff.

---

## 🎯 What You'll Walk Away With
- The big picture of SAP Commerce Cloud infra and what "cloud-native commerce" actually means
- A solid working model of Docker — images, containers, volumes, networking, compose
- Hands dirty with real Docker workflows: building a custom image, persisting data, wiring up multi-container apps

---

## Part 1: Infrastructure Overview

### SAP Commerce Cloud, in Plain English
Forget racks of servers in a basement. SAP Commerce Cloud is SAP's fully managed home for your e-commerce platform — they handle the infra, scaling, patching, and uptime headaches, so dev teams focus on building the actual storefront experience.

Think of it like renting a fully-serviced apartment vs. building a house from scratch. You still customize the inside (commerce logic, storefront, integrations) — but the plumbing, electricity, and foundation? Already sorted.

### Cloud-Native Commerce — Why It's a Big Deal
"Cloud-native" isn't just marketing fluff. It means the app is *built* to run in the cloud from day one:
- **Scales on demand** — Black Friday traffic spike? No sweat.
- **Resilient** — one component fails, the rest keeps running.
- **Containerized & orchestrated** — which is exactly what today's lab is about, and what Kubernetes (Day 2) builds on top of.

This is the shift from "monolith on one big server" to "a bunch of independent, portable services that can spin up anywhere."

---

## Part 2: Docker Fundamentals

### The Core Trio

| Concept | What It Actually Is | Real-World Analogy |
|---|---|---|
| **Docker Architecture** | Client-server model — the Docker CLI talks to the Docker daemon, which does the heavy lifting | You (client) order food; the kitchen (daemon) cooks it |
| **Images** | Read-only blueprint/snapshot of an app + its dependencies | A recipe card 📋 |
| **Containers** | A running instance of an image — live, isolated, disposable | The actual dish, cooked and served 🍜 |

**Key mindset shift:** Images are static. Containers are alive. You can spin up 10 containers from the same image, and each runs independently.

### Docker Components That Make It Production-Worthy
- **Volumes** — Containers are disposable; your data shouldn't be. Volumes let data survive even after a container is deleted.
- **Networking** — How containers talk to each other and the outside world. Critical once you're running multi-container setups (app + DB + search engine, etc.).
- **Docker Compose** — Describe your whole multi-container setup in one YAML file, spin it all up with a single command. This is how real dev environments get managed.

---

## 🧪 Hands-On Lab

*Environment check: run `docker info` — if it responds cleanly, you're ready to go.*

### Lab 1: Build Your Own Image
Create a `Dockerfile` for a minimal app (we'll use a simple Nginx-based static page as our example — swap in any app you like):

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```

Build and run it:
```bash
docker build -t my-first-image .
docker run -d -p 8080:80 --name my-container my-first-image
```
Visit `http://localhost:8080` — that's your custom image, alive as a container.

### Lab 2: Volumes — Make Data Survive
```bash
docker volume create commerce-data
docker run -d -v commerce-data:/data --name data-container alpine tail -f /dev/null
docker exec data-container sh -c "echo 'persisted!' > /data/test.txt"
docker rm -f data-container
docker run -d -v commerce-data:/data --name data-container-2 alpine tail -f /dev/null
docker exec data-container-2 cat /data/test.txt
```
Notice: the container got destroyed and recreated, but the data lived on. That's the whole point.

### Lab 3: Networking — Two Containers, One Conversation
```bash
docker network create commerce-net
docker run -d --network commerce-net --name backend alpine tail -f /dev/null
docker run -it --network commerce-net --name frontend alpine ping -c 3 backend
```
Containers on the same network can resolve each other **by name** — no hardcoded IPs needed. This is exactly how SAP Commerce's app + DB + search containers will talk to each other later in the program.

### Lab 4: Docker Compose — Spin Up a Mini Stack
Create a `docker-compose.yml`:
```yaml
version: "3.8"
services:
  web:
    image: nginx:alpine
    ports:
      - "8081:80"
  cache:
    image: redis:alpine
```
```bash
docker compose up -d
docker compose ps
docker compose down
```
One file, two services, one command to rule them all. This pattern is exactly how you'll spin up multi-service dev environments going forward.

---

## ✅ Quick Recap Check

1. What's the key difference between a Docker **image** and a **container**?
2. Why does SAP position SAP Commerce Cloud as "cloud-native" rather than just "cloud-hosted"?
3. In Lab 2, why did the data survive even after the container was removed?
4. In Lab 3, how did the `frontend` container reach `backend` without an IP address?
5. What problem does Docker Compose solve that plain `docker run` commands don't?

*(Save your answers — quick rapid-fire review at the start of Day 2 before we move into Kubernetes.)*

---

## 👀 Coming Up on Day 2
We go from "a couple of containers on one machine" to "a fleet of containers, orchestrated across a cluster." Enter **Kubernetes**.
