# ROOTED Community — Application Architecture

ROOTED Community is the live public-facing vertical of the ROOTED platform.

It is NOT a standalone app.
It is a governed surface layer built on top of ROOTED Core and ROOTED Platform.

---

## 🧠 Inherited Architecture Layers

This application inherits ALL enforcement from:

1. Identity & Governance Layer
   - Auth
   - Roles
   - Tiers
   - Feature Flags

2. Core Commerce Layer
   - Providers
   - RFQs
   - Bids
   - Bulk Offers

3. Community & Intelligence Layer
   - Events
   - Experiences
   - Feeds
   - Landmarks
   - Maps
   - Seasonal Engine

4. Safety & Consent Layer
   - Kids Mode
   - Cultural Controls
   - Holiday Opt-ins
   - Content Filtering

5. Analytics Layer
   - Vendor analytics
   - Bulk analytics
   - Engagement analytics

---

## 🧬 Vertical Plug-in Doctrine

ROOTED Community:

- Reuses the SAME core as every vertical
- Adds only:
  - Category sets
  - Community-specific experiences
  - Educational overlays
  - Seasonal layers
  - Discovery UI surfaces

---

## 🛑 Architectural Non-Negotiables

- Core governance overrides all UI behavior
- No UI route may bypass feature flags
- No UI route may bypass RLS
- No discovery surface may bypass backend limits
- No Kids surface may expose adult tools

---

ROOTED behaves as:

Civic OS + Discovery Engine + Safety Platform

Not a social network.
Not an ad company.
Not a growth machine.
