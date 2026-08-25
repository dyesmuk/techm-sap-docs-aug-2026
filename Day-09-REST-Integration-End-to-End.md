# Day 9 — REST Integration, End to End 📦

**Duration:** 2.5 hrs
**Vibe check:** Yesterday's iFlow was a warm-up. Today you build the real scenario this whole program keeps referencing: **SAP Commerce → CPI → External Shipping API** — a full round-trip integration you'll actually test with Postman.

---

## 🎯 What You'll Walk Away With
- A working REST integration flow using HTTP Sender/Receiver adapters
- Real JSON transformation between two different data shapes
- A tested, end-to-end flow, verified through Postman — not just "it deployed," but "it actually works"

---

## Part 1: The Scenario

Here's what we're building: when an order ships, SAP Commerce needs to notify an external shipping provider with the order details, in *their* expected format — which is never the same as Commerce's internal format.

```
SAP Commerce (order data) → CPI (transform + route) → External Shipping API (expects a different shape)
```

This exact pattern — internal format in, transform, external format out — is the single most common integration scenario you'll build in any real SAP project. Nail this pattern today and you've basically nailed 80% of integration work.

### The Adapters
- **HTTP Sender Adapter** — accepts the inbound call from Commerce (or whatever's simulating Commerce for our lab)
- **HTTP Receiver Adapter** — makes the outbound call to the shipping API, with its own headers, auth, and endpoint config

### JSON Transformation
Not every mapping needs the full Message Mapping visual tool — sometimes a lightweight approach (Groovy script or a JSON-to-JSON mapping step) is faster for straightforward reshaping. Today you'll try this leaner approach as an alternative to yesterday's graphical mapper.

---

## 🧪 Hands-On Lab

### Lab 1: Build the Flow Skeleton
- New iFlow: `commerce-to-shipping`
- **HTTP Sender** adapter — this is where Commerce's order-shipped event would land
- **HTTP Receiver** adapter — pointing at a mock shipping endpoint (again, `httpbin.org/post` works great for testing without needing a real external system)

### Lab 2: Transform the Payload
Incoming (Commerce-style):
```json
{ "orderId": "1001", "shippingAddress": "12 MG Road, Hyderabad", "weight_kg": 2.5 }
```
Shipping API expects:
```json
{ "reference": "1001", "destination": "12 MG Road, Hyderabad", "package_weight": 2.5 }
```
Add a **Groovy Script** step (or JSON-to-JSON mapping) that reads the incoming JSON and rewrites it into the target shape. This is a common real-world task — field renames, unit conversions, restructuring nested objects.

### Lab 3: Deploy
Deploy the iFlow and confirm it shows as **Started** in the Integration Content list.

### Lab 4: Test via Postman
Open Postman and send a POST request to your iFlow's endpoint with the Commerce-style payload from Lab 2. Check:
- Response status (should be 200/success)
- The mock endpoint's echoed response — confirm the payload it received matches your *transformed* shape, not the original

### Lab 5: Trace It in Monitor
Back in **Cloud Integration → Monitor**, open this run and step through it — confirm you can see the payload before and after your transformation step, side by side.

---

## ✅ Quick Recap Check

1. Why is "internal format → transform → external format" such a common integration pattern?
2. What's the difference in role between the HTTP Sender and HTTP Receiver adapters in this flow?
3. When might a lightweight Groovy/JSON transformation be preferable to the full graphical Message Mapping tool?
4. In Lab 4, how did you confirm the transformation actually worked — what did you check?
5. If the shipping API required an API key in its headers, where in the flow would you add that?

---

## 👀 Coming Up on Day 10
A tour of the wider SAP Commerce integration landscape — headless commerce, payment integrations, OMS, Data Hub, Marketing Cloud, and Qualtrics — so you know what's out there beyond what we've hands-on built so far.
