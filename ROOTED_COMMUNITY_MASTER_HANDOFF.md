# 🌱 ROOTED Community — Master Handoff (UI + Backend)

Status: Only live vertical  
Scope: ROOTED Community only  
Backend: Locked & governed via ROOTED Core  
Remaining Work: UI, UX, QA polish only  

If app behavior and this document conflict → this document wins.

---

## 1. What ROOTED Community Is

Public-facing cultural + food + community layer of ROOTED.

Includes:

- Farms, markets, vendors  
- Experiences & events  
- Landmarks & education  
- Seasonal & cultural discovery  
- Kids Education Mode (design complete, pilot OFF)

Is:

✅ Public  
✅ Non-political  
✅ Non-religious by default  
✅ Safety-first  
✅ Not paywalled for discovery  

Is NOT:

❌ Job board  
❌ Construction system  
❌ Healthcare system  
❌ Gig economy  
❌ Open social network  

---

## 2. Roles & Access (Backend-Enforced)

All access controlled by:

- `public.user_tiers`
- `feature_flags`
- Admin Governance Layer

### 2.1 Guest

Can:

- Browse vendors, events, landmarks  
- View seasonal overlays  

Cannot:

- Use marketplaces  
- View analytics  
- Message providers  

---

### 2.2 Individual / Community Member

Same as Guest, plus identity.

Cannot:

- Use procurement
- Act as provider
- Use dashboards

Kids Mode surfaces OFF at Community launch.

---

### 2.3 Vendors

Shared powers:

- Provider profile (after approval)
- Media uploads
- Events & experiences

Tier Rules:

**FREE**

- Bulk marketplace: optional / locked by default
- Bids: ❌
- Basic analytics: optional
- Advanced: ❌

**PREMIUM**

- Bulk marketplace: ✅
- Bids: ❌
- Basic analytics: ✅
- Advanced: ❌

**PREMIUM PLUS**

- Bulk: ✅
- Bids: ✅
- Basic: ✅
- Advanced: ✅

**Founding Vendor Rule**

First 3 approved:

- Lifetime Premium
- 50% Premium+ upgrade forever
- Enforced via feature flags only

---

### 2.4 Institutions

- Discoverable
- Host events
- Anchor education

Tier parity with vendors enforced in Core.

---

### 2.5 Sanctuaries & Rescues

✅ Volunteer & education only  
❌ No Premium tools  
❌ No markets  
❌ No ads  

Access via:

`provider_type = nonprofit_sanctuary`

---

### 2.6 Admin

Defined strictly by:

- `role = admin`
- `account_status = active`

Admins:

- Govern accounts
- Moderate content
- Manage seasonal features

Admins do NOT bypass markets.

---

## 4. Kids Mode (Design-Complete, Pilot OFF)

At Community launch:

- ❌ Kids UI disabled
- ✅ No kids monetization enforced now

When enabled in Education vertical:

- Only kids-safe content
- No commerce
- No uploads
- No messaging

---

Remaining sections (maps, moderation, analytics, holidays) inherit from ROOTED Core & Platform governance.
