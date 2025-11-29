✅ ROOTED – COMMUNITY VERTICAL
UI FRONT-END FIXES & QA MASTER REPORT

Scope: Community Layer Only
Applies To: Web + Mobile
Excludes: Construction, Healthcare, Emergency, Disaster, Workforce

1. GLOBAL UI STABILITY ISSUES (PLATFORM-WIDE)
1.1 Navigation & Routing

✅ All bottom nav icons must:

Respect role (guest / individual / vendor / institution)

Hide locked features instead of showing broken links

⛔ No dead routes allowed

✅ Back button behavior must:

Never break session

Never reset Kids Mode

Never bypass paywalls

1.2 Role-Based UI Gating (CRITICAL)

Verify UI responds correctly to:

Role	Must See	Must NOT See
Guest	Directory, Landmarks, Events (view)	Messaging, Posting, Analytics
Individual	Feeds, Events, Landmarks	Vendor dashboards, RFQs
Vendor	Vendor profile, media, events	Institutional bid screens (unless Premium+)
Institution	Discovery, RFQs	Vendor analytics
Kids Mode	Landmarks, Learning, Events	Messaging, Commerce, Fundraising

⚠️ No UI feature may rely only on backend gating.
UI must hide or gray out locked features.

2. KIDS MODE – UI FIXES (HIGH PRIORITY)
2.1 Entry & Exit

✅ Clear toggle flow

✅ Parental PIN screen visible

✅ Session timeout indicator visible

❌ No silent exit allowed

2.2 UI Restrictions

Kids Mode must HIDE COMPLETELY:

Fundraisers

Donations

Vendor pricing

RFQs, Bids, Marketplaces

Open messaging

Public comments

Likes on adult feeds

2.3 Kids Visual Design

Softer color palette

No alert-style reds

Simplified icons

No numeric financial values shown anywhere

3. FEED UI (CURRENTLY LIVE – NEEDS HARDENING)
3.1 Feed Item Display

✅ Proper author display (community / vendor / institution)

✅ Feed category icon shown

✅ Feed image cropping not distorted

✅ Text overflow gracefully handled

3.2 Comments & Likes

User has stated:

“I barely wanted likes and don’t really want comments.”

✅ UI must now:

Disable comments by default

Likes allowed but not incentivized

No engagement leaderboard

No dopamine-loop animations

4. MAP + GEO UI PROBLEMS
4.1 Municipal Layer Leakage (BUG)

Municipal data must:

Be ADMIN only

Never visible to public map legend

Never auto-loaded

✅ Verify:

Map layers respect discovery rules

No ghost categories

4.2 Kids Mode Map

Kids Mode map must:

Hide vendors

Hide institutions

Show only:

Landmarks

Educational events

Nature zones

5. EVENT UI FIXES
5.1 Event Creation

✅ Clean distinction:

Public events

Volunteer events

Kids-safe events

⛔ No pricing allowed in Kids events

✅ Date picker must:

Handle time zones correctly

Prevent invalid past submissions

5.2 Event Discovery

Event filters must not reset on route change

Kids Mode auto-filters to kids-safe events

Location radius slider must persist state

6. PROFILE UI ISSUES
6.1 Community Profiles

Must display:

Name

Bio

Interests

Public activity

Must NOT show:

Exact location

Analytics

Vendor tools

6.2 Vendor Profiles (Community-Facing)

✅ Clean public storefront view

✅ Media gallery sorting

✅ No backend admin data leaks

✅ No analytics graphs on public view

7. MEDIA + UPLOAD UI
7.1 Upload Flow

Must confirm:

File type

Size limits

Content type (photo/video/document)

✅ Upload progress bar required

⛔ No silent failures allowed

7.2 Media Display

Correct aspect ratios

No layout jumps

No autoplay video in Kids Mode

8. SUPPORT + CONTACT UI
8.1 Contact Form (CONFIRMED LIVE)

✅ Must be visible on:

Desktop

Tablet

Mobile

⚠️ Currently suspected hidden on mobile

✅ Required fields:

Name

Email

Message

✅ Confirmation toast required after submit

9. PAYWALL & FEATURE GATES

✅ Premium buttons allowed

❌ Premium function execution blocked without subscription

✅ Locked feature click should:

Explain restriction

Never hard crash

Never redirect to error page

10. DISCOVERY FILTERS (COMMUNITY)

Category filters must persist on refresh

Distance filters must persist through navigation

Seasonal filters must:

Auto apply based on date

Respect holiday opt-in only

11. ACCESSIBILITY (REQUIRED FOR CIVIC PLATFORMS)

✅ Minimum contrast for text

✅ Tap targets large enough for mobile

✅ No critical functionality on hover only

✅ Font scaling must not break layout

12. PERFORMANCE UI ISSUES

✅ No feed infinite loader lockups

✅ No skeleton loaders stuck

✅ Map tiles must not delay entire screen interaction

13. COMMUNITY UI FINAL LAUNCH BLOCKERS

These must be ✅ before public launch:

☐ Kids Mode fully locked
☐ Map municipal leak fixed
☐ Support form mobile visible
☐ Feed comments disabled
☐ Event UI cleaned
☐ Vendor profiles safe
☐ Paywalls safe
☐ Discovery filters stable

✅ STATUS SUMMARY
Area	Status
Core Feed UI	⚠ Needs polish
Kids Mode UI	⚠ Active fixes required
Map & GEO	❌ Critical fixes required
Events UI	⚠ Cleanup required
Profiles	✅ Mostly stable
Media	✅ Stable
Support	⚠ Mobile visibility fix
Paywalls	✅ Present but needs UX polish
