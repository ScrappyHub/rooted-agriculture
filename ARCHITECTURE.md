# ROOTED Agriculture — Application Architecture

This repository powers the **ROOTED Agriculture & Local Food vertical**.

It is **not** a standalone app.  
It is a governed surface layer built on top of:

- `rooted-platform` (governance & law)
- `rooted-core` (database, RLS, engines)

If this document and the UI disagree → this document wins.  
If this document and ROOTED governance disagree → governance wins.

---

## 🧠 Inherited Architecture Layers

ROOTED Agriculture inherits **all** platform enforcement from ROOTED Core:

### Identity & Governance Layer

- Auth (Supabase)
- Roles (`community_member`, `vendor`, `institution`, `admin`)
- Tiers (`free`, `premium`, `premium_plus`)
- `feature_flags` based access

### Core Commerce Layer

- `providers`
- `rfqs`
- `bids`
- `bulk_offers`

### Community & Intelligence Layer

- `events` (with `event_vertical = 'AGRICULTURE_FOOD'`)
- `experiences`
- `feed_items`, `feed_comments`, `feed_likes`
- `landmarks`
- Map & geo intelligence (50-mile / 25-marker rules)
- Seasonal & cultural intelligence engine

### Safety & Consent Layer

- Kids Mode & Teen Mode (backend law)
- Holiday & cultural opt-ins
- Nonprofit & sanctuary protections
- RLS-enforced content filtering

### Analytics Layer

- Vendor analytics
- Bulk marketplace analytics
- Engagement analytics (read-only in this repo)

---

## 🧬 Vertical Plug-in Doctrine

ROOTED Agriculture:

- Reuses the **same core** as every other vertical
- Only adds Agriculture-specific:

  - Categories & specialty groupings  
  - Discovery filters  
  - Seasonal overlays (harvest, planting, CSA, markets)  
  - Educational panels & storytelling  
  - UI maps and cards for farms, markets, sanctuaries

This repo **does not** create new engines.  
It only consumes what `rooted-core` has already defined.

---

## 🛑 Architectural Non-Negotiables

- Core governance overrides **all** UI behavior
- No UI route may bypass `feature_flags`
- No UI route may bypass RLS
- No discovery surface may bypass backend limits
- No Kids/Teen surface may expose adult tools
- No UI may expose analytics or markets that the backend has not granted

ROOTED behaves as:

- Civic OS  
- Discovery & procurement engine  
- Safety platform  

It is **not**:

- A social network  
- An ad company  
- A growth machine  

---
