---
name: "regulars-offline-kit"
description: "Build the Regulars Promotion Kit Offline for one client venue: poster, A6 counter flyer, 7 cm table sticker, 12 cm window sticker, Danish and English, print PDFs and a review page. Use when Maia or Hans names a client and asks for the offline kit."
---

# Regulars Promotion Kit Offline

One client in, four print pieces out, in Danish and English, ready for the venue to print. Nothing is designed per client. Only the logo, the card on the phone, the QR, the two poster lines and the language change. Everything else is locked.

The argument is the venue name, for example `/regulars-offline-kit Støvring Pizza og Sandwich`. If no name is given, ask for it and stop.

## Where things live

- Poster kit (Hans Christian's scripts, never redesign): `regulars-poster-kit/card-generator/`. On Maia's Mac it is under `~/Documents/Master/Regulars/`. In a cloud session, unzip the kit the user attached into its own folder. Contains `generate-card.js`, `compose-poster.js`, `render-poster.js`, `poster-template.html` (holds the Regulars wordmark as base64), `render-kit.js`.
- Output folder per client on the Mac: `~/Documents/Master/Regulars/Promotion Kit Offline/<Venue>/` with `assets/` for inputs and `print/` for PDFs.
- Needs Node 22, `pnpm install --ignore-workspace` inside `card-generator` (a fresh cloud container has no node_modules, run it first), and Chrome headless. In the cloud container set `CHROME_PATH=/opt/pw-browsers/chromium-1194/chrome-linux/chrome`.
- Apple rules apply because the poster shows an iPhone and Wallet: official iPhone 18 Pro bezel only, never imply an Apple partnership, text beside the device.

## Step 1. Collect the four inputs

Every kit needs exactly these. Collect all four before rendering anything.

1. Venue name as they write it, plus website or Instagram.
2. Logo, white on transparent PNG, at least 600 px wide.
3. The card: the 24 character card id, or a clean screenshot of the card as it looks in Wallet.
4. The sign up link, `https://cards.getregulars.com/c/<card id>`. The QR is generated from it. Never use the QR printed on a member's card, that is one person's code.

Plus language set (default both, da and en) and card type (membership, stamp, prepaid).

### The Regulars dashboard, first source

`https://dashboard.getregulars.com/programs`, opened in the user's Chrome. If it shows "Welcome back" sign in, ask the user to log in and wait; never type credentials. Two Chrome browsers may be connected on Maia's Mac and the login lives in only one of them; if a reload still shows the sign in page, ask which browser she logged in with and switch. Then:

1. The page opens on the Regulars internal organisation. Clients are separate organisations: click the organisation switcher at the bottom of the left sidebar (the current name with a small arrow) and pick the client from the alphabetical list.
2. Programs shows the client's cards with a status badge. Note which are **Inactive**. An inactive program has a dead sign up link; the kit can be built but must say so, and nothing is printed until the program is activated.
3. Open the card. The URL is `dashboard.getregulars.com/program-details/<card id>`, which gives the card id.
4. Click **Links and QR codes**. The panel shows the Program link (`https://cards.getregulars.com/c/<card id>`) with Copy link and Download QR. Use the link to generate the white QR yourself.
5. The card logo and banner are images on the page hosted on `reg-getregulars-imagegallery-test.s3.eu-north-1.amazonaws.com`. The container and page scripts cannot fetch them (proxy and CORS), and base64 cannot travel back through the browser tool. Working route: open the logo URL in a new tab, scale the `img` up with JS (`transform: scale(3)`, white body), take a `zoom` screenshot of its box with `save_to_disk`, and turn that capture into white on transparent with the alpha trick below. It gives about 1400 px wide, good for all four pieces.

### Fallbacks

- If the dashboard is not reachable, ask for a card screenshot and the link. From a screenshot the logo can be lifted the same way but is soft; say it should be replaced by the dashboard file before sending.
- Venue websites are often ordering pages with no clean logo; do not spend more than a couple of minutes there.

Lifting a dark logo from a light background (Python, PIL, numpy): take the median of a corner as `bg`, `alpha = clip((bg - luminance) / (bg - 70), 0, 1) ** 0.9`, set RGB to white, trim to the alpha bounding box, save PNG. Invert the luminance for a light logo on dark.

## Step 2. Prepare the assets

Inside `card-generator`, slug = venue name lowercased, letters and digits, hyphens.

- `assets/<slug>-logo-white.png`: the logo.
- `assets/<slug>-poster-qr.svg`: WHITE QR of the sign up link, `qrcode.make(link, image_factory=qrcode.image.svg.SvgPathImage, error_correction=ERROR_CORRECT_M, border=0)` then add `fill="#ffffff"` to the path. A black QR on the black poster is the classic mistake.
- `card-<slug>.png`: the card. From the pipeline when the card id is available (`generate-card.js`, name on the card is always Caroline). From a screenshot: upscale 3x, apply a rounded rectangle alpha mask with radius about 5.5 percent of the width so no white corners show, then **pad it**: 4 percent transparent on each side and 30 percent transparent below. Without the padding the warp pulls a screenshot card down to the bottom edge of the phone and it looks misaligned; the pipeline's own cards are taller and do not need it.

## Step 3. Poster (Hans's pipeline, untouched)

```
node compose-poster.js card-<slug>.png poster-phone-<slug>.png
node render-poster.js input-poster-<slug>.json      # Danish
node render-poster.js input-poster-<slug>-en.json   # English
```

`input-poster-<slug>.json`:

```json
{"phoneImage":"poster-phone-<slug>.png","posterQr":"assets/<slug>-poster-qr.svg","bullets":["...","..."],"qrSize":210,"bulletSize":32}
```

Each run writes `poster.png`; rename it right away to `01-poster-<slug>-da.png` / `-en.png`.

Poster lines, approved by Maia on 9 Nov 2026, two lines, never write "under a minute":

- Stamp card, en: `Collect the stamps.` / `Your card lives in your Wallet.`; da: `Saml stemplerne.` / `Kortet ligger i din Wallet.`
- Membership, en: `Show your card every visit.` / `Your card lives in your Wallet.`; da: `Vis dit kort ved hvert besøg.` / `Kortet ligger i din Wallet.`
- Prepaid, en: `Load your card once, pay with one tap.` / `Your card lives in your Wallet.`; da: `Fyld kortet op én gang, betal med ét tryk.` / `Kortet ligger i din Wallet.`
- A third line with the reward is added only when the venue has confirmed the reward in writing. Never invent a benefit.

The headline `Enjoy Member Privileges` is locked and stays in English on every poster. The template in use since 5 Nov 2026 has the website fonts (Instrument Serif italic, Google Sans Flex) and the larger phone (`left:-6%; top:27%; width:104%`), approved by Maia, pending Hans Christian; `poster-template-original.html` keeps his original. Never edit the phone placement yourself.

## Step 4. The three small pieces

`input-kit-<slug>.json`: `{"venue":"<Venue>","logo":"assets/<slug>-logo-white.png","qr":"assets/<slug>-poster-qr.svg","lang":"da"}` and a copy with `"lang":"en"` and venue `"<Venue> EN"`.

```
node render-kit.js input-kit-<slug>.json out-<slug>
node render-kit.js input-kit-<slug>-en.json out-<slug>
```

It writes, at 300 dpi: `02-counter-flyer` 1240x1748 (A6), `03-table-sticker` 827x827 (7 cm), `04-window-sticker` 1417x1417 (12 cm). Stickers are a black disc on transparent, logo on top, white QR, headline `Become a regular` / `Bliv stamgæst` in Instrument Serif italic, Regulars wordmark below. Rename the outputs with `-da` / `-en`. Logo slots are 460x200 (flyer), 260x100 (table), 440x170 (window), so wide logos fit; do not change anything else in the script.

## Step 5. Verify the QR, then print PDFs

Decode the QR from every rendered file with OpenCV: flatten onto black, invert so the code is dark, crop to the white bounding box of the code with a margin, downscale to about 20 percent, pad with white, `cv2.QRCodeDetector().detectAndDecode`. Each must return the client's link exactly. A kit whose QR does not decode is not finished.

With PIL, one PDF per piece and language, page size equal to the physical size: poster 210 mm wide, flyer 105 mm, table sticker 70 mm, window sticker 120 mm. Flatten transparent stickers onto white (the white square shows the printer where the round cut goes). `im.save(f, 'PDF', resolution=im.width/(mm/25.4))`. Name them `01-poster-<slug>-da.pdf` and so on. Zip them as `<Venue>-Promotion-Kit-Offline-print-PDF.zip`.

## Step 6. Deliver

- Save PNGs in the client folder and PDFs in its `print/` subfolder on the Mac when the computer is linked (`device_commit_files`, with `force` when replacing); otherwise send the zip.
- Publish a review page as an artifact (not PNG attachments): title `<Venue> Promotion Kit`, a Dansk / English switch that hides the inactive language with the `hidden` attribute (a plain `display:none` on `[data-lang]` loses to the image rule), each piece in its own frame on a checker ground so the round cut reads, under each piece exactly what it says, its size and where it goes, a chip with the QR link, and the checklist below. Open it for the user with the Artifact open action when they ask.
- Tell the user in a few lines what each piece says and what is still open. Keep it as a draft until every check passes.

## Checks before anything goes to the venue

1. The program is **Active** in the dashboard. Inactive means every QR in the kit is dead; say it first and loudest.
2. The QR was generated from `cards.getregulars.com/c/<card id>` for this client, is white on every piece, decoded back to the link from every rendered file, and one printed proof was scanned with a phone.
3. The logo is the client's real file (dashboard), not a crop from a card screenshot.
4. The card on the phone shows the name Caroline, from the pipeline, not a dashboard preview with John.
5. The poster lines name no benefit the client has not approved.
6. The poster came out of the poster kit with the phone placement untouched.
7. Files are named 01 to 04 with the language suffix and sent in one email, using the email template in the Regulars Promotion Kit Guide.

## Rules that never bend

- Black background, white text, Regulars wordmark on every piece, sizes A4, A6, 7 cm, 12 cm.
- No phone template on the small pieces, only logo, QR, headline, wordmark. No small print.
- Never send anything on Maia's behalf (Slack, email) without showing the draft and getting her OK.
- Never enter credentials anywhere. If a login is needed, the user logs in.