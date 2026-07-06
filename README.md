# Cellar Book — setup

A wine cellar inventory + tasting journal that installs on your phone like a normal app. All data lives on your device; nothing is sent anywhere.

## Get it onto your phone (once-off, ±5 minutes)

The app needs to be served over HTTPS to install as a real app. GitHub Pages does this for free:

1. Go to github.com → **New repository** → name it `cellarbook` → set it to **Public** → Create.
2. Click **uploading an existing file** and drag in all 5 files from this folder (`index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`). Commit.
3. Repo **Settings → Pages** → under "Branch" choose `main` and `/ (root)` → Save.
4. After a minute your app is live at `https://<your-username>.github.io/cellarbook/`
5. Open that URL in **Chrome on your phone** → menu (⋮) → **Add to Home screen** → **Install**.

You now have a Cellar Book icon on your home screen. It opens full-screen, works offline, and keeps your data on the phone.

## What else it tracks

- **Bottles opened.** "Open a bottle" logs the date and price, so Stats shows bottles opened per year and what you've drunk in Rand terms. Drinking the last bottle removes the wine from the cellar (Undo on the popup brings it back), and opening another bottle of a wine already in your journal won't create a duplicate entry. Stats → View & edit log lets you delete accidental log entries.
- **Tasting search & history.** Search the journal by wine, vintage or notes; wine cards show a Notes (n) button that jumps to all past tastings of that bottle.
- **Wishlist.** The Cellar tab has a Cellar / Wishlist toggle for bottles you're hunting; "Bought it" moves a wish straight into the cellar form.
- **Sorting.** Sort the cellar by newest, drink-by urgency, score, vintage, or name.
- **Formats and purchase dates.** Bottles can be halves, magnums, etc., and carry the date you bought them.

## PDF inventory

**Settings → Export cellar as PDF** produces a restaurant-style wine list — sections in Sparkling → Rosé → White → Red → Dessert → Fortified order, each wine as vintage, name and price with an italic detail line (varietal, region, bin, quantity, score, drink window), plus bottle and value totals. Needs internet the first time (it fetches the PDF library), then it's cached.

## Backups and Google Drive

**Settings → Share backup** opens your phone's share sheet — pick Google Drive and the backup is saved there in two taps (it travels as a .txt file because Android restricts which file types can be shared; the content is the same and restore accepts it directly). To restore (on this phone or a new one), **Restore from backup** opens the file picker, which can browse Drive directly. A backup after any big cellar update is a good habit.

## Backups

Your data is stored in the app on your device. Tap **Backup** (top right) → **Export backup** every so often and drop the JSON file in your cloud drive. **Restore from backup** loads it back — including onto a new phone.

## Filling in bottles quickly

Four free routes, all in the bottle and tasting forms:

- **Scan barcode** — point the camera at the EAN on the back label. If the wine is in the free Open Food Facts database, name and producer fill in instantly and exactly. Big producers usually hit; small estates often won't.
- **Paste copied text** — the best reader on your phone is Google Lens (in your camera or Photos app). Read the label there, copy the text, then tap this button: Cellar Book parses out the vintage and name candidates.
- **Read label (OCR)** — the built-in reader described below.
- Or just type it — the wine name field suggests wines already in your cellar.

## Reading labels from photos

The camera button in the bottle and tasting forms attaches a label photo to the record. Tap **Read label** and on-device OCR runs a two-pass read (auto layout + sparse text sweep) over an enhanced high-resolution copy of the photo — grayscale, contrast-stretched — then fills in the vintage and the most prominent line as the wine name, with other readable lines as tappable suggestions (boilerplate like volumes and alcohol percentages is filtered out). Everything runs on your phone — nothing is sent anywhere. First use downloads a few MB; a scan takes 15–25 seconds. It still works best on straight-on, well-lit shots — script fonts and heavy foil remain OCR's blind spot.

## What else it tracks

- **Bottles opened.** "Open a bottle" logs the date and price, so Stats shows bottles opened per year and what you've drunk in Rand terms. Drinking the last bottle removes the wine from the cellar (Undo on the popup brings it back), and opening another bottle of a wine already in your journal won't create a duplicate entry. Stats → View & edit log lets you delete accidental log entries.
- **Tasting search & history.** Search the journal by wine, vintage or notes; wine cards show a Notes (n) button that jumps to all past tastings of that bottle.
- **Wishlist.** The Cellar tab has a Cellar / Wishlist toggle for bottles you're hunting; "Bought it" moves a wish straight into the cellar form.
- **Sorting.** Sort the cellar by newest, drink-by urgency, score, vintage, or name.
- **Formats and purchase dates.** Bottles can be halves, magnums, etc., and carry the date you bought them.

## PDF inventory

**Settings → Export cellar as PDF** produces a restaurant-style wine list — sections in Sparkling → Rosé → White → Red → Dessert → Fortified order, each wine as vintage, name and price with an italic detail line (varietal, region, bin, quantity, score, drink window), plus bottle and value totals. Needs internet the first time (it fetches the PDF library), then it's cached.

## Backups and Google Drive

**Settings → Share backup** opens your phone's share sheet — pick Google Drive and the backup is saved there in two taps (it travels as a .txt file because Android restricts which file types can be shared; the content is the same and restore accepts it directly). To restore (on this phone or a new one), **Restore from backup** opens the file picker, which can browse Drive directly. A backup after any big cellar update is a good habit.

## Backups

Your data is stored in the app on your device. Tap **Backup** (top right) → **Export backup** every so often and drop the JSON file in your cloud drive. **Restore from backup** loads it back — including onto a new phone.

## Filling in bottles quickly

Four free routes, all in the bottle and tasting forms:

- **Scan barcode** — point the camera at the EAN on the back label. If the wine is in the free Open Food Facts database, name and producer fill in instantly and exactly. Big producers usually hit; small estates often won't.
- **Paste copied text** — the best reader on your phone is Google Lens (in your camera or Photos app). Read the label there, copy the text, then tap this button: Cellar Book parses out the vintage and name candidates.
- **Read label (OCR)** — the built-in reader described below.
- Or just type it — the wine name field suggests wines already in your cellar.

## Reading labels from photos

Two options, both from the same camera button in the bottle and tasting forms:

**Free OCR (no key needed).** "Read text (free OCR)" runs entirely on your phone. It fills in the vintage and the most prominent line as the wine name, and shows the other lines it read as tappable suggestions. First use downloads a few MB; works best on straight-on, well-lit shots of printed labels. Script fonts and foil can defeat it.

## AI label reading (optional)

The camera button in the bottle and tasting forms attaches a label photo. To have the app *read* the label and auto-fill the wine name, producer, vintage, varietal and region:

1. Create an API key at console.anthropic.com (Settings → API keys).
2. In the app: **Settings** (top right) → paste the key → **Save API key**.
3. From then on, taking a label photo automatically fills in the form. Each scan costs a fraction of a cent, billed to your Anthropic account.

The key is stored only on your device and is never included in backups. Without a key, photos still attach to bottles and tastings — they just won't auto-fill.

## Notes

- Any static host works (Netlify, Cloudflare Pages) if you prefer those over GitHub Pages.
- If you later update `index.html`, just upload the new version to the repo — the app refreshes itself on next launch with internet.
