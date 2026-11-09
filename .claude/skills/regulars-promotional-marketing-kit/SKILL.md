---
name: "regulars-promotional-marketing-kit"
description: "Build a Regulars client's onboarding print kit in Canva: window poster, table sticker, countertop poster, with editable links, print PDFs, verified QR and a handoff note."
---

# Regulars Promotional Marketing Kit

One client in, one branded kit out: three editable Canva designs, print ready PDFs in the sizes the client chooses, a verified QR on every piece, and a short handoff note. The master templates are never edited for a client; every client gets copies.

The argument is the venue name, for example `/regulars-promotional-marketing-kit Støvring Pizza`. If no name is given, ask for it.

## The three pieces

1. **Window or wall poster.** Visual reference: the Mikkeller "Enjoy Member Privileges" poster. Black background, serif italic headline, Regulars wordmark, tilted phone showing the venue's card, short lines bottom left, QR bottom right. Default A4 (210 x 297 mm), common alternatives A3 and 50 x 70 cm.
2. **Table sticker.** The QR is the hero. Venue logo on top, QR in the middle, CTA under it, Regulars wordmark at the bottom. Default 70 x 70 mm round, alternatives 80 mm round or 70 x 70 mm square.
3. **Countertop poster.** Logo, QR, CTA and one short line on why to join. Default A6 (105 x 148 mm), alternative A5.

## Master templates

The masters live in a Canva folder called `Regulars Promo Kit · Masters`, one design per piece:

* `MASTER · Window poster`
* `MASTER · Table sticker`
* `MASTER · Countertop poster`

Find them with Canva search-folders and list-folder-items (or search-designs "MASTER ·"). Never edit a master during a client run; always copy-design first.

**If the masters do not exist yet (first run):** ask Maia for the Mikkeller Canva file or link she wants as the reference, read it with read-design, then build the three masters in that folder. Every replaceable element gets a fixed placeholder so it can be found and swapped:

* Text: `{{VENUE}}`, `{{CTA}}`, `{{WHY}}`, `{{LINE1}}`, `{{LINE2}}`
* Images: an element named or placed as LOGO, CARD, QR
* Colours: background and accent use two colours only, so recolouring is two swaps

Show Maia the three masters and get her OK before using them for a client. If her Canva plan has brand templates, publish the masters as brand templates and use autofill with these same field names; otherwise copy and edit.

## Step 1. Collect the client's details (once)

Ask in one go, with AskUserQuestion where options make sense:

1. Venue name, exactly as they write it.
2. Logo, PNG or SVG with transparency, at least 600 px wide. Ask for a white version and a dark version if they have both.
3. Brand colours, as hex. Main colour and one accent.
4. Membership card artwork: the venue's current card as it looks in Wallet. First source is the Regulars dashboard (dashboard.getregulars.com, open the program, card preview); otherwise a clean screenshot from the client.
5. Signup link (`https://cards.getregulars.com/c/<card id>`) or the signup QR. If only a QR image is given, decode it to get the link.
6. Print sizes for each piece (offer the defaults above) and whether the printer needs bleed, and how much (3 mm is standard).
7. Language: English, Danish or both.

If the signup link or the card artwork is missing, stop and ask for the correct asset. Never use a QR from a member's own card; that is one person's code. If the dashboard shows the program as Inactive, say so first: every QR in the kit will be dead until it is activated.

## Step 2. Prepare the assets

* **QR:** generate it fresh from the signup link with Python `qrcode`, error correction Q, quiet zone at least 4 modules, PNG at 2000 px or more. Default is dark code on a light square; a light code on dark is allowed on the poster but must pass the scan check. Decode the file with OpenCV before uploading; it must return the link exactly.
* **Logo:** trim to its content, keep transparency.
* **Card:** crop to the card, rounded corners with transparency, no white corners. The Regulars standard member name on card visuals is Caroline; if the client's card artwork shows a placeholder name like John, ask whether to keep it.
* **Phone for the window poster:** if the Regulars poster kit (`card-generator`) is available, build the tilted phone with `compose-poster.js` and use that image as the CARD element on the poster, never changing the phone placement. If it is not available, place the flat card artwork in the master's phone frame and say so in the handoff.
* Upload each asset to Canva with create-upload-url, then use the returned asset in the designs.

## Step 3. Build the client's designs

For each piece:

1. copy-design the master into a client folder `Regulars Promo Kit · <Venue>`, named `<Venue> · Window poster` and so on. Use move-item-to-folder if needed.
2. edit-design: replace `{{VENUE}}`, swap LOGO, CARD and QR images, set the two brand colours, fill the copy.
3. If the chosen size differs from the master, resize-design to the new size, then read-design and fix the layout for the new proportions: logo, QR and CTA re-centred, nothing within 5 mm of the trim edge, text sized for reading distance.
4. If bleed is required, make the background run past the trim by the bleed amount on every side and keep all content inside the safe area.

Rules for the QR on every piece and every size:

* Always square, never stretched or rotated.
* Clear space around it of at least 4 modules, no text or graphics inside that space.
* Minimum printed size 20 mm on the table sticker, 25 mm on the countertop poster, 35 mm on the window poster.
* Strong contrast with what is behind it.

## Step 4. Copy

Short, about joining the venue's membership, nothing else.

* Default CTA: `Scan to join <Venue>.` Danish: `Scan og bliv medlem af <Venue>.`
* Countertop "why" line: one sentence about what the member gets, only using a benefit the venue has confirmed in writing. If none is confirmed, use a neutral line: `Your card lives in your Wallet.` / `Kortet ligger i din Wallet.`
* Window poster headline `Enjoy Member Privileges` stays as in the Mikkeller reference unless Maia changes it. Up to two lines under the phone, same rule on benefits.
* Never invent a reward, discount or perk.

## Step 5. Export and verify

1. export-design each design as PDF for print (and as PNG for checking). Use the print quality option and include bleed if the export offers it.
2. Check every exported file: the page size matches the chosen size (plus bleed when asked), the QR is square, and the QR decodes with OpenCV to the exact signup link. A piece whose QR does not decode is not finished.
3. Open the signup link in the browser and confirm it lands on the venue's Regulars signup page with the right card. Note it if the program is Inactive.
4. Look at each export yourself: nothing cut at the edge, logo sharp, colours right.

## Step 6. Deliver

Give Maia:

* The three editable Canva links, one per piece.
* The print PDFs, sent as files, named `01-window-poster-<slug>-<size>.pdf`, `02-table-sticker-<slug>-<size>.pdf`, `03-countertop-poster-<slug>-<size>.pdf` (with `-da` / `-en` when both languages), and a zip of all of them.
* The handoff note below, filled in.

Handoff note template:

> **<Venue> · Regulars promotion kit**
> Signup link: <link> (program status: Active / Inactive)
> 1. Window or wall poster, <size>, <bleed>. Place at eye height by the entrance or in the window, facing the street.
> 2. Table sticker, <size>, <round or square>, <bleed>. One on each table, in reach of a seated guest.
> 3. Countertop poster, <size>, <bleed>. By the till or where guests order and pay.
> Before printing: scan one printed proof with a phone and check it opens the signup page.

If the computer is linked, also save the PDFs to `~/Documents/Master/Regulars/Promotion Kit Offline/<Venue>/print/`.

## Rules that never bend

* Masters stay clean. Every client gets copies.
* Use the client's current card design wherever a card appears.
* Every QR is generated from this client's signup link and verified on every exported file.
* Apple rules on the poster: never imply an Apple partnership; Wallet is mentioned only as where the card lives.
* Never send anything to the client or anyone else on Maia's behalf; show the draft email and wait for her OK.
* Never enter credentials. If Canva or the dashboard needs a login, Maia logs in.