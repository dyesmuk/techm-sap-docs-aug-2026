# Day 11 — Configuring OAuth Clients, Properly 🔑

**Duration:** 2.5 hrs
**Vibe check:** Day 4 you *used* an OAuth token as a caller. Today you're on the other side — configuring the OAuth clients and credentials that iFlows themselves use, both for accepting inbound calls and authenticating outbound ones.

---

## 🎯 What You'll Walk Away With
- Clarity on the two directions OAuth matters in CPI: securing your iFlow's inbound endpoint, and authenticating your iFlow's outbound calls to other systems
- A configured OAuth client, stored securely in Integration Suite's credential store
- An iFlow updated to actually use it

---

## Part 1: Two Directions, One Concept

Here's the distinction that matters today: **inbound security** (who's allowed to call *my* iFlow) vs. **outbound security** (how does *my* iFlow authenticate when calling someone else's API).

- **Inbound** — your HTTP Sender adapter can require OAuth, so random unauthenticated callers can't trigger your flow (same principle as Day 4, just configured on the CPI side this time)
- **Outbound** — your HTTP Receiver adapter, when calling an external system (like yesterday's shipping API), often needs to attach its own credentials — and you don't want those hardcoded in the iFlow itself

### Where Credentials Actually Live
CPI has a dedicated **Security Material** store (under Monitor → Manage Security → Security Material). Credentials — OAuth clients, certificates, user credentials — get stored there *once*, then referenced by name inside iFlows. This means:
- Credentials aren't hardcoded into flow logic
- Rotating a secret means updating it in one place, not hunting through every iFlow that uses it

This is a security best practice worth internalizing beyond just SAP: **never hardcode secrets into integration logic.**

---

## 🧪 Hands-On Lab

### Lab 1: Create an OAuth2 Client Credentials Artifact
In **Cloud Integration → Monitor → Manage Security → Security Material**:
- Create a new **OAuth2 Client Credentials** artifact
- Give it a name (e.g., `shipping-api-oauth`), and fill in a client ID/secret (use dummy/test values if no real provider is available)

### Lab 2: Secure Your Inbound Endpoint
Go back to yesterday's (or Day 8's) iFlow. On the **HTTP Sender** adapter, change the authentication setting from "none" to **OAuth2 Client Credentials** (or Basic Auth as a simpler alternative if OAuth isn't available in your trial setup), pointing to a security artifact.
- Redeploy
- Try calling it **without** credentials — confirm it now gets rejected
- Call it again **with** the correct credentials — confirm it succeeds

### Lab 3: Reference the Credential in an Outbound Call
On your Day 9 iFlow's **HTTP Receiver** adapter (calling the shipping API), set its authentication to reference the `shipping-api-oauth` artifact you created in Lab 1, instead of leaving it unauthenticated.

### Lab 4: Rotate a Secret
Go back into Security Material and update the client secret for `shipping-api-oauth`. Note: you didn't have to touch the iFlow itself at all — that's the entire point of centralizing credentials.

---

## ✅ Quick Recap Check

1. What's the practical difference between securing an iFlow's inbound endpoint vs. its outbound calls?
2. Why does CPI store credentials separately in Security Material instead of letting you type them directly into an adapter's config?
3. What did Lab 4 demonstrate about the benefit of centralized credential storage?
4. If an external partner rotates their API key on their end, what's the minimum change you'd need to make on your side?
5. Why is "never hardcode secrets into integration logic" good practice beyond just SAP CPI?

---

## 👀 Coming Up on Day 12
We go deeper into the token mechanics — running the full Client Credentials Flow yourself, generating and validating access tokens, and securing APIs end-to-end.
