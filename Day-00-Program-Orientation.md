# Day 0 — Welcome Aboard 🚀
### SAP Commerce (Hybris) + SAP Integration Suite + S/4HANA — Program Orientation

No lecture today. Just context, so you know exactly what you're signing up for and why the next 20 days are structured the way they are.

---

## 📦 What This Program Actually Covers

By the end of this program, you'll have hands-on exposure across four connected worlds:

| Track | What You'll Build/Do |
|---|---|
| **Cloud Infra** | Docker, Kubernetes — the foundation everything else runs on |
| **SAP Commerce Core** | Integration architecture, APIs, security, monitoring |
| **SAP Integration Suite** | iFlows, REST/OAuth integrations, OData consumption connecting Commerce ↔ S/4HANA |
| **Storefront (Spartacus/Angular)** | Homepage, product pages, cart — a real headless storefront |
| **Customization** | Extensions, Solr search config, business processes |

Think of it as: **infra → integration → storefront → customization**, in that order, each block building on the last.

---

## ⏱️ The Shape of the Program

- **20 sessions, 2.5 hrs each** — roughly 50 hours total
- Every single day includes **hands-on lab work** — this isn't a slide-deck-and-chill program
- The published schedule is a **guide, not gospel** — some days will lean lab-heavy, some concept-heavy, depending on how the group's pacing goes

---

## 🧰 Your Lab Environment (Already Provisioned)

You won't be spending training time installing things. Your environment already has:
- **SAP Commerce Cloud** with Backoffice, HAC, OCC APIs, SmartEdit, Solr, plus a sample storefront pre-loaded with products, categories, customers, and orders
- **SAP Integration Suite / BTP** — Cloud Integration (CPI), API Management, Event Mesh
- **SAP S/4HANA sandbox** as your integration target for OData
- Local dev tooling: Docker, Kubernetes tools, JDK, Maven, Git, Postman, MySQL, Solr, Tomcat, Spartacus

If anything in your environment doesn't respond the way this guide expects, flag it immediately rather than losing lab time debugging setup — that's an environment issue, not a "you" issue.

---

## 🎓 What We're Assuming You Already Know

This program moves fast because you're not starting from zero. Walking in, you should be comfortable with:
- Core Java & OOP (classes, collections, exceptions)
- REST/HTTP basics (methods, status codes, JSON)
- Basic command-line usage
- SQL / relational DB fundamentals

**Nice-to-have (not blocking, but helpful):**
- Angular/TypeScript exposure
- OAuth 2.0 concepts
- Some Docker/Kubernetes familiarity
- E-commerce domain concepts (catalogs, orders, categories)

If any of the "must-have" list feels shaky, a quick refresh before Day 1 will pay off — we won't be slowing down to cover Java basics mid-program.

---

## 🤝 How This Runs, Day to Day

- Each day = **short concept framing + real lab work + a quick recap check** at the end
- Recap questions aren't graded homework — they're a sanity check so you (and we) know the concepts landed before moving on
- Courseware lives in the GitHub repo, one file per day — pull the latest before each session
- Questions mid-lab? Ask them live. This program is dense enough that "I'll figure it out later" tends to compound

---

## 🗺️ Rough Roadmap

1. **Infra Foundations** — Docker, Kubernetes
2. **SAP Commerce Integration Basics** — architecture, patterns, security, monitoring
3. **SAP Integration Suite Deep Dive** — iFlows, REST via CPI, OAuth, OData
4. **Storefront Build** — Spartacus + Angular, from install to shopping cart
5. **Customization** — extensions, Solr, business processes
6. **Wrap-up & Q&A**

---

That's the map. Day 1 starts with cloud infra and Docker — see you there. 👋
