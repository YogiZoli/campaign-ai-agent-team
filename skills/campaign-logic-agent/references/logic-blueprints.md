# Campaign Logic Agent — Full Blueprints

Complete sequence blueprints for all 7 campaigns. Platform-independent. Ready to implement in any CRM/email platform.

---

## 01 — Onboarding Flow

**Goal:** Welcome new subscribers, establish trust, deliver first value, bridge to active campaigns.

```
Entry: New opt-in → email confirmed → lead magnet delivered
Tags: zg.onboard.entered / active / completed

Day 0  → Email 1: Welcome + lead magnet link [IMMEDIATE]
         Apply tag: zg.onboard.entered
         Wait: 24 hours

Day 1  → Email 2: Hero Story
         Wait: 48 hours

Day 3  → Email 3: Content roadmap / what to expect
         Wait: 48 hours

Day 5  → Email 4: Social proof / transformation story
         Wait: 48 hours

Day 7  → Email 5: Survey invite OR soft offer
         Wait: 72 hours

Day 10 → Email 6: Nurture / value
         Wait: 96 hours

Day 14 → Email 7: Bridge email → enter Click Sequence (02)
         Apply tag: zg.onboard.completed
         Remove tag: zg.onboard.active
         Enter: 02_Click_Sequence

Exit on purchase: apply zg.onboard.converted → enter buyer onboarding
Exit on unsub: apply zg.onboard.unsub → remove from all sequences
```

---

## 02 — Click Sequence

**Goal:** Identify engaged subscribers vs. cold subscribers. Universal engagement filter.

```
Entry: Tag zg.click-seq.entered applied (from Onboarding Day 14 OR manual trigger)
Tags: zg.click-seq.entered / clicked / cold / completed

Day 0 → Email 1: "Still there?" re-engagement hook
         Apply tag: zg.click-seq.entered
         Wait: 24 hours

Day 1 → Email 2: Value bomb + one-click ask
         Wait: 24 hours

Day 2 → Email 3: Short story + soft ask
         Wait: 48 hours

Day 4 → Email 4: "Are you in or out?" direct ask
         Wait: 24 hours

Day 5 → Email 5: The goodbye — last chance

AFTER DAY 5 — SPLIT:
  IF clicked any link in sequence:
    → Apply tag: zg.click-seq.clicked
    → Remove tag: zg.click-seq.entered
    → Apply tag: zg.click-seq.completed
    → Enter: 03_Survey_Funnel OR active nurture

  IF did NOT click any link:
    → Apply tag: zg.click-seq.cold
    → Remove tag: zg.click-seq.entered
    → Suppress for 90 days (no emails during suppression)
    → After 90 days: attempt one final re-engagement, then remove if no response

Exit on purchase: apply zg.click-seq.converted → buyer onboarding
Exit on unsub: apply zg.click-seq.unsub → remove all sequences
```

---

## 03 — Survey Funnel (ASK Method)

**Goal:** Segment list into buyer buckets. Capture language. Identify deepest pain.

```
Entry: Completion of Click Sequence (clicked) OR dedicated survey opt-in page
Tags: zg.survey.entered / responded / bucket-a / bucket-b / no-response

Day 0 → Email 1: Survey invite (why we're asking + what they get)
         Apply tag: zg.survey.entered
         Wait: 48 hours

Day 2 → IF no open: Email 2 (reminder) to non-openers only
         IF opened: skip Email 2
         Wait: 48 hours

Day 4 → Email 3: Last chance (to all who haven't completed survey)

SURVEY COMPLETION SPLITS:
  Response indicates Bucket A:
    → Apply tag: zg.survey.bucket-a
    → Apply tag: zg.survey.responded
    → Enter: Bucket A tailored sequence

  Response indicates Bucket B:
    → Apply tag: zg.survey.bucket-b
    → Apply tag: zg.survey.responded
    → Enter: Bucket B tailored sequence

  No response after Day 4:
    → Apply tag: zg.survey.no-response
    → Enter: default nurture sequence

Post-survey thank-you page: deliver promised insight + introduce next step
Exit on purchase: zg.survey.converted
Exit on unsub: zg.survey.unsub
```

---

## 04 — Webinar Campaign

**Goal:** Register → attend → convert. Drive attendance and offer uptake.

```
Entry: Webinar registration form submission
Tags: zg.webinar.registered / attended / offer-seen / converted

ON REGISTRATION:
  → Apply tag: zg.webinar.registered
  → Send: confirmation email (immediate) with join link
  → Add to reminder sequence

REMINDER SEQUENCE:
  Day -3 (3 days before): Reminder + build anticipation
  Day -1 (day before):    What to prepare / mindset
  Day 0 morning:          It's today! Here's your link
  Day 0 (-30 min):        Starting soon

ATTENDANCE SPLIT (post-webinar):
  IF attended (tag applied by platform during event):
    → Apply tag: zg.webinar.attended
    → Enter: Attended follow-up sequence

  IF registered but did not attend:
    → Apply tag: zg.webinar.no-show
    → Enter: No-show replay sequence

ATTENDED FOLLOW-UP (3 emails):
  +2h:  Replay available + summary
  +24h: Key insight + offer reminder
  +48h: Offer closes [real deadline]

NO-SHOW REPLAY SEQUENCE (3 emails):
  +4h:  Replay now available — here's what you missed
  +24h: Replay + offer
  +48h: Last chance — replay and offer close together

Exit on purchase: zg.webinar.converted → buyer onboarding
Exit on unsub: zg.webinar.unsub
```

---

## 05 — PLF Launch (Jeff Walker — Seed → Internal)

**Goal:** Build anticipation through PLC content, open cart, drive purchases before real deadline.

```
PRE-LAUNCH (21 days before cart open):
  Seed emails: 2-3 emails that hint at the coming launch without announcing it
  PLC 1 release (Day 0):   Apply tag: zg.plf.plc1-sent → 24h wait
  PLC 2 release (Day 7):   Apply tag: zg.plf.plc2-sent → 24h wait
  PLC 3 release (Day 14):  Apply tag: zg.plf.plc3-sent → announce cart opening

CART OPEN SEQUENCE (Day 21 → Day 26-28):
  Day 21: Cart open announcement
          Apply tag: zg.plf.cart-open
  Day 22: FAQ / top objection handling
  Day 23: Case study / social proof
  Day 24: "Here's what's inside" — offer breakdown
  Day 25: 48 hours remaining reminder
  Day 26: 24 hours remaining
  Day 27: Final hours (real deadline — no extensions unless pre-announced)
          Remove all from sequence → apply zg.plf.cart-closed

PURCHASE SPLIT (throughout cart open):
  On purchase: apply zg.plf.buyer → remove from cart sequence → buyer onboarding

POST-LAUNCH (non-buyers):
  → Apply tag: zg.plf.no-purchase
  → Wait 2 weeks
  → Enter: next nurture campaign
```

---

## 06 — Invisible Campaign (Frank Kern)

**Goal:** 30-day value delivery that embeds an offer naturally without feeling like a campaign.

```
Entry: Completion of any active campaign OR manual trigger
Duration: 30 days / 12-15 touchpoints

Structure:
  Week 1: Pure value — no offer mention. Establish expertise.
  Week 2: Stories with embedded lessons. One soft mention of offer.
  Week 3: Social proof + case studies. Offer naturally mentioned 2x.
  Week 4: Direct offer week — 3-4 emails with clear CTA.

Tag: zg.invisible.active → zg.invisible.completed
Exit on purchase: zg.invisible.converted
```

---

## 07 — 4 Day Cash Machine (Frank Kern)

**Goal:** Short revenue burst. 4 days. 4 emails. One specific offer. Real deadline.

```
Entry: Manual trigger to active warm list
Duration: 4 days

Day 1: Email 1 — Announce the thing. What it is. Why now. Who it's for.
        Apply tag: zg.4dcm.entered
        CTA: Learn more / join waitlist / buy now (depending on offer)

Day 2: Email 2 — The story behind it. Why you created this.
        CTA: same link

Day 3: Email 3 — Proof + FAQ. Handle the top 3 objections.
        CTA: same link

Day 4: Email 4 — Deadline reminder. Real close time stated clearly.
        IMPORTANT: DO NOT extend unless you pre-announced a possible extension.
        Apply tag: zg.4dcm.closed (on all non-buyers at end of Day 4)

Purchase at any point:
  → Apply tag: zg.4dcm.converted
  → Remove from sequence
  → Buyer onboarding
```

---

## Tag Master List (ZoltanGero)

| Tag | Meaning |
|-----|---------|
| zg.onboard.entered | Entered onboarding flow |
| zg.onboard.completed | Completed full onboarding |
| zg.onboard.converted | Bought during onboarding |
| zg.click-seq.clicked | Engaged in click sequence |
| zg.click-seq.cold | Did not click — cold subscriber |
| zg.survey.bucket-a | Survey segment A |
| zg.survey.bucket-b | Survey segment B |
| zg.webinar.attended | Attended live webinar |
| zg.webinar.no-show | Registered but did not attend |
| zg.plf.buyer | Purchased during PLF launch |
| zg.plf.cart-open | Cart open period active |
| zg.4dcm.converted | Purchased during 4DCM |
| zg.global.buyer | Global buyer tag (all purchases) |
| zg.global.unsub | Unsubscribed from all |
