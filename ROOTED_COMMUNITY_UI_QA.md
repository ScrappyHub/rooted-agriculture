# ROOTED – COMMUNITY VERTICAL  
UI FRONT-END FIXES & QA MASTER REPORT (CANONICAL)

Scope: Community UI Layer Only  
Applies To: Web + Mobile  
Excludes: Construction, Healthcare, Emergency, Disaster, Workforce  

This document governs **UI correctness only**.  
Backend authority is defined in:

- rooted-core  
- rooted-platform/governance  

If UI and governance conflict → governance wins.

---

## 1. GLOBAL UI STABILITY ISSUES (PLATFORM-WIDE)

### 1.1 Navigation & Routing

✅ Bottom navigation MUST:

- Respect role (guest / individual / vendor / institution)
- Hide locked features (not broken links)
- Never expose disabled routes

⛔ No dead routes allowed

✅ Back button behavior MUST:

- Never break session
- Never reset Kids Mode
- Never bypass paywalls

---

### 1.2 Role-Based UI Gating (CRITICAL)

| Role | MUST SEE | MUST NOT SEE |
|------|----------|--------------|
| Guest | Directory, Landmarks, Events (view) | Messaging, Posting, Analytics |
| Individual | Feeds, Events, Landmarks | Vendor dashboards, RFQs |
| Vendor | Vendor profile, media, events | Institutional bid screens (unless Premium+) |
| Institution | Discovery, RFQs | Vendor analytics |
| Kids Mode | Landmarks, Learning, Events | Messaging, Commerce, Fundraising |

⚠️ No UI feature may rely ONLY on backend gating.  
UI must hide or gray out locked features.

---

## 2. KIDS MODE – UI FIXES (HIGH PRIORITY)

### 2.1 Entry & Exit

✅ Clear toggle flow  
✅ Parental PIN screen visible  
✅ Session timeout visible  
❌ No silent exit allowed  

### 2.2 UI Restrictions (HARD HIDE)

Kids Mode must completely hide:

- Fundraisers
- Donations
- Vendor pricing
- RFQs, Bids, Marketplaces
- Open messaging
- Public comments
- Likes on adult feeds

### 2.3 Kids Visual Design

- Softer color palette
- No alert reds
- Simplified icons
- No numeric financial values anywhere

---

## 3. FEED UI (LIVE – REQUIRES HARDENING)

### 3.1 Feed Display

✅ Correct author identity  
✅ Feed category icon  
✅ Image cropping correct  
✅ Safe text overflow  

### 3.2 Comments & Likes

User directive:

“I barely wanted likes and don’t really want comments.”

✅ Comments disabled by default  
✅ Likes allowed but NOT incentivized  
✅ No engagement leaderboards  
✅ No dopamine-loop animations  

---

## 4. MAP + GEO UI PROBLEMS

### 4.1 Municipal Layer Leakage (CRITICAL BUG)

Municipal data MUST:

- Be ADMIN only
- Never appear in public legend
- Never auto-load

✅ Verify rules enforced

### 4.2 Kids Mode Map

Kids Mode map MUST:

- Hide vendors
- Hide institutions
- Show ONLY:
  - Landmarks
  - Educational events
  - Nature zones

---

## 5. EVENT UI FIXES

### 5.1 Event Creation

✅ Clear distinction:

- Public events  
- Volunteer events  
- Kids-safe events  

⛔ No pricing in Kids events  

✅ Date picker:

- Correct timezone handling  
- Prevents past submissions  

### 5.2 Event Discovery

- Filters persist on navigation
- Kids auto-filters to kids-safe
- Radius slider retains state

---

## 6. PROFILE UI ISSUES

### 6.1 Community Profiles

Must show:

- Name
- Bio
- Interests
- Public activity

Must NOT show:

- Exact location
- Analytics
- Vendor tools

### 6.2 Vendor Profiles (Public)

✅ Clean storefront  
✅ Media gallery sorted  
✅ No admin data leakage  
✅ No analytics on public view  

---

## 7. MEDIA + UPLOAD UI

### 7.1 Upload Flow

✅ Confirm file type  
✅ Confirm file size  
✅ Confirm content type  
✅ Show progress bar  
⛔ No silent failures  

### 7.2 Media Display

- Correct aspect ratios
- No layout shifting
- No autoplay in Kids Mode

---

## 8. SUPPORT + CONTACT UI

✅ Must be visible on:

- Desktop
- Tablet
- Mobile

⚠️ Currently suspected hidden on mobile  

✅ Required fields:

- Name
- Email
- Message  

✅ Submit confirmation toast required

---

## 9. PAYWALL & FEATURE GATES

✅ Premium buttons allowed  
❌ Premium execution blocked without subscription  

✅ Locked clicks must:

- Explain restriction
- Never crash
- Never redirect to error

---

## 10. DISCOVERY FILTERS

✅ Category filters persist  
✅ Distance filters persist  
✅ Seasonal filters auto-apply  
✅ Holiday overlays respect opt-in  

---

## 11. ACCESSIBILITY (CIVIC REQUIREMENT)

✅ Text contrast  
✅ Tap target sizing  
✅ No hover-only gates  
✅ Font scaling safe  

---

## 12. PERFORMANCE UI

✅ No feed infinite loaders  
✅ No stuck skeletons  
✅ Map tiles never block interaction  

---

## 13. COMMUNITY UI FINAL LAUNCH BLOCKERS

☐ Kids Mode fully locked  
☐ Municipal map leak fixed  
☐ Support visible on mobile  
☐ Feed comments disabled  
☐ Event UI cleaned  
☐ Vendor profiles safe  
☐ Paywalls hardened  
☐ Discovery filters stable  

---

## ✅ STATUS SUMMARY

| Area | Status |
|------|--------|
| Core Feed UI | ⚠ Needs polish |
| Kids Mode UI | ⚠ Active fixes |
| Map & GEO | ❌ Critical |
| Events UI | ⚠ Cleanup |
| Profiles | ✅ Stable |
| Media | ✅ Stable |
| Support | ⚠ Mobile issue |
| Paywalls | ✅ Needs UX polish |
