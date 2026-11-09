---
name: "regulars-new-partner-post"
description: "Use when a new Regulars partner appears in Slack #gtm-csm (or Maia names one): research the venue, pick its best photo and make the 'Welcome {Partner}' visual plus Instagram and LinkedIn captions for approval."
---

# Regulars: New Partner Post

One new partner in, one approval-ready package out: one 'Welcome {Partner}' visual (used on both Instagram and LinkedIn), an Instagram caption and a LinkedIn caption. Same structure every time.

Never publish, schedule, react or post in Slack. Slack is read only. Output is a draft for Maia; later the approved package goes to FeedHive.

## Positioning (use in every caption)

Regulars is guest data collection for hospitality. The membership card in Apple and Google Wallet is how a venue gets to know its guests: who they are, how often they come back, and how to reach them directly. Lead with knowing your guests; the card is the how. Do not use #RethinkLoyalty.

## 1. Check #gtm-csm for new partners

Read Slack channel #gtm-csm (id C05UENNUC22). New partners are automatic posts from the **Regulars** bot:

```
:rocket: {Partner name}
:round_pushpin: {Country code}
```

- Take every :rocket: post since the last run (default: last 24 hours, or since Friday on a Monday). If Maia names a partner, do only that one.
- Before starting, check the Content calendar in the Regulars Marketing System doc: skip partners that already have a row, so nothing is made twice.
- Use the name exactly as the bot writes it (e.g. 'Sol Coffee'). Maia dictates by voice, so trust the Slack spelling and mention any difference.
- Ignore other posts (:wallet:, :gift:, :mailbox_with_mail:, joins).
- If the name looks like a person (first name + surname), list it under 'Skipped / check with Maia' instead of making a post.
- Also check the thread and search Slack for the name in case the team shared links.
- No new :rocket: posts: report 'No new partners' in one line and stop.

## 2. Identify and research the venue

- Web search '{name} {country}' and '{name} instagram' to find the official website and Instagram.
- Confirm it is the right business: address in the right country, a venue type that fits, ideally Regulars visible (wallet card, QR at the counter, link in bio). If two candidates fit, stop and ask Maia.
- From the website (or the Instagram bio if there is no website) note only stated facts: what they serve or do, signature, how they describe themselves, city.

## 3. Pick the photo

If Maia sends a photo, use that one. Otherwise review their website and the last 30 or so Instagram posts (use the browser; WebFetch is usually blocked) and choose the most aesthetic image, in this order:

1. The people or the place: owners or team in front of the venue, the facade, a candid moment of service. The Grammes sample (two owners in aprons in their doorway) is the ideal.
2. Portrait friendly: the subject sits in the upper two thirds, leaving calm space at the bottom for the text.
3. Natural, warm light with depth. Avoid flat, overexposed or very busy shots.
4. No text or graphics baked in. No identifiable children. High resolution.

Getting the file: Instagram blocks automatic downloads to the container and Chrome downloads may not land. If you cannot get the image file in one try, ask Maia to attach it (a phone screenshot of the post works).

Record the source URL and keep 2 runner ups. The photo belongs to the partner: flag that we need their OK before it goes live.

## 4. Build the visual (the 'Welcome Grammes' template)

One image, 1080x1350 (4:5), used for Instagram and LinkedIn. Build as HTML, render to PNG with Playwright at 2x. Fonts via npm (Google Fonts is blocked from the container): @fontsource/instrument-serif (400 normal and italic) and @fontsource-variable/google-sans-flex. Regulars logo: RegularsLogoWhite.png from the project files.

- **Photo:** full bleed, cropped to 4:5 with the subject in the upper half (crop from the bottom when the bottom is busy).
- **Filter (dark and moody, approved by Maia on Sol Coffee):**
  - photo filter: brightness(.68) contrast(1.05) saturate(.9)
  - vertical gradient: rgba(15,15,15,0) at 0%, .15 at 30%, .6 at 58%, .9 at 76%, solid #0F0F0F at 92%
  - soft vignette: radial-gradient(ellipse 85% 70% at 50% 38%, transparent 55%, rgba(15,15,15,.45) 100%)
  - Keep the photo's own colours; no tint, no grain.
- **Text block, bottom left, 80px side margin, 60px from the bottom:**
  - 'Welcome' in Instrument Serif regular, Regulars White #FAF9F6, 84px, line-height 1.02
  - '{Partner}' on the next line in Instrument Serif Italic, same size, same colour
- **Hairline:** 1px, rgba(250,249,246,.7), from the left margin to the right margin, 40px below the name.
- **Footer, 24px under the line:** left '{City}, {Country}' in Google Sans Flex regular 22px; right the white Regulars logo at 24px height, aligned to the right margin.
- **Partner logo:** only if Maia provides a clean file (PNG or SVG). Do not crop a blurry logo from a profile photo.
- Nothing else on the image.

Check the render: name spelled right, text sharp and readable, nothing covering faces, margins equal left and right.

## 5. Write the captions

Voice: calm, direct, confident, human. Short sentences. Outcome first. 'Guest' before signup, 'member' after. Never use: discount, deal, coupon, promo code, bargain, cashback. No exclamation marks, no hashtag campaigns. English by default; add Danish only if Maia asks, marked 'needs native check'.

**Instagram (max 4 short lines + CTA)**

```
Welcome to Regulars, {Partner}.
{One line from their website or bio about what makes them theirs.}
From today, their guests join in one tap from Apple or Google Wallet, and {Partner} gets to know who their regulars are.

Running a venue? Link in bio.
@{instagram_handle}
```

**LinkedIn (80 to 150 words)**

```
Welcome to Regulars, {Partner}.

{Two sentences on who they are, only facts from their site, bio or Slack.}

Most venues lose track of a guest the moment they pay. With a membership card in Apple and Google Wallet, {Partner} now learns who their guests are, how often they come back, and can reach them directly, with the guest's consent.

{City} just got one more spot for regulars.

Want to know your guests too? getregulars.com/demo
```

Tag the partner's LinkedIn company page if it exists. Name a membership type only if Slack or Maia confirms it.

## 6. Deliver the package

Per partner, send the PNG (also save it to Maia's Downloads folder when her computer is linked), then one message with:

- The visual and 2 runner up photos
- Instagram and LinkedIn captions
- 5W1H: Who, What, Why, Where (channel), When (proposed date), How (format)
- Sources: Slack post date, website or Instagram URL, photo source URL
- To confirm: permission to use the photo and announce, language, any fact not found
- Skipped / check with Maia

Add the rows to the Content calendar in the Regulars Marketing System doc with stage Draft. Then stop and wait for Maia's approval or edits.