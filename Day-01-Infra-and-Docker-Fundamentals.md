# Day 1 — Setting the Stage: Cloud Infra + Docker 🐳

**Duration:** 2.5 hrs
**Vibe check:** Today we zoom out and look at *where* SAP Commerce actually lives (spoiler: the cloud), then get our hands dirty with Docker — the tech that makes "works on my machine" a thing of the past.

---

## 🎯 What You'll Walk Away With
- The big picture of SAP Commerce Cloud infra and what "cloud-native commerce" even means
- A working mental model of Docker — images, containers, the whole deal
- Docker installed, verified, and your first container up and running

---

## Part 1: Infrastructure Overview

### SAP Commerce Cloud, in Plain English
Forget racks of servers in a basement. SAP Commerce Cloud is SAP's fully managed home for your e-commerce platform — they handle the infra, scaling, patching, and uptime headaches, so dev teams can focus on building the actual storefront experience.

Think of it like renting a fully-serviced apartment vs. building a house from scratch. You still customize the inside (your commerce logic, storefront, integrations) — but the plumbing, electricity, and foundation? Already sorted.

### Cloud-Native Commerce — Why It's a Big Deal
"Cloud-native" isn't just marketing fluff. It means the app is *built* to run in the cloud from day one:
- **Scales on demand** — Black Friday traffic spike? No sweat.
- **Resilient** — one component fails, the rest keeps running.
- **Containerized & orchestrated** — which is exactly what we're about to learn.

This is the shift from "monolith running on one big server" to "a bunch of independent, portable services that can spin up anywhere."

---

## Part 2: Docker Fundamentals

### Why Docker Exists
Every dev has said it: *"but it works on my machine."* Docker kills that excuse. It packages your app + everything it needs (libraries, configs, runtime) into one portable unit that runs identically everywhere — your laptop, a colleague's laptop, or a production server.

### The Core Trio

| Concept | What It Actually Is | Real-World Analogy |
|---|---|---|
| **Docker Architecture** | Client-server model — the Docker CLI talks to the Docker daemon, which does the heavy lifting | You (client) order food; the kitchen (daemon) cooks it |
| **Images** | Read-only blueprint/snapshot of an app + its dependencies | A recipe card 📋 |
| **Containers** | A running instance of an image — live, isolated, disposable | The actual dish, cooked and served 🍜 |

**Key mindset shift:** Images are static. Containers are alive. You can spin up 10 containers from the same image, and each one runs independently.

---

## Part 3: Docker Components

Once you're past the basics, three components make Docker actually *useful* for real apps:

- **Volumes** — Containers are disposable; your data shouldn't be. Volumes let data survive even if the container gets deleted. Think of it as external storage that outlives the container's lifecycle.
- **Networking** — How containers talk to each other (and the outside world). Essential once you're running multi-container setups (like SAP Commerce + a database + a search engine).
- **Docker Compose** — Instead of manually starting five containers with five long commands, you describe your whole multi-container setup in one YAML file and spin it all up with a single command. This is how real-world dev environments are managed.

---

## 🧪 Hands-On Lab

### Step 1: Install Docker
Grab **Docker Desktop** (Windows/Mac) or **Docker Engine** (Linux) from [docker.com](https://www.docker.com/products/docker-desktop/).

### Step 2: Verify Installation
```bash
docker --version
docker info
```
If both commands return clean output (no errors), you're good.

### Step 3: Run Your First Container
```bash
docker run hello-world
```
This pulls a tiny test image and runs it. If you see a "Hello from Docker!" message — congrats, your setup works end to end (pull → create → run).

### Step 4: Poke Around
```bash
docker ps -a          # see all containers (running + stopped)
docker images         # see images you've downloaded
docker run -it ubuntu bash   # spin up an interactive Ubuntu container and explore inside it
```
Type `exit` to leave the container shell.

---

## ✅ Quick Recap Check

1. What's the key difference between a Docker **image** and a **container**?
2. Why does SAP position SAP Commerce Cloud as "cloud-native" rather than just "cloud-hosted"?
3. If you delete a container, does your data automatically disappear? What's the fix?
4. What command lets you run multiple containers together using a single config file?
5. What's the real-world problem Docker was built to solve?

*(Save your answers — we'll do a rapid-fire review at the start of Day 2 before moving into Kubernetes.)*

---

## 👀 Coming Up on Day 2
We go from "one container running" to "a fleet of containers, orchestrated." Enter **Kubernetes**.
