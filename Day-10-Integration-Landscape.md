# Day 10 — The Wider Integration Landscape 🗺️

**Duration:** 2.5 hrs
**Vibe check:** You've now hand-built the core integration pattern (Day 8-9). Today's a bit different — a guided tour of the other integrations that show up in real SAP Commerce projects, so you recognize them by name and know roughly what each does, even without building all of them from scratch this week.

---

## 🎯 What You'll Walk Away With
- A working vocabulary for headless commerce, payment integrations, OMS, Data Hub, Marketing Cloud, and Qualtrics integrations
- Enough context to know *which* integration pattern from Day 3 each one typically uses
- A look at where these integration points actually surface in your sample Commerce instance

---

## Part 1: The Cast of Integrations

### Headless Commerce
"Headless" means the commerce **backend** (catalog, cart, pricing, orders) is fully decoupled from the **frontend** (storefront UI) — they talk purely through APIs (OCC, which you've already used). This is *exactly* what lets you swap in Spartacus, a mobile app, or a voice assistant as the frontend without touching backend logic. You've been working headless-style since Day 3 without necessarily labeling it that way.

### Payment Integrations
Commerce doesn't process payments itself — it integrates with payment service providers (PSPs) via their APIs. Typically synchronous at checkout (authorize the payment) with async follow-up (capture, refund, webhook notifications for status changes). This is a textbook mix of the sync and event-driven patterns from Day 3.

### OMS (Order Management System)
Once an order's placed, a lot happens outside Commerce: inventory allocation, fulfillment routing, returns. Larger implementations offload this to a dedicated OMS, with Commerce and OMS syncing order state back and forth — usually event-driven, so Commerce doesn't sit blocked waiting on fulfillment logic.

### SAP Data Hub
A data orchestration platform for larger-scale data movement and pipelines across systems — think less "single order sync" and more "nightly batch pipeline moving catalog data across five systems." This is the batch/scheduled pattern from Day 3, at enterprise scale.

### Marketing Cloud Integration
Feeds customer behavior and order data from Commerce into SAP Marketing Cloud, powering targeted campaigns, personalization, and segmentation. Mostly event-driven — actions in Commerce (purchase, cart abandonment) trigger marketing workflows elsewhere.

### Qualtrics Integration
Post-purchase or post-support experience surveys, triggered from Commerce events (order delivered, support ticket closed) and fed back as customer experience (CX) data. Small in scope, but a good example of how even "soft" data (satisfaction scores) gets wired into the same integration fabric as transactional data.

---

## Part 2: Spot the Pattern

Notice something? Every single integration above maps back to a pattern from Day 3 (sync REST, event-driven, batch, or middleware-brokered). That's the actual point of today: **you don't need to memorize six new systems — you need to recognize which of the four patterns each one is wearing.**

---

## 🧪 Hands-On Lab

### Lab 1: Find the Payment Config
In **Backoffice**, locate the **Payment Provider** configuration for your sample site (usually under a Commerce/Site Config section). Note what provider is configured and what settings are exposed (API keys, endpoint URLs, webhook config).

### Lab 2: Trace a Headless Call
Using Postman, re-run one of your OCC calls from Day 3/9 and specifically note: nothing in that response assumes a particular frontend. Confirm you could theoretically hand this exact JSON to a totally different frontend (mobile app, voice assistant) and it'd work identically. That's headless in practice, not just in definition.

### Lab 3: Design an Event Map
On paper (or a shared doc), sketch out: for an "order delivered" event in Commerce, which of today's six integrations would plausibly subscribe to it, and why? (Hint: at least Qualtrics and Marketing Cloud have an obvious reason to care.)

### Lab 4: Classify the Six
For each of the six integrations discussed today, write down which Day 3 pattern (sync REST / event-driven / batch / middleware-brokered) it primarily uses. Compare notes with a peer — there's some legitimate room for debate on a few of these.

---

## ✅ Quick Recap Check

1. What does "headless" actually mean, and what have you been doing since Day 3 that already qualifies?
2. Why is payment processing typically a mix of synchronous and event-driven patterns rather than purely one or the other?
3. What's the practical difference in scale/purpose between a single CPI iFlow (Day 8-9) and SAP Data Hub?
4. Give one real example of data that would flow from Commerce into Marketing Cloud, and why it's useful there.
5. Why might a team choose to integrate a survey tool (Qualtrics) directly into their commerce event stream instead of sending surveys manually?

---

## 👀 Coming Up on Day 11 & 12
Back to hands-on — configuring OAuth clients properly within Integration Suite, and running through the full client credentials token flow to secure both inbound and outbound calls.
