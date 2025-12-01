🌱 ROOTED Community — Master Handoff (UI + Backend)

Status: Only live vertical (backend hardened, UI stabilizing)  
Scope: ROOTED Community only  
Excludes: Construction, Healthcare, Emergency, Workforce, all future verticals  
Backend: Locked & governed via ROOTED Core + Admin Governance Layer  
Remaining Work: UI / UX polish, wiring, and visual QA only

This document is the single source of truth for ROOTED Community behavior.  
If the app and this document disagree, **this document wins**.

---

## 1. What ROOTED Community Is

ROOTED Community is the public-facing cultural + food + community layer of the ROOTED platform.

It includes:

- Farms, orchards, markets
- Food vendors & community staples
- Experiences & events
- Landmarks & educational locations
- **Kids Education Mode (design-complete; pilot OFF at Community launch)**
- Seasonal & holiday intelligence
- Community discovery & maps

It is:

- ✅ Always public
- ✅ Non-political
- ✅ Non-religious by default
- ✅ Safety-first
- ✅ Kids-safe where flagged (for future Kids Mode surfaces)
- ✅ Not paywalled for basic discovery

It is NOT:

- ❌ A job board
- ❌ A construction or healthcare system
- ❌ A general gig marketplace
- ❌ A bidding marketplace for regular users
- ❌ An open social network (likes only; comments off by default)

Only ROOTED Community is in active development and production.  
All other vertical repos exist as **quiet future options**, not promises.

---

## 2. Roles & Access (Backend-Enforced)

All access is controlled by `public.user_tiers` + `feature_flags` and the Admin Governance Layer defined in ROOTED Core.

### 2.1 Public / Guest

Can:

- Browse vendors, maps, events, landmarks
- View seasonal & holiday overlays (if enabled)

Cannot:

- ❌ Access any marketplace (RFQs, bids, bulk offers)
- ❌ View analytics
- ❌ Message vendors/institutions

### 2.2 Individual / Community Member

Same as Public, with login identity.

Can:

- Save favorites and perform basic engagement actions (if wired)

Cannot:

- ❌ Access procurement tools
- ❌ Use vendor/institution dashboards
- ❌ Act as a provider or institution

Kids Mode:

- Kids Mode behavior is defined at the platform level.
- At Community launch, **Kids Mode UI surfaces are OFF**.
- When enabled in Education/Kids verticals, this document’s Kids rules apply.

Community profiles are private to the user.  
They may have a public display name/avatar in likes or lightweight social proof, but they are not discoverable like providers.

### 2.3 Vendors (Businesses)

Vendors are “businesses” on the map legend.

Shared powers (all vendor tiers):

- Create & manage provider profile (after approval + moderation)
- Post public media (photos, videos) within rules
- Create experiences & events
- Appear in directory, map, and seasonal discovery (if tagged & approved)

Tier-specific via `feature_flags`:

**Vendor — FREE**

- `can_use_bulk_marketplace`: optional (false at Community launch unless explicitly enabled)
- `can_use_bid_marketplace`: false
- `can_view_basic_analytics`: optional
- `can_view_advanced_analytics`: false

**Vendor — PREMIUM**

- `can_use_bulk_marketplace`: true (when market is opened)
- `can_use_bid_marketplace`: false
- `can_view_basic_analytics`: true
- `can_view_advanced_analytics`: false

**Vendor — PREMIUM PLUS**

- `can_use_bulk_marketplace`: true
- `can_use_bid_marketplace`: true
- `can_view_basic_analytics`: true
- `can_view_advanced_analytics`: true

Founding vendor rule (Community only):

- The first 3 non-seeded vendors to sign up and be approved receive:
  - Lifetime **Premium** (not Premium Plus)
  - Ability to upgrade to Premium Plus at 50% of whatever the price is at the time
- This is implemented via feature flags (e.g. `is_founding_vendor`, `has_discounted_upgrade`), never by bypassing tiers.

### 2.4 Institutions

Community vertical institutions (schools, nonprofits, municipalities, etc.) are represented as providers too, with separate tagging.

In ROOTED Community:

- Discoverable via map & directory
- Hosts of events, volunteer opportunities, and experiences
- Anchors for school/education relationships

Tier behavior (controlled in Core):

- Basic analytics: ✅ allowed
- Bulk marketplace: ✅ for Premium+ institutional tiers (when opened)
- Bid marketplace: ✅ for Premium+ where vertical allows
- Advanced analytics: ✅ for Premium+ only

### 2.5 Sanctuaries & Rescues (Nonprofit Provider Type)

Sanctuary / rescue entity types are allowed on ROOTED but restricted to community + volunteer only.

Canonical behavior:

- ✅ May apply to ROOTED
- ✅ May post volunteer & education events
- ✅ May appear in community discovery & map
- ❌ May **not** use Provider Premium / Premium Plus tools
- ❌ May **not** access bid markets, bulk procurement, or commercial ads
- ❌ May **not** participate as contractors or institutional vendors

Access tier:

- `provider_type = 'nonprofit_sanctuary_rescue'` (or equivalent)
- Commercial access disabled via `feature_flags`

### 2.6 Admin

Admin is defined strictly by:

- `user_tiers.role = 'admin'`
- `account_status = 'active'`

Admins:

- See everything that any role can see
- Use admin dashboards for:
  - Account governance (roles, tiers, status, flags)
  - Moderation queue (events, landmarks, applications)
  - Seasonal/holiday debug and featured checks

Admins do **not** bypass Premium/Plus gates through UI; gates are enforced in the DB.

---

## 4. Kids Mode (Design-Complete, Pilot OFF)

Kids Mode is **design-complete** at the platform level but:

- ❌ Kids Mode UI is OFF for ROOTED Community launch
- ✅ All “no kids monetization / no kids marketplaces” rules are still enforced now

This section defines future behavior once Kids Mode is enabled in Education / Kids verticals.

When Kids Mode is ON:

- Only content with `is_kids_safe = true` appears
- No pricing, subscriptions, fundraising, or donation CTAs
- No RFQs, bids, bulk offers, or institutional dashboards
- Kids Mode cannot upload anything (no spots, no events, no experiences)
- Kids Mode is **view-only** on community content

Until that day:

- Community behaves like an adult-safe directory with family-aware content
- Kids Mode config flags stay false in `app_settings` / feature flags

---

(You can keep the rest of your existing sections: seasonal logic, maps, moderation, analytics, debug hooks, non-negotiable laws. They are already aligned with your canonical docs.)
