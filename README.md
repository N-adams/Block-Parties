# 🎉 Block Party Permit Tracker

An interactive map-based tool for tracking block party permit applications. Built with Leaflet.js — no server required, runs entirely in the browser.

**[➜ Open the tracker](https://YOUR-USERNAME.github.io/block-party-tracker/)**

---

## What it does

- Displays each permitted block closure as a **colored line** on a map
- Color encodes urgency based on **event date proximity**:
  - **Gray** — no approval date yet (pending)
  - **Red** — approved, event within 1 week
  - **Orange** — approved, event within 2 weeks
  - **Yellow** — approved, event within 3 weeks
  - **Blue** — approved, event within 4+ weeks
- Click any line or sidebar card to see full permit details
- Searchable sidebar list
- Export all data as CSV

---

## How to deploy on GitHub Pages

1. **Fork or clone** this repository to your GitHub account
2. Go to **Settings → Pages** in your repo
3. Under "Source", select **Deploy from a branch**
4. Choose `main` branch, `/ (root)` folder — click **Save**
5. Your site will be live at `https://YOUR-USERNAME.github.io/REPO-NAME/` within a minute

---

## How to add new permit applications

### Option A — Via the web interface (easiest)
Anyone with the link can click **"+ New Application"** and fill in the form. Their entry is saved locally in their browser and appears on the map immediately. *(Note: browser-local entries don't sync to others automatically — use Option B for shared records.)*

### Option B — Edit the source file (recommended for shared, persistent records)

Open `index.html` and find the `STATIC_PERMITS` array near the top of the `<script>` section (around line 160). Add a new object following this format:

```javascript
{
  id: 5,                          // unique number — just increment
  received:   '2026-04-01',       // YYYY-MM-DD
  approved:   '2026-04-05',       // YYYY-MM-DD, or '' if still pending
  street:     '300 block of Elm St',
  cross:      'Oak Ave & Pine Ave',
  eventdate:  '2026-05-10',       // YYYY-MM-DD
  hours:      '1:00 PM – 7:00 PM',
  activities: 'Live band, food trucks, kids zone',
  applicant:  'Sarah Connor',
  contact:    '555-0123',
  lat:        37.8720,            // latitude of block center
  lng:        -122.2650           // longitude of block center
},
```

**To find lat/lng:** Open [Google Maps](https://maps.google.com), right-click the center of the block, and click the coordinates shown at the top of the context menu.

After adding your entry, commit and push `index.html`. GitHub Pages will update within ~1 minute and everyone will see the new permit.

### Option C — Submit a pull request
If you don't have write access to the repo, add your entry as described in Option B and open a pull request. A repo admin can review and merge it.

---

## Fields reference

| Field | Required | Description |
|-------|----------|-------------|
| `id` | ✅ | Unique integer — increment from last entry |
| `received` | ✅ | Date application was submitted (`YYYY-MM-DD`) |
| `approved` | — | Date permit was approved; leave `''` if pending |
| `street` | ✅ | Block description, e.g. `"400 block of Oak St"` |
| `cross` | — | Bounding intersections, e.g. `"Elm Ave & Pine Ave"` |
| `eventdate` | ✅ | Date of the event (`YYYY-MM-DD`) |
| `hours` | — | Closure time window, e.g. `"12:00 PM – 6:00 PM"` |
| `activities` | — | Free-text description of planned activities |
| `applicant` | — | Name of the person who applied |
| `contact` | — | Phone or email |
| `lat` / `lng` | ✅ | Coordinates of block center for map placement |

---

## Questions?

Open a GitHub Issue or contact the repo admin.
