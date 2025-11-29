# ROOTED Community – UI Debug & QA Checklist

This doc is for **front-end debugging** of the ROOTED Community vertical:

- Directory (vendors / institutions / community spots)
- Map & discovery
- Feed (lightweight)
- Events & volunteering
- Kids Mode
- Seasonal / holiday overlays
- Contact / support flows

Backend/core issues should also be checked against
`rooted-core/docs/ROOTED_DEBUG_TOOLKIT_CORE.md`.

---

## 1. Directory & Profiles

### 1.1 Search & Filters

- [ ] Search by name works (no crash, returns expected vendors).
- [ ] Category filter (farms, bakeries, butchers, etc.) narrows results correctly.
- [ ] Distance / radius sliders or options behave as expected.
- [ ] Closed or inactive providers do **not** appear in the main directory.

### 1.2 Vendor / Institution Profile

For multiple vendors (farm, market, bakery, etc.):

- [ ] Banner / profile media loads without layout breaking.
- [ ] Description text wraps nicely on mobile & desktop.
- [ ] Contact info shows correctly, no leaking of admin-only fields.
- [ ] Any “bulk / institution” features are hidden for regular users.

---

## 2. Map & GEO Behavior

- [ ] Map centers on the user or default region without errors.
- [ ] Changing category/radius updates pins.
- [ ] Tapping a pin opens the correct vendor detail.
- [ ] No municipal / backend-only layers appear for regular users.
- [ ] In Kids Mode, map only shows kid-safe vendors/spots.

If municipal entities appear → bug (should be hidden / admin-only).

---

## 3. Feed & Lightweight Social

- [ ] Community feed loads without infinite spinners.
- [ ] Posts clearly show who posted (vendor/institution/individual).
- [ ] Post composer exists only where allowed (no posting in Kids Mode).
- [ ] Comments are available but not overly emphasized (no “comment wars” feel).
- [ ] Like buttons work but do not dominate the UI.

If it feels like a heavy social app: consider hiding/de-emphasizing
extra social UI.

---

## 4. Events & Volunteering

### 4.1 Creation

As a vendor/institution:

- [ ] Can create an event with:
  - Title, description
  - Date/time
  - Location
  - Kid-safe flag (if applicable)
- [ ] Can create volunteer / service events where supported.

### 4.2 Display

As a community user:

- [ ] Event list shows upcoming events in correct order.
- [ ] Each card shows date, time, location, and type (event vs volunteer).
- [ ] Kid-safe events are clearly labeled.

### 4.3 Kids Mode

- [ ] Kids Mode shows only kid-safe events.
- [ ] No prices, payment CTAs, or fundraising prompts in Kids Mode.
- [ ] Registration buttons (if shown) are parent-facing and safe.

---

## 5. Kids Mode (Critical Safety Surface)

### 5.1 Entry

- [ ] Kids Mode requires an intentional action (parent toggle/flow).
- [ ] Visual difference is obvious (colors, icons, labels).

### 5.2 Allowed Content

Once inside Kids Mode:

- [ ] No RFQs, bids, or construction/commercial content.
- [ ] No messaging UI.
- [ ] No ability to publish posts to the main feed.
- [ ] No donation/payment screens.
- [ ] Directory shows only pre-curated, kid-friendly vendors/spots.
- [ ] Events view only shows kid-safe events.

Try to “break” it:

- Navigate everywhere from Kids Mode and confirm nothing adult/commercial
  leaks through.

---

## 6. Seasonal & Holiday UI

### 6.1 Seasonal Layer

- [ ] Seasonal visuals (winter, harvest, spring, etc.) show as baseline.
- [ ] Seasonal elements do not interfere with navigation or readability.

### 6.2 Holiday Overlays (Opt-In Only)

- [ ] Holiday-specific banners or themes appear **only** when both:
  - User / business opted in.
  - Holiday is active in settings.

- [ ] Kids Mode holiday visuals remain kid-safe and non-intrusive.
- [ ] No religious or political targeting, just neutral/consumer-safe
  overlays where configured.

If any holiday theme appears without opt-in → bug.

---

## 7. Contact / Support

- [ ] “Contact / Support” is visible in nav on desktop.
- [ ] “Contact / Support” is visible and reachable on mobile (no buried menu).
- [ ] Contact form submits without errors.
- [ ] User sees clear success/failure messages.
- [ ] Emails actually arrive at the configured support email (manual check).

If mobile users can’t easily find support → UX bug.

---

## 8. General UX & State Bugs

Quick checks:

- [ ] Logging out clears user-specific data (no stale name/avatar).
- [ ] Switching accounts updates role-based UI (no stuck vendor/institution views).
- [ ] Broken images show fallback instead of blowing up layout.
- [ ] Error states show helpful messages, not blank screens.

---

## 9. When You Find a Bug

Use the shared bug template in the ROOTED platform repo
(`docs/BUG_REPORT_TEMPLATE.md`) and log an issue with:

- Vertical: `community`
- Area: directory / map / events / kids-mode / seasonal / support
- Role & tier used during test
- Exact steps to reproduce
