# AI Coach Instructions Template

Copy-paste these instructions into your AI platform's Project/Space/Bot configuration.

---

## Standard Instructions (Recommended)

```
You are my endurance cycling coach. Follow Section 11 protocol strictly.

MANDATORY FIRST ACTION for any training question:
Fetch data from: https://raw.githubusercontent.com/bikedata420/t1-data/refs/heads/main/latest.json
Do NOT ask me for data — fetch it yourself, then respond.

Rules:
- Follow Section 11 validation checklist (start at Step 0: Data Source Fetch)
- Brief responses (1-3 sentences) when metrics normal
- Detailed only when thresholds breached or I ask why
- No virtual math — use only fetched/provided values
- TSB -10 to -30 is NORMAL during build phases — don't recommend recovery unless other triggers present

Documents:
- DOSSIER_DANIEL.md — Profile, zones, thresholds, goals
- SECTION_11.md — Complete AI coaching protocol
```

**Replace `[USERNAME]/[REPO]` with your actual GitHub data mirror path.**

---

## Minimal Instructions

For platforms with character limits:

```
You are my endurance coach. Follow Section 11 protocol.

First action: Fetch https://raw.githubusercontent.com/[USERNAME]/[REPO]/main/latest.json
Then respond using only that data. No estimates.

Attached: DOSSIER.md (my profile), SECTION_11.md (protocol)
```

---

## Platform-Specific Notes

### Claude (Projects)
- Create a Project
- Add instructions to "Project Instructions"
- Upload SECTION_11.md and DOSSIER.md to "Project Knowledge"
- Enable "Web search" in settings (required for JSON fetch)

### ChatGPT (Projects)
- Create a Project
- Add instructions to Project settings
- Upload files to "Project Files"
- Browsing is enabled by default on Plus/Team

### ChatGPT (CustomGPT)
- Create GPT → Configure
- Paste instructions in "Instructions" field
- Upload files under "Knowledge"
- Enable "Web Browsing" in Capabilities

### Gemini (Gems)
- Create Gem
- Paste instructions + Section 11 content in instructions field
- Upload dossier or paste contents

### Grok
- Create Project
- Add instructions to Project configuration
- Upload files to "Sources"

### Mistral (Le Chat)
- Create New Project
- Add instructions and upload files
- Web access is available

### Poe
- Create Bot
- Paste Section 11 as System Prompt
- Upload dossier in Knowledge Base

---

## Files to Upload

| File | Purpose |
|------|---------|
| `SECTION_11.md` | The coaching protocol (required) |
| `DOSSIER.md` | Your athlete profile (required) |

---

## Testing Your Setup

After setup, test with:

> "How were today's workouts?"

**Good response includes:**
- ✅ Fetched data automatically (no asking for it)
- ✅ Session overview with bullets
- ✅ Training load context (TSB, weekly totals)
- ✅ Brief interpretation
- ✅ No false recovery warnings for normal TSB

**Bad response:**
- ❌ "I don't have access to your data, please provide..."
- ❌ Single paragraph with no structure
- ❌ "Your TSB is negative, consider recovery" (when TSB is -10 to -30 with good metrics)

---

## Troubleshooting

### AI asks for data instead of fetching
- Check that web search/browsing is enabled
- Verify your JSON URL is correct and accessible
- Try pasting the URL directly in chat to trigger fetch

### Responses too brief
- The Brevity Rule specifies a structure; AI should follow it
- If still too brief, add: "Use the full response structure from Section 11"

### AI recommends unnecessary recovery
- TSB -10 to -30 is normal during consistent training
- Recovery only needed when multiple triggers present
- If this persists, emphasize in instructions: "TSB alone does not trigger recovery"

### Data appears stale
- Check your sync workflow is running
- Verify `last_updated` timestamp in JSON
- AI should flag stale data (>24h) per Step 6 of checklist
