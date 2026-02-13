---
name: section-11
description: Evidence-based endurance cycling coaching protocol (v11.4). Use when analyzing training data, reviewing sessions, generating pre/post-workout reports, planning workouts, answering training questions, or giving cycling coaching advice. Always fetch athlete JSON data before responding to any training question.
---

# Section 11 — AI Coaching Protocol

## First Use Setup

On first use:

1. **Check for DOSSIER.md** in the workspace
   - If not found, fetch template from: https://raw.githubusercontent.com/CrankAddict/section-11/main/DOSSIER_TEMPLATE.md
   - Ask the athlete to fill in their data (zones, goals, schedule, etc.)
   - Save as DOSSIER.md in the workspace

2. **Set up JSON data source**
   - Athlete creates a private GitHub repo for training data
   - Set up automated sync from Intervals.icu to `latest.json` and `history.json`
   - Save both raw URLs in DOSSIER.md under "Data Source"
   - `latest.json` — current 7-day snapshot + 28-day derived metrics
   - `history.json` — longitudinal data (daily 90d, weekly 180d, monthly 3y)
   - See: https://github.com/CrankAddict/section-11#2-set-up-your-data-mirror-optional-but-recommended

3. **Configure heartbeat settings**
   - Fetch template from: https://raw.githubusercontent.com/CrankAddict/section-11/refs/heads/main/openclaw/HEARTBEAT_TEMPLATE.md
   - Ask athlete for their specific values:
     - Location for weather checks (city/area)
     - Timezone
     - Valid outdoor riding hours
     - Weather thresholds (min temp, max wind, max rain %)
     - Preferred notification hours
   - Save as HEARTBEAT.md in the workspace

Do not proceed with coaching until dossier, data source, and heartbeat config are complete.

## Protocol

Fetch and follow: https://raw.githubusercontent.com/CrankAddict/section-11/main/SECTION_11.md

**Current version:** 11.4

## Data Hierarchy
1. JSON data (always fetch latest.json first, then history.json for longitudinal context)
2. Protocol rules (SECTION_11.md)
3. Athlete dossier (DOSSIER.md)
4. Heartbeat config (HEARTBEAT.md)

## Required Actions
- Fetch latest.json before any training question
- Fetch history.json when trend analysis, phase context, or longitudinal comparison is needed
- No virtual math on pre-computed metrics — use fetched values for CTL, ATL, TSB, ACWR, RI, zones, etc. Custom analysis from raw data is fine when pre-computed values don't cover the question.
- Follow Section 11 C validation checklist before generating recommendations
- Cite frameworks per protocol (checklist item #10)

## Report Templates

Use standardized report formats from `/examples/reports/`:
- **Pre-workout:** Readiness assessment, Go/Modify/Skip recommendation — see `PRE_WORKOUT_TEMPLATE.md`
- **Post-workout:** Session metrics, plan compliance, weekly totals — see `POST_WORKOUT_TEMPLATE.md`
- **Brevity rule:** Brief when metrics are normal. Detailed when thresholds are breached or athlete asks "why."

Fetch templates from:
- https://raw.githubusercontent.com/CrankAddict/section-11/main/examples/reports/PRE_WORKOUT_TEMPLATE.md
- https://raw.githubusercontent.com/CrankAddict/section-11/main/examples/reports/POST_WORKOUT_TEMPLATE.md

## Heartbeat Operation

On each heartbeat, follow the checks and scheduling rules defined in your HEARTBEAT.md:
- Daily: training/wellness observations (from latest.json), weather (only if conditions are good)
- Weekly: background analysis (use history.json for trend comparison)
- Self-schedule next heartbeat with randomized timing within notification hours
