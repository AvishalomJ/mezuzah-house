# Publishing the Mezuzah Landing Page on Wix

This is a self-contained landing page (**`design-2-midnight.html`**, Hebrew, or
**`design-2-midnight.en.html`**, English). The CSS and JavaScript are built into
the file — it only needs the **`images/`** folder, the **`favicon*`** files, and an
internet connection (it loads Google Fonts from the web). There is no database:
orders are sent to you over **WhatsApp**.

## The one catch with Wix

Wix **cannot host raw HTML files**, and this page (~78 KB) is far too big to paste
into Wix's *Embed HTML* box (that box only accepts ~10,000 characters). So the trick
is: **host the page on a free static host, then show it on your Wix site.**

---

## Option 1 — Embed it on your Wix page (keeps it "on Wix") ⭐

1. **Pick the file** you want live: `design-2-midnight.html` (Hebrew) or
   `design-2-midnight.en.html` (English).
2. **Host it for free.** Sign up for **Netlify**, **GitHub Pages**, or **Cloudflare
   Pages** and upload, keeping the same folder structure:
   - the chosen HTML file (rename it to **`index.html`**)
   - the **`images/`** folder
   - the **`favicon*`** files
   You'll get a public URL, e.g. `https://your-site.netlify.app`.
3. **Embed it in Wix.** In the Wix Editor: **Add → Embed Code → Embed a Site**,
   paste your URL, then stretch the box to full width/height. (Hide the Wix header/
   footer on that page if you want it to look standalone.)
4. **Publish** in Wix. Done.

---

## Option 2 — Connect your domain to the host (cleanest, best for Google) 

Skip the iframe entirely: point your domain (or a subdomain like
`shop.yourdomain.com`) straight at Netlify / GitHub Pages. Visitors get the real,
full-speed page with proper SEO. Use Wix only if you also want other Wix pages.
This is the best result if search ranking matters.

## Option 3 — Rebuild it inside the Wix Editor

Recreate the design with native Wix elements. This is the most work and you'd lose
the custom cart and "choose a mezuzah" picker. Only do this if everything *must* be
native Wix.

---

## What works once it's on Wix

✅ **Works out of the box** (Options 1 & 2):
- WhatsApp "order now" buttons
- Catalog, gallery, and FAQ
- **"Choose a specific mezuzah" picker** (pick an exact in-stock piece)
- Cart + checkout — automatically sends the order via WhatsApp
- PayPal payment link (if a PayPal user is configured)
- Google Fonts

⚠️ **Does *not* run on Wix** (these need the local Python server):
- The admin order-confirmation **email**
- Automatic **"mark as sold"** for picker items

Orders still reach you — checkout falls back to WhatsApp on its own. To change
prices, stock, or sold items, edit locally and re-upload the new HTML (see below).
Note: an iframe embed (Option 1) gets weaker SEO than Option 2, and the browser
address bar keeps showing your Wix URL.

---

## Editing content before you publish

Edit locally with the **Admin Studio**, then re-upload the result:

1. Run **`start-admin.bat`** (or `python admin-server.py`).
2. Open **http://localhost:8777/admin.html** and make your changes.
3. The tool re-renders `design-2-midnight.html` from `content.json`.
4. Re-upload that file (and any new images) to your host.

The Admin Studio is a **local editing tool only** — it is never published to Wix.
