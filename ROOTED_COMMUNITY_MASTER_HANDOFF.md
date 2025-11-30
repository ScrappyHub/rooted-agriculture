🌱 ROOTED Community — Master Handoff (UI + Backend)

Status: Live vertical (backend hardened)
Scope: ROOTED Community only
Excludes: Construction, Healthcare, Emergency, Workforce, future verticals
Backend: Locked & governed via ROOTED Core + Admin Governance Layer
Remaining Work: UI / UX polish, wiring, and visual QA only

This document is the single source of truth for ROOTED Community behavior.
If the app and this document disagree, this document wins.

1. What ROOTED Community Is

ROOTED Community is the public-facing cultural + food + community layer of the ROOTED platform.

It includes:

Farms, orchards, markets

Food vendors & community staples

Experiences & events

Landmarks & educational locations

Kids Education Mode

Seasonal & holiday intelligence

Community discovery & maps

It is:

✅ Always public

✅ Non-political

✅ Non-religious by default

✅ Safety-first

✅ Kids-safe where flagged

✅ Not paywalled for discovery

It is NOT:

❌ A job board

❌ A construction or healthcare system

❌ A general gig marketplace

❌ A bidding marketplace for regular users

❌ An open social network (likes only; comments off by default)

2. Roles & Access (Backend-Enforced)

All access is controlled by public.user_tiers + feature_flags and the Admin Governance Layer defined in ROOTED Core.

2.1 Public / Guest

Can:

Browse vendors, maps, events, landmarks

View seasonal & holiday overlays (if enabled)

Cannot:

❌ Access any marketplace (RFQs, bids, bulk offers)

❌ View analytics

❌ Message vendors/institutions

2.2 Individual / Community Member

Same as Public, with login identity.

Can:

Use Kids Mode (via parent/guardian flow)

Save favorites, basic engagement actions (if wired)

Cannot:

❌ Access procurement tools

❌ Use vendor/institution dashboards

❌ Act as a provider or institution

Community profiles are private to the user.
They may have a “public name/avatar” in likes or lightweight social proof, but they are not discoverable like providers.

2.3 Vendors (Businesses)

Vendors are “businesses” on the map legend.

Shared powers (all vendor tiers):

Create & manage provider profile (if approved)

Post public media (photos, videos) within rules

Create experiences & events

Appear in directory, map, and seasonal discovery (if tagged & approved)

Tier-specific via feature_flags:

Vendor — FREE

can_use_bulk_marketplace: optional (false or true depending on launch config)

can_use_bid_marketplace: false

can_view_basic_analytics: optional

can_view_advanced_analytics: false

Vendor — PREMIUM

can_use_bulk_marketplace: true

can_use_bid_marketplace: false

can_view_basic_analytics: true

can_view_advanced_analytics: false

Vendor — PREMIUM PLUS

can_use_bulk_marketplace: true

can_use_bid_marketplace: true

can_view_basic_analytics: true

can_view_advanced_analytics: true

The first 3 non-seeded vendors to sign up and be approved in ROOTED Community receive:

Lifetime Premium (not Premium Plus)

Ability to upgrade to Premium Plus at 50% off whatever the price is at the time.
This is handled in feature_flags (e.g. is_founding_vendor + discounted upgrade logic), not by bypassing tiers.

2.4 Institutions

Community vertical institutions (schools, nonprofits, municipalities, etc.) are represented as providers too, with separate tagging, but they do not get the same discovery specialty badges as vendors.

Tier behavior (controlled in Core):

Basic analytics: ✅ allowed

Bulk marketplace: ✅ for premium+ institutional tiers

Bid marketplace: ✅ for premium+ where vertical allows

Advanced analytics: ✅ for premium+ only

In Community launch, institutions are mostly:

Discoverable via map & directory

Hosts of events, volunteer opportunities, experiences

Anchors for school/education relationships

2.5 Sanctuaries & Rescues (Nonprofit Provider Type)

Sanctuary / rescue entity types are allowed on ROOTED but restricted to community + volunteer only.

Canonical types (9):

Farm Animal Sanctuaries

Wildlife Rehabilitation Centers

Domestic Animal Rescue Shelters

Equine Sanctuaries & Horse Rescues

Exotic Animal Rescues (non-commercial, compliant, non-breeding)

Marine Wildlife Rescue Organizations

Insect & Pollinator Preservation Sanctuaries

Educational Animal Sanctuaries (non-zoo)

Conservation Land Trusts with Animal Protection

They can:

✅ Apply to ROOTED

✅ Post volunteer events & education events

✅ Appear in community discovery & map

✅ (Future) Accept donations, if a safe flow is built

They cannot:

❌ Use Provider Premium / Premium Plus tools

❌ Access bid markets, bulk procurement, or commercial advertising

❌ Participate as contractors or institutional vendors

Canonical label:

provider_type = 'nonprofit_sanctuary_rescue' (or equivalent)

Access tier: Community + Volunteer Only

Commercial access: Disabled by feature_flags

2.6 Admin

Admin is defined strictly by:

user_tiers.role = 'admin'

account_status = 'active'

Admins:

See everything that any role can see

Use admin dashboards for:

Account governance (roles, tiers, status, flags)

Moderation queue (events, landmarks, applications)

Seasonal/holiday debug and featured checks

Do not bypass Premium/Plus gates through UI; gates are enforced in the DB.

3. Discovery, Badges & Categories

Discovery in ROOTED Community is grounded in:

Provider category (map legend)

Specialty discovery badges (for vendors)

Seasonal & cultural intelligence

Moderation status (only approved items surface)

3.1 Vendor Specialty Badges (Map Legend)

These map directly to vendor specialties and discovery badges:

Businesses (Vendors):

Bakeries

Baristas

Butchers

Community Staples

Dairies

Farms

Fish Markets

Food Trucks

Honey Farms & Apiaries

Markets

Orchards

Restaurants

Additional vendor badge (not in the legend but allowed):

Farm Stand

These are specialty / discovery badges and drive:

Icons and colors on the map

Filters in the directory

Seasonal & featured vendor views

3.2 Institution Tags (Non-Discovery)

Institutions have their own tags, but they are not treated as discovery specialty badges. They are used for:

Compliance

Filtering in institutional views

Context in RFQ / procurement flows later

They appear on the map, but do not receive the same “featured vendor” treatment.

3.3 Community Spots (Uploads Locked)

Community Spots (map legend):

Birdwatching

Butterfly Garden

Camping Spot

Community Garden

Fishing Spot

Foraging Area

Hunting Spot

Stargazing Site

Trail

Canonical decision:

Community Spot uploads from general users are disabled for now.

These spots are curated/seeded only (by you/admin) until:

The Culture Loop + Experiences system is fully mature, and

There is a better governance layer for citizen uploads.

Rules:

Kids Mode never has upload rights for Community Spots.

Community Spots must not be embedded or governed solely by the “Community” vertical in a way that risks safety.

When citizen uploads eventually open:

They go through Moderation System (MODERATION_SYSTEM.md)

They are flagged with kids-safe and access scopes

Upload permissions are controlled via feature_flags

3.4 Community Member Social Proof

Community members can earn non-commercial social proof badges related to:

Volunteering impact

Event participation

Community service

Constraints:

User profiles remain private to themselves.

Only minimal, anonymized, or opt-in public signals appear (e.g. “This farm has 37 community volunteer check-ins this year.”)

These stats are surfaced on provider profiles, not as detailed public user profiles.

4. Kids Mode (Strict Canon)

Kids Mode for Community follows the ROOTED Core kids rules:

Activated via explicit parent flow

Parental PIN required

Session timer

Age tiers: 3–6, 7–9, 10–13, 13+

Rules in Community:

Only content with is_kids_safe = true appears.

No pricing, subscriptions, fundraising, or donation CTAs.

No RFQs, bids, bulk offers, or institutional dashboards.

Food rules (e.g. dietary content) apply only to food/recipes.

Animal and farm education is never blocked for being “agricultural”; it is filtered purely on safety and content.

Kids Mode cannot upload:

Community Spots

Landmarks

Events

Experiences

Kids Mode is view-only for community-facing content.

5. Seasonal & Holiday Intelligence (Community Layer)

Seasonal & holiday logic reuses the ROOTED Core system.

5.1 Seasons (Always On)

Season is a baseline:

Always active (Spring, Summer, Fall, Winter)

Drives color palette, card accents, subtle animations

Influences which vendors are surfaced as “Seasonally Featured”

Backend:

A read-only view (e.g. seasonal_featured_providers) selects vendors to highlight based on:

Today’s date

Seasonal tags on provider or badges

Engagement and discovery rules

Discovery queries (directory, map, home feed) read from this view instead of hard-coding logic in the app.

5.2 Holidays (Opt-In Overlays)

Holidays are:

OFF by default

Defined across ~11 cultural sets and ~30+ holidays

For a holiday overlay to appear:

Date matches holiday range

User has opted in to that holiday set

Business/provider has opted in

Kids Mode (if active) approves content as kid-safe

If any condition fails → fall back to seasonal baseline only.

5.3 Season Debug (Admin)

The Season Debug section (documented also in the Debug Toolkit) must be available to admins:

Questions it answers:

“Given today’s date, which seasonal tags are active?”

“Which vendors are currently considered ‘seasonally featured’?”

Implementation:

Via SQL view(s) + admin debug screen

Read-only; no direct writes from debug tools

6. Maps, Landmarks & Locations

ROOTED Community map shows:

Vendors (Businesses)

Institutions

Community Spots (curated)

Landmarks

User location (optional)

6.1 Landmarks

Landmarks are:

Educational, non-commercial

Often tied to:

History

Environment

Culture

Can optionally link to experiences (e.g. tours, field trips)

Rules:

Never monetized

Only shown when is_published = true

Kids views add is_kids_safe = true

Governed by Moderation System:

New landmarks start as moderation_status = 'pending'

Only approved appear in public queries

6.2 Municipalities

Municipal / government provider entries in Community:

Are not promoted or featured like vendors

Can appear for context (e.g. event hosts, school districts)

Must respect non-political, non-campaign, non-endorsement rules

7. Events, Experiences & Volunteering
7.1 Vendors

Can:

Host public events (markets, tastings, open farm days)

Host educational experiences (tours, demos)

Run seasonal programs (harvest events, etc.)

7.2 Institutions

Can:

Host community events

Host educational events (school trips, field days)

Partner with vendors for experiences

7.3 Public / Community Members

Can:

Browse events and experiences

Register / RSVP (if wired)

Participate in volunteering

Kids:

View education-only event surfaces

No pricing, booking, or fundraising UI in Kids Mode

7.4 Community Staples & Heritage

Community Staples (100+ year heritage businesses) are:

Tagged via badges (COMMUNITY_STAPLE, etc.)

Surface in Community vertical as “heritage anchors”

Often cross-linked with events, landmarks, and seasonal feature spots

8. Moderation & Safety (Canonical)

Community vertical uses ROOTED MODERATION_SYSTEM.md.

Moderated entities:

Events

Landmarks

Vendor & institution applications

(Future) Feed items and user submissions

Key rules:

All submissions create a row in public.moderation_queue

No entity is public until moderation_status = 'approved'

public.admin_moderate_submission() is the only public admin RPC:

Approve or reject

Writes audit logs

Sends notifications (submission_approved / submission_rejected)

Internal _admin_moderate_submission_internal is never exposed via RPC.

Kids Mode relies on moderation + is_kids_safe flags to gate content.

9. Analytics & Community Impact

Community vertical uses ROOTED Core analytics tables:

vendor_analytics_daily

vendor_analytics_basic_daily

vendor_analytics_advanced_daily

bulk_offer_analytics (for vendors using bulk later)

Community-facing surface:

Providers see:

Profile views

Directory clicks

Experience views

Favorites added

Some metrics may be rephrased as “Community Impact”:

Volunteer shifts filled

Events attended

School visits

Seasonal campaign performance

Community member individual stats are not public profiles; they roll up into provider/community impact views.

10. Account Governance & Lifecycle (Applies Here Too)

Community vertical obeys the ROOTED Account Governance Layer:

user_tiers is the single source of truth for:

role, tier, account_status, feature_flags

Admin actions (role/tier/status/flags) are always logged in user_admin_actions.

Admin account list and controls come from:

admin_user_accounts view

admin_get_user_accounts() RPC (security definer, checks is_admin())

Account deletion:

Users initiate via official deletion flow:

Adds a row to account_deletion_requests with status = 'pending'

Immediately restricts account behavior (no new content)

Admins/processes move deletion through in_progress → completed

PII is anonymized; civic + analytic audit rows remain.

No vertical, including Community, can bypass:

account_status

role

tier

feature_flags

11. Debug & QA Hooks (Community)

Community vertical uses the ROOTED_DEBUG_TOOLKIT_CORE.md plus this vertical-specific layer.

Key tools:

/founder/preview:

Toggle seasons, holiday sets, dark mode, and Kids Mode locally (UI-only).

Backend health query (#365 from Debug Toolkit):

Confirms RLS, policies, functions, feature matrix.

Community UI Debug Checklist:

Map, legends, badges, seasonal featured views

Kids Mode map vs adult map

Contact/support visibility

Mobile navigation and discoverability

All debug tools are read-only and must not change production data directly.

12. Non-Negotiable Laws (Community)

❌ No schema rewrites from this vertical.

❌ No RLS removal or “temporary” bypasses.

❌ No exposure of RFQs, bids, or bulk analytics to regular users or Kids Mode.

❌ No monetization of landmarks or children’s attention.

❌ No automatic holiday activation without consent.

❌ No community spot uploads from Kids Mode or public users until culture loop & governance are complete.

✅ Only UI, wiring, styling, and QA work is allowed here, on top of the locked backend.

ROOTED Community is the emotional, cultural, and public face of your platform.
It must ship:

Clean

Safe

Grounded in governance

Deeply respectful of families, culture, and community

This document is now the canonical reference for anything Community-related in ROOTED.
