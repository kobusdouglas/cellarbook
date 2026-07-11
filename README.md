# Cellar Book — setup & guide

A wine cellar inventory and tasting journal that installs on your phone like a normal app. All data lives on your device; nothing is sent anywhere.

## Get it onto your phone (once-off, ±5 minutes)

The app needs to be served over HTTPS to install as a real app. GitHub Pages does this for free:

1. Go to github.com → **New repository** → name it `cellarbook` → set it to **Public** → Create.
2. Click **uploading an existing file** and drag in all 5 files from this folder (`index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`). Commit.
3. Repo **Settings → Pages** → under "Branch" choose `main` and `/ (root)` → Save.
4. After a minute your app is live at `https://<your-username>.github.io/cellarbook/`
5. Open that URL in **Chrome on your phone** → menu (⋮) → **Add to Home screen** → **Install**.

You now have a Cellar Book icon on your home screen. It opens full-screen, works offline, and keeps your data on the phone. To update the app later, replace `index.html` and `sw.js` in the repo — the installed app refreshes itself on the next launch with internet. Anyone else opening your URL gets their own empty cellar; your data is never visible to them.

## What it does

- **Cellar.** Bottles with producer, vintage (or **NV** for non-vintage wines), type, varietal, country, region, bin location, quantity, price (ZAR), bottle format (halves to double magnums), purchase date, a score /100, and a drink-from/drink-by window shown as a gauge on every card. Search, filter by type, and sort by newest, drink-by urgency, score, vintage, or A–Z.
- **Opening a bottle.** Tap "Open a bottle": stock drops instantly, the date and price are logged, and a confirmation sheet offers an optional tasting note — with **Undo** if it was a mis-tap. Drinking the last bottle removes the wine from the cellar (Undo brings it back). A wine is identified by **name + vintage**, so the 2020 is treated separately from the 2019. If that exact wine and vintage is already in your journal, no duplicate entry is created — you can view the existing notes or deliberately add another.
- **Tastings.** Journal entries carry the same wine identity as the cellar — producer, vintage, type, varietal, region — plus a score /100, date, notes, and photo, all prefilled when you open a bottle from the cellar. Below the notes sits an optional collapsible **Structured tasting** section — WSET-style dimensions as tap-pills (appearance, nose, palate, conclusions), with colour options that follow the wine's type and a mousse row that appears only for sparkling. Filled selections show as a compact summary line on the journal card. Below it, an **Aromas & flavours** dropdown offers the full descriptor lexicon (primary / secondary / tertiary, grouped by cluster) as tappable pills — picks are stored on the entry, shown on the card, and searchable, so \"every wine where I found blackcurrant\" is one search away. Search across every field. Wine cards show a **Notes (n)** button that filters the journal to that exact wine and vintage (tap the chip to clear).
- **Alerts.** Wines whose drinking window closes within a year, and wines past their window, with a badge on the tab.
- **Stats.** Bottles, cellar value, average scores, breakdown by type, a **maturity timeline** (bottles in their drinking window per year, current year highlighted — shows at a glance where your cellar is over- or under-stocked), top regions, journal highlights, and a **Bottles opened** panel with per-year bars and Rand totals. **View & edit log** lets you delete accidental entries (tap +1 on the bottle to restore its stock).
- **Fast scrolling.** Long pages get a slim burgundy handle on the right edge — drag it to jump anywhere in a big cellar. It fades when idle and stays out of the way on short pages.
- **Back button.** Android's back steps through the app — closes photos and forms, returns to the Cellar tab — instead of exiting.

## Reading labels from photos

The camera button in the bottle and tasting forms attaches a label photo (take one or choose from the gallery). Tap **Read label** and on-device OCR runs a two-pass read over an enhanced high-resolution copy of the photo, then fills in the vintage and the most prominent line as the wine name, with other readable lines as tappable suggestions (volumes and alcohol percentages are filtered out). Everything runs on your phone — nothing is sent anywhere. First use downloads a few MB; a scan takes 15–25 seconds. It works best on straight-on, well-lit shots of printed labels; script fonts and heavy foil remain OCR's blind spot.

## Spreadsheets: CSV import & export

**Settings → Import cellar from CSV** bulk-loads bottles from a spreadsheet — the fastest way to get a real cellar in. It matches columns by name (Name is required; Producer, Vintage — "NV" accepted — Type, Varietal, Region, Country, Bin, Qty, Price, Format, Score, Drink From, Drink To, Purchase Date, Notes all recognised under common spellings), understands SA conventions ("R 1 250" prices, dd/mm/yyyy dates, "MCC" as Sparkling), and shows a preview with counts before anything is written. Wines matching an existing name + vintage get their quantities topped up rather than duplicated. A template CSV is downloadable from the preview.

**Export cellar as CSV** produces a spreadsheet of every bottle and field — ready for Excel or Power BI. **Export tastings as CSV** does the same for the journal: every entry with wine details, score, aromas, notes, and each structured-tasting dimension in its own column.

## PDF wine list

**Settings → Export cellar as PDF** produces a restaurant-style wine list — sections in Sparkling → Rosé → White → Red → Dessert → Fortified order, sub-grouped by grape variety (alphabetical) with wines ranked cheapest to dearest within each variety (unpriced bottles first). Each wine shows vintage, name and price — plus the bottle size when it isn't a standard 750ml — with an italic detail line (producer where it isn't already in the name, region, country, bin, quantity, score, drink window), plus bottle and value totals. Needs internet the first time (it fetches the PDF library), then it's cached.

## PDF tasting journal

**Settings → Export tasting journal as PDF** produces a printable chronological journal — each tasting with its wine, date, score, structured-tasting summary, aroma picks and full notes, in the same styling as the wine list.

## Backups and Google Drive

Your data is stored in the app on your device, inside the browser's private database. It is not a file you can browse to — which is exactly why backups matter:

- **Settings → Share backup** opens your phone's share sheet — pick Google Drive and the backup is saved there in two taps. (It travels as a `.txt` file because Android restricts which file types can be shared; the content is the same and restore accepts it directly.)
- **Export backup** downloads a `.json` file instead — handy on a laptop.
- **Restore from backup** loads either format back, including onto a new phone. Restoring replaces current data.

Settings shows how long ago you last backed up and nudges you after 30 days. A backup after any big cellar update is a good habit.

## Notes

- Any static host works (Netlify, Cloudflare Pages) if you prefer those over GitHub Pages.
- Data is per browser and per device: the same URL in another browser starts empty. Moving devices = Share backup → Restore.
