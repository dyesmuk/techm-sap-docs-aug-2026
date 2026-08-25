# Day 2 — From One Container to a Fleet: Kubernetes 🚢

**Duration:** 2.5 hrs
**Vibe check:** Yesterday you ran a handful of containers by hand. Today we talk about what happens when you've got *hundreds* of them, across *multiple machines*, and they need to survive crashes, scale up on demand, and update without downtime. That's Kubernetes' entire job.

> Your lab machine already has a local Kubernetes cluster (via Kind) ready to go — check with `kubectl cluster-info` before we start.

---

## 🎯 What You'll Walk Away With
- Why Docker alone isn't enough once you're running production workloads at scale
- The core Kubernetes building blocks: Pods, ReplicaSets, Deployments, Services
- Hands-on: deploy an app to your local cluster, scale it, update it with zero downtime, and expose it
- A clear (conceptual) picture of how SAP Commerce Cloud uses this exact model in production, via AKS + Automation Engine + CI/CD

---

## Part 1: Why Kubernetes Even Exists

Picture this: you've got 50 containers running your app across 10 servers. One server dies. Now what?
- Which containers were on it?
- Who restarts them, and where?
- How does traffic get rerouted so users don't notice?

Doing this by hand doesn't scale. **Kubernetes (K8s)** is the system that watches your containers, restarts what dies, spreads load across machines, and rolls out updates without taking the app offline. Docker packages your app. Kubernetes *runs the show* at scale.

**Analogy:** Docker gives you the shipping container. Kubernetes is the entire port — cranes, scheduling, routing, the works — making sure every container ends up where it needs to be, and stays there.

### The Building Blocks

| Term | What It Is | Why It Matters |
|---|---|---|
| **Cluster** | A set of machines (nodes) working together, managed by Kubernetes | Your "fleet" |
| **Node** | A single machine (VM or physical) in the cluster | Where containers actually run |
| **Pod** | The smallest deployable unit — wraps one or more tightly-coupled containers | K8s doesn't manage containers directly; it manages Pods |
| **Architecture** | Control plane (the "brain" — scheduler, API server, etcd) + worker nodes (where Pods actually run) | You *talk to* the control plane; it decides where things go |

**Key mental model:** you never tell Kubernetes "run this container on node 3." You describe the *desired state* ("I want 3 replicas of this app running") and Kubernetes figures out the how and where — and keeps enforcing that state forever, self-healing as needed.

---

## Part 2: Kubernetes Workloads

Pods on their own are fragile — if a Pod dies, it's just gone unless something is watching it. That's where these come in:

- **ReplicaSet** — Ensures a specified number of identical Pod copies are always running. Pod crashes? ReplicaSet notices and spins up a replacement automatically.
- **Deployment** — Sits on top of ReplicaSets and adds the good stuff: rolling updates, rollbacks, version history. In practice, **you almost never create a ReplicaSet directly — you create a Deployment**, and it manages ReplicaSets for you.
- **Service** — Pods are disposable and get new IPs every time they restart. A Service gives your app a **stable network identity** (a fixed name/IP) so other things can reliably talk to it, no matter which Pods are currently backing it.

**Why this matters for SAP Commerce:** in a production SAP Commerce Cloud setup, your storefront, backoffice, and integration layers are each running as Deployments, each fronted by a Service — exactly the pattern you're about to build.

---

## Part 3: Cloud Deployment — The Bigger Picture

This part is conceptual (your local cluster won't fully replicate an enterprise Azure setup, but the mental model transfers 1:1):

- **Azure Kubernetes Service (AKS)** — This is where SAP Commerce Cloud's Kubernetes clusters actually run in production — a managed K8s service on Azure, so SAP handles the control-plane maintenance and you focus on workloads.
- **Automation Engine** — SAP Commerce Cloud's own orchestration layer that manages builds, deployments, and environment provisioning on top of AKS — it's the piece that takes your code commit and turns it into a running environment.
- **CI/CD** — Every code change flows through an automated pipeline: build → test → containerize → deploy. This is what makes "update without downtime" a routine event instead of a stressful one.

Put together: **you push code → CI/CD builds and tests it → Automation Engine deploys it → AKS runs it as Pods/Deployments/Services**, self-healing and scaling the whole time.

---

## 🧪 Hands-On Lab

*Sanity check first:* `kubectl cluster-info` and `kubectl get nodes` — both should return clean output.

### Lab 1: Deploy Your First App
```bash
kubectl create deployment demo-app --image=nginx:alpine --replicas=2
kubectl get deployments
kubectl get pods
```
Notice: two Pods spun up automatically. That's the Deployment enforcing your desired state.

### Lab 2: Expose It with a Service
```bash
kubectl expose deployment demo-app --port=80 --type=NodePort
kubectl get services
```
Grab the assigned NodePort and hit it (or use `kubectl port-forward deployment/demo-app 8080:80` and browse `localhost:8080`).

### Lab 3: Watch Self-Healing in Action
```bash
kubectl get pods
kubectl delete pod <one-of-the-pod-names>
kubectl get pods
```
The Pod you deleted is gone — but a new one appears almost instantly. That's the ReplicaSet doing its job, no human intervention needed.

### Lab 4: Scale on Demand
```bash
kubectl scale deployment demo-app --replicas=5
kubectl get pods
```
Five Pods, on command. This is the exact mechanism behind "handle the Black Friday spike."

### Lab 5: Rolling Update — Zero Downtime
```bash
kubectl set image deployment/demo-app nginx=nginx:latest
kubectl rollout status deployment/demo-app
kubectl rollout history deployment/demo-app
```
Watch how Pods get replaced gradually, not all at once — that's how you deploy updates without taking the app down. If something goes wrong, `kubectl rollout undo deployment/demo-app` rolls it right back.

### Cleanup
```bash
kubectl delete service demo-app
kubectl delete deployment demo-app
```

---

## ✅ Quick Recap Check

1. What's the actual difference between a **Pod** and a **Deployment** — and why don't you create Pods directly in practice?
2. In Lab 3, you deleted a Pod and a new one appeared without you doing anything. What component made that happen?
3. Why does a **Service** exist when Pods already have their own IP addresses?
4. Where does SAP Commerce Cloud's Kubernetes infrastructure actually run in production?
5. Walk through the flow: code commit → running, updated production Pod. What are the stages in between?

---

## 👀 Coming Up on Day 3 & 4
We move from *infrastructure* to *SAP Commerce itself* — integration architecture, patterns, APIs, security, and monitoring. This is where Commerce starts talking to the outside world.
