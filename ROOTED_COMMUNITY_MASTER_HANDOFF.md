# ROOTED Community — Master Handoff (UI + Backend)

**Status:** Live Vertical  
**Scope:** ROOTED Community ONLY  
**Excludes:** Construction, Healthcare, Emergency, Workforce  
**Backend:** Hardened & Governed  
**Remaining Work:** UI / UX polish, frontend wiring, visual QA

This document is the single source of truth for ROOTED Community.

---

## 1. What ROOTED Community IS

ROOTED Community is the **public-facing cultural + food + community layer** of the ROOTED platform.

It includes:

- Farms
- Markets
- Food vendors
- Experiences
- Events
- Landmarks
- Kids Education Mode
- Seasonal + Holiday Intelligence
- Community Discovery
- Public Maps

It is:
✅ Always public  
✅ Non-political  
✅ Non-religious by default  
✅ Safety-first  
✅ Kids-safe where flagged  
✅ Not paywalled for discovery  

It is NOT:
❌ A job board  
❌ A construction system  
❌ A healthcare system  
❌ A bidding marketplace for regular users  
❌ A social network with open comments (likes only)

---

## 2. Roles & Access (ENFORCED BY BACKEND)

### Public / Guest
- Can browse vendors
- Can view maps
- Can view events
- Can view landmarks
- ❌ CANNOT access any marketplace
- ❌ CANNOT see bids, RFQs, bulk, analytics

### Individual / Community Member
- Same as Guest
- Kids Mode available via parent flow
- ❌ Still NO access to the marketplace

### Vendor — FREE
- Can create public profile
- Can post media
- Can create experiences
- ✅ can_use_bulk_marketplace: optional (allowed if enabled)
- ❌ can_use_bid_marketplace: false
- ✅ can_view_basic_analytics: optional
- ❌ can_view_advanced_analytics: false

### Vendor — PREMIUM
- ✅ can_use_bulk_marketplace: true
- ❌ can_use_bid_marketplace: false
- ✅ can_view_basic_analytics: true
- ❌ can_view_advanced_analytics: false

### Vendor — PREMIUM PLUS
- ✅ can_use_bulk_marketplace: true
- ✅ can_use_bid_marketplace: true
- ✅ can_view_basic_analytics: true
- ✅ can_view_advanced_analytics: true

### Institutions
- ✅ can_view_basic_analytics: true
- ✅ can_use_bulk_marketplace: premium+
- ✅ can_use_bid_marketplace: premium+
- ✅ can_view_advanced_analytics: premium+

### Admin
- Global visibility (read)
- Moderation tools
- Does NOT bypass premium gates through UI logic alone

---

## 3. Non-Negotiable Rules

- Regular users NEVER see bidding or procurement UI.
- Kids Mode NEVER shows:
  - Pricing
  - Booking
  - Fundraising
  - Donations
  - RFQs
  - Bids
  - Subscriptions
- Landmarks are NEVER monetized.
- Holidays require:
  - Date match
  - User opt-in
  - Business opt-in
  - Kids-safe approval if in Kids Mode
- Seasonal theming is ALWAYS active (baseline).

---

## 4. Kids Mode (STRICT)

- Activated only through explicit parent flow
- PIN protected
- Timed session
- Age tiers: 3–6, 7–9, 10–13, 13+
- Food rules apply ONLY to food
- Animal/farm education is NOT blocked
- No fundraising, no sales language, no pricing

---

## 5. Seasonal & Holiday Intelligence

### Seasons
- Always on
- Drives palette
- Drives animations
- Drives icon density
- Drives background tone

### Holidays
- OFF by default
- Opt-in based
- Dual consent required
- Kids requires extra safety flag
- Turning OFF removes all visuals

---

## 6. Maps & Landmarks

- Community Map: vendors, markets, landmarks
- Kids Map: only kids-safe entries
- Municipalities are NOT visible to public users
- Landmarks:
  - Educational
  - Non-commercial
  - Never monetized
  - Optional experience links only

---

## 7. Events & Experiences

### Vendors
- Can create experiences
- Can host events

### Institutions
- Can host community events

### Public Users
- Can browse
- Can attend

### Kids
- View only
- Education-only
- No pricing

---

## 8. Contact & Support

- Single support contact form
- Routes to founder email
- Must be mobile-accessible
- No phone number required at launch

---

## 9. Social Layer (LIMITED)

- Feed items allowed
- Likes allowed
- Comments:
  - Disabled by default for ethical control
  - Admin-only toggle if ever enabled

---

## 10. What Is ALREADY COMPLETE

✅ Backend RLS and policies  
✅ Roles & tiers  
✅ Feature flags  
✅ Bidding gates  
✅ Bulk gates  
✅ Kids restrictions  
✅ Media buckets  
✅ Protected uploads  
✅ Events schema  
✅ Feed schema  
✅ Analytics tables  
✅ Seasonal logic  
✅ Holiday gating  

---

## 11. What Is STILL ACTIVE WORK (FRONTEND ONLY)

- UI polish
- Mobile nav fixes
- Contact form visibility on mobile
- Kids Map transitions
- Dark mode consistency
- Founder preview toggles
- Role preview accuracy
- Visual seasonal transitions
- Holiday animation hooks

---

## 12. Absolute Law

❌ No schema rewrites  
❌ No RLS removal  
❌ No marketplace exposure to regular users  
❌ No Kids Mode monetization  
❌ No holiday auto-activation  

✅ Only UI, wiring, styling, QA allowed

---

**ROOTED Community is the emotional, cultural, and public face of the platform.  
It ships clean. It ships safe. It ships grounded.**
