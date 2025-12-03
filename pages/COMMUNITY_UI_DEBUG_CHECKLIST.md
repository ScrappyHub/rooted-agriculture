# ROOTED Community – UI Debug & QA Checklist

Backend checks must reference:
`rooted-core/docs/ROOTED_DEBUG_TOOLKIT_CORE.md`

---

## 1. Directory & Profiles

### 1.1 Search & Filters
- [ ] Name search works
- [ ] Category filters work
- [ ] Distance filters work
- [ ] Inactive providers hidden

### 1.2 Vendor Profiles
- [ ] Media loads correctly
- [ ] Text wraps on mobile
- [ ] No admin data leaks
- [ ] No market UI for regular users

---

## 2. Map & GEO
- [ ] Centers correctly
- [ ] Pins update on filters
- [ ] No municipal leakage
- [ ] Kids Mode map hides vendors

---

## 3. Feed
- [ ] Loads without infinite spinner
- [ ] Shows author clearly
- [ ] No posting in Kids Mode
- [ ] Comments minimal, not emphasized

---

## 4. Events
- [ ] Create event with title/date/location
- [ ] Volunteer supported
- [ ] Discovery order correct
- [ ] Kids-safe label required

---

## 5. Kids Mode
- [ ] Entry requires intent
- [ ] No commerce views
- [ ] No messaging
- [ ] Only kids-safe discovery

---

## 6. Seasonal & Holidays
- [ ] Seasonal always on
- [ ] Holidays only appear with opt-in
- [ ] Kids visuals remain safe

---

## 7. Contact / Support
- [ ] Visible on mobile
- [ ] Form submits
- [ ] Confirmation shows
- [ ] Email arrives

---

## 8. UX & State
- [ ] Logout clears state
- [ ] Account switching updates UI
- [ ] Fallback images work
- [ ] Errors show messages

---

## 9. Bug Reporting

Use:

`docs/BUG_REPORT_TEMPLATE.md`

Include:

- Role & tier
- Mode (kids/normal)
- Area
- Expected vs actual
