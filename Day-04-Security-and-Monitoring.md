# Day 4 — Lock It Down, Watch It Run: Security & Monitoring 🔐

**Duration:** 2.5 hrs
**Vibe check:** Yesterday you called OCC APIs freely. Today: why that shouldn't fly in production, how OAuth fixes it, how event-driven architecture keeps systems loosely coupled, and how you actually know something's wrong before a customer tells you.

---

## 🎯 What You'll Walk Away With
- A real grasp of OAuth 2.0 — not just the buzzword, but the actual flow
- Why event-driven architecture is the backbone of scalable integrations
- Hands-on: hit a protected endpoint two ways (unauthenticated vs. token-secured), then explore Commerce's monitoring tools

---

## Part 1: APIs & Security

### Event-Driven Architecture, Revisited
Quick recall from Day 3: instead of System A directly calling System B (and waiting), System A fires an **event** ("order placed") and any system that cares can react — independently, at its own pace.

**Why this matters at scale:** if Commerce had to synchronously wait on the shipping system, the marketing system, *and* the loyalty system every time an order was placed, checkout would be painfully slow and fragile — one slow system blocks everyone. Event-driven decouples all of that.

### Integration APIs — The Contract Layer
Every integration point (OCC, CPI-brokered connections, etc.) is really just a **contract**: "send me data in this shape, and I'll respond in this shape." APIs are how that contract gets enforced and documented — which is exactly why API design (versioning, clear error codes, predictable payloads) matters so much in integration-heavy systems like Commerce.

### OAuth 2.0 — Actually Understanding It
Forget the acronym soup for a second. The problem OAuth solves: **how does a system prove it's allowed to access an API, without passing around a raw username/password everywhere?**

The flow you'll use most in this program (**Client Credentials Flow** — for system-to-system, no human involved):
1. Your client (an app/service) sends its `client_id` + `client_secret` to a token endpoint
2. The auth server verifies and issues an **access token** (a short-lived, signed string)
3. Your client attaches that token to every subsequent API call: `Authorization: Bearer <token>`
4. The API checks the token's validity before doing anything

**Key insight:** the token is temporary and scoped — if it leaks, the blast radius is limited (it expires, and it typically can't do *everything* your actual credentials could).

---

## Part 2: Monitoring & Performance

### Why This Isn't Optional
An integration that works today can silently break tomorrow — an external API changes its response shape, a token expires and isn't refreshed, a cronjob starts timing out. Monitoring is how you catch this **before** it becomes a customer-facing incident.

### What You Watch, in Commerce
- **Cronjobs / background processes** (HAC → System → Monitoring) — did the nightly catalog sync actually finish, or silently fail halfway?
- **Error logs** — Commerce logs failed API calls, failed jobs, and exceptions; knowing where to look saves hours of guessing
- **Performance metrics** — response times on OCC calls, Solr query performance, thread/session usage under load

### Error Handling — Fail Loud, Fail Useful
A well-built integration doesn't just "fail" — it fails in a way that tells you *what* broke and *why*: meaningful HTTP status codes (401 vs. 500 vs. 503 mean very different things), structured error payloads, and retry logic where it makes sense (transient network blip) vs. where it doesn't (bad credentials — retrying won't help).

---

## 🧪 Hands-On Lab

### Lab 1: Hit a Protected Endpoint Without a Token
```bash
curl -i "https://<your-commerce-host>/occ/v2/<basesite>/users/current"
```
Note the response — you should get a **401 Unauthorized** (or similar). This is the API correctly refusing an unidentified caller.

### Lab 2: Get an OAuth Token (Client Credentials Flow)
```bash
curl -X POST "https://<your-commerce-host>/authorizationserver/oauth/token" \
  -d "grant_type=client_credentials" \
  -d "client_id=<your-client-id>" \
  -d "client_secret=<your-client-secret>"
```
You'll get back a JSON response with an `access_token`. Copy it.

### Lab 3: Call the Same Endpoint, Authenticated
```bash
curl -i "https://<your-commerce-host>/occ/v2/<basesite>/users/current" \
  -H "Authorization: Bearer <access_token>"
```
Compare this response to Lab 1. Same endpoint, wildly different outcome — that's the whole value of token-based security in one side-by-side.

### Lab 4: Go Monitoring-Hunting in HAC
Head back into **HAC → System → Monitoring**:
- Find the list of cronjobs and check their last-run status (success/error)
- Pick one job and open its execution log — what does a "successful" log entry look like vs. a failed one?
- If you can find one, look at a recent error log entry — what information does it give you to diagnose the issue?

### Lab 5: Break It on Purpose
Repeat Lab 3 but with a deliberately wrong/expired token. Observe the error response. What status code and message do you get? How would a well-built client know to refresh its token vs. give up?

---

## ✅ Quick Recap Check

1. Walk through the Client Credentials Flow in your own words — what gets exchanged, in what order?
2. Why is event-driven architecture generally preferred over synchronous calls for things like "order placed → notify 5 downstream systems"?
3. What's the practical difference between a 401 and a 500 response, and why does that difference matter for how a client should react?
4. Where in Commerce would you check whether last night's catalog sync actually succeeded?
5. Why is retrying automatically a good idea for a network timeout, but a bad idea for a bad-credentials error?

---

## 👀 Coming Up on Day 5
We zoom out again — a tour of the extended integration landscape: SAP CPI/Integration Suite, OData, SAP BTP, and how S/4HANA fits into all of this. Setting the stage before we go hands-on with Integration Suite starting Day 6.
