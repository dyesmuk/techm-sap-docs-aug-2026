# Day 12 — Tokens, End to End 🎫

**Duration:** 2.5 hrs
**Vibe check:** You've configured OAuth clients (Day 11) and used tokens as a caller (Day 4). Today ties it all together — you'll generate tokens yourself, inspect what's actually inside one, and deliberately test what happens when validation fails.

---

## 🎯 What You'll Walk Away With
- Confidence generating and using access tokens end-to-end, not just following steps
- An understanding of what's actually *inside* a token (it's not just a random string)
- Hands-on experience with token expiry and validation failures — the stuff that actually causes production incidents

---

## Part 1: What's Actually Inside a Token

Most OAuth access tokens in SAP's ecosystem are **JWTs (JSON Web Tokens)** — and despite looking like gibberish, they're just Base64-encoded JSON with a signature. A JWT has three parts separated by dots: `header.payload.signature`.

The **payload** contains claims like:
- `exp` — expiry timestamp (this is why tokens are short-lived by design)
- `scope` — what this token is actually allowed to do
- `client_id` / `sub` — who this token was issued to

**Why this matters:** a token isn't just "yes/no access" — it carries *scoped, time-limited* permissions. A well-designed API checks not just "is this token valid" but "does this token's scope actually permit this specific action."

### Securing APIs vs. Validating Tokens
These are two different jobs:
- **Securing an API** — deciding a token is *required* to call it (what you did Day 11 on the Sender adapter)
- **Validating a token** — checking the token presented is genuine, unexpired, and scoped correctly (what happens automatically, but you should understand *why* it can fail)

---

## 🧪 Hands-On Lab

### Lab 1: Generate a Token and Decode It
```bash
curl -X POST "https://<your-auth-host>/oauth/token" \
  -d "grant_type=client_credentials" \
  -d "client_id=<client-id>" \
  -d "client_secret=<client-secret>"
```
Copy the `access_token` value and decode it (paste into [jwt.io](https://jwt.io) or decode the payload manually with `echo '<payload-part>' | base64 -d`). Identify the `exp`, `scope`, and `client_id` claims.

### Lab 2: Use It Against Your Secured Endpoint
Call your Day 11 secured iFlow endpoint with this token in the `Authorization: Bearer` header — confirm success.

### Lab 3: Test Expiry
Note the token's `exp` timestamp from Lab 1. Wait until it passes (or use a token you generated earlier in the program), then retry the same call. Confirm you now get a rejection — and note the specific error message/status code.

### Lab 4: Test a Wrong Scope (If Configurable)
If your setup allows scoped tokens, generate a token with a narrower scope than the endpoint requires, and confirm the API rejects it even though the token itself is technically valid and unexpired. This demonstrates: **valid token ≠ automatically authorized for everything.**

### Lab 5: Full Round Trip
Put it all together — generate a fresh token, call your Day 9 shipping integration (now secured, per Day 11) with it end-to-end, and confirm it works exactly like your Day 9 test did, but now properly authenticated on both the inbound and outbound legs.

---

## ✅ Quick Recap Check

1. What are the three parts of a JWT, and what does each roughly contain?
2. Why are access tokens deliberately short-lived instead of permanent?
3. What's the difference between a token being "valid" and a token being "authorized" for a specific action?
4. In Lab 3, what response did you get once the token expired, and how would a well-built client be expected to react?
5. Why might an API reject a technically valid, unexpired token (as in Lab 4)?

---

## 👀 Coming Up on Day 13
We shift focus to **OData** — consuming real data from your S/4HANA sandbox with GET operations, filtering, sorting, and pagination.
