---
name: "regulars-newsletter"
description: "Build a Regulars client newsletter (customer success, current clients) in the fixed dark format approved by Alexander, following his copy rules from 5 Nov 2026, and put it in Brevo as a draft. Use whenever Maia asks for a Regulars newsletter or client mail."
---

# Regulars newsletter

## Who it is for and what it must win

The Brevo list "Regulars Newsletter" (id 30) is **current clients**. Every mail is customer success, never a sales pitch: it helps clients get more value from Regulars. HC's goal, which the newsletter serves: activate and expand clients by helping them capture more guest relationships and use more of Regulars. That creates value for them and their guests and makes Regulars harder to replace. (Alexander, 5 Nov 2026.)

Before writing a single line, answer in the chat, in two sentences: **What should the reader do next? Why is that valuable for Regulars, our clients and their guests?** If there is no clear next action, there is no button; the reply to HC is the call to action.

## Alexander's copy rules (5 Nov 2026)

- **No eyebrow.** Removed by default; the title sits directly under the picture.
- **Hero title**: a confident statement, never a question. Example: "Make the busy season count." One line when it fits (max about 28 characters at 40 px); a short statement on two lines is accepted when Alexander or Maia chose the words.
- **Simple language.** "Guest data" or "guest relationships", never "first-party guest data". Do not use "card" as the product; Regulars is broader (membership, guest data, relationships). Keep it relevant across hospitality, not only cafés.
- **Do not** centre the mail on Christmas or January, and do not assume guests visit only once. A season is the occasion, not the subject.
- **CTA**: the action that gets the client using more of Regulars. If none, no button; "Just reply to this email" to HC does the job. The button is an image (see build step 3).
- Short and easy to scan: one or two paragraphs, each at most 3 lines.

Layout is fixed (approved 23 Oct 2026, prepaid mail). Per newsletter only these change: the HD picture, the title, the text, the button label and link (or no button), the preheader and the subject. Logo, button style, reply line, HC's face signature, socials and footer never change. Do not add a greeting line.

## Before writing, ask Maia for what is missing

- The picture. At least 2000 px on the long side; check dimensions with Pillow and ask for the original if smaller (phone or camera export, Unsplash or Pexels largest download, never a WhatsApp or Slack copy). Never upscale. Check the licence allows commercial use.
- What the mail is about. If Maia, Alexander or HC give finished text that fits the rules, keep it word for word.
- Never invent business facts, prices, numbers, client names, quotes or results. Check product claims against getregulars.com and against Magnus's release notes in Slack (#dev-updates, #dashboard-2_1). Do not announce a feature as live until the team confirms it is live for clients; use "launches soon" wording otherwise.

## Copy rules

**Title**: statement, sentence case, final period allowed ("Get paid upfront.", "Make the busy season count."). Instrument Serif italic 40 px.

**Text**: one or two paragraphs, each at most 3 lines at 440 px and 14 px (about 170 to 200 characters). Paragraph 1: the situation and the concrete thing to do with Regulars (name the mechanism: sign-up QR at the table, Wallet membership, auto-refill). Paragraph 2 (optional): the result for the client, may open with a short bold lead. Speak to the owner as "you", call their customers "guests".

**Reply line**: "Questions? Just reply to this email." or, when the action needs HC, "Questions, or want help setting it up? Just reply to this email."

**Preheader**: one line under 90 characters, the promise of the mail.

**Subject**: short, calm, specific, no emoji, no exclamation. Suggest 2 options.

## Voice

Calm, direct, warm, confident. Short sentences. No exclamation marks, no hype words, no discount or sales words, no "we are excited". One idea per mail. English.

Approved examples:
- Prepaid (23 Oct 2026): title "Get paid upfront."; text "Give your most committed guests an easy next step. Prepaid lets them pay upfront for a bundle, such as 5 or 10 coffees at a better rate, directly in Apple or Google Wallet." then "**The best? Auto-refill.** When the card runs out, it can refill automatically. More repeat purchases, no extra work for your team."; button "See how prepaid works →" to getregulars.com/platform/prepaid.
- Busy season (5 Nov 2026, after Alexander's feedback): subject "More guests this season. Know them."; preheader "Every new guest this season can become a guest you know."; title "Make the busy season count."; text "The festive season brings in guests you have not met yet. A sign-up QR at the table or the counter lets them join your membership in seconds, while your team keeps serving." then "Every member you add now is a guest relationship you can build on all year."; button "Get your sign-up QR →" to mailto:hc@getregulars.com.

## How to build it

1. Copy the template below exactly and replace only [[TITLE]], [[TEXT_1]], [[TEXT_2]] (delete the whole second paragraph block if unused), [[BUTTON_SRC]], [[BUTTON_ALT]], [[BUTTON_HREF]], [[BUTTON_W]] (delete the whole button block if there is no clear action), [[PREHEADER]], [[HERO_SRC]], [[HERO_ALT]] and the page title.
2. Hero: crop to 2:1 around the subject, export JPG 960 x 520, quality about 88, with Pillow. Shown at 480 x 260, rounded 24 px. If the photo is as dark as the mail (a dashboard screenshot), add `border:1px solid #242424;` to the hero's wrapping div so it reads as a card; photos do not need it.
3. Button image: PNG at 2x with Pillow using Inter Medium (fc-match "Inter:medium"): text 11 px, letter-spacing 0.5 px, arrow 12 px, padding 24 px sides and 14 px top and bottom, pill fully rounded, background #FAF9F6, text #0F0F0F, render at 3x then downsample to 2x; shown at half its pixel size, height always 41 px, width = png width / 2. Reuse a hosted button when the label is the same: "See how prepaid works" `https://img.mailinblue.com/3836384/images/content_library/original/6adb4b1061d48f2c837f78cf.png` (203 wide); "Get your sign-up QR" `https://img.mailinblue.com/3836384/images/content_library/original/6aec7a4bf818fe7a6e34073d.png` (186 wide). Light buttons must be images: Gmail on iPhone inverts HTML buttons.
4. Fixed assets: logo `https://img.playbook.com/o26f6RyvKch88MHWADPBd6NVEs0fck67ZJqza4zRHk0/Z3M6Ly9wbGF5Ym9v/ay1hc3NldHMtcHVi/bGljL2UyMTYzZTU3/LTNjODItNGNkYS04/NTg2LWYwMzdhNTcw/ZDBjNw`; HC face `https://img.mailinblue.com/3836384/images/content_library/original/6adb4b1061d48f2c837f78d0.jpg` (shown 62 x 62).
5. Keep the dark mode recipe (in the template): color-scheme meta tags, the two u + .body rules, gmail-screen and gmail-difference spans around every text, linear-gradient on every dark table and cell. New text must also be wrapped in the two spans.
6. Local preview with Playwright (640 px viewport, 2x, full page), swapping images the sandbox cannot load (img.playbook.com is blocked) for local files; check title lines, each paragraph at most 3 lines, button and face visible. Publish the preview copy as the artifact for the team; never send it to Brevo.

## Putting it in Brevo

1. Host new images in Brevo's media library through Maia's Chrome (ask which browser if two are connected; it has been "Browser 1"): open `https://app.brevo.com/content-hub`, `find` "hidden file input for uploading files", `file_upload` with files copied to `/mnt/user-data/uploads/`, read the URLs from the page (`img.mailinblue.com/3836384/images/content_library/original/...`).
2. Create the draft with `email_campaign_management_create_email_campaign`: sender id 3 ("HC from Regulars"), replyTo hc@getregulars.com, recipients list 30, tag the topic, subject, previewText, htmlContent with hosted URLs. Never schedule or send.
3. To change an existing draft: subject, preview and name with `email_campaign_management_update_email_campaign`; the HTML through `https://app.brevo.com/editor/classic/html/<id>` in Chrome, editing the `<textarea>` value with `javascript_tool` (native value setter plus input and change events), then "Guardar y salir". Confirm with `email_campaign_management_get_email_campaign`.
4. Report the campaign id and tell Maia to send herself a test from "Vista previa y prueba" on Gmail iPhone in dark mode. Brevo's preview zooms about 2.5x, so judge sharpness in a real inbox.

List facts (Nov 2026): list 30 has 319 contacts, 43 blacklisted (38 hard bounces and 5 unsubscribes from the Workfeed mail, 21 at theburgerconcept.com); 276 recipients is correct. Do not tick "Don't send to unengaged contacts". Only one newsletter per week to this list.

## Deliverables to Maia

- the two questions answered (what the reader does next, why it is valuable) in one short paragraph
- the artifact (preview copy) and `<topic>-preview.png`
- the 2 subject options, the preheader and the Brevo campaign id

Never send or schedule the mail; Maia and Alexander approve first.

## Template

```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="color-scheme" content="dark">
<meta name="supported-color-schemes" content="dark">
<title>Regulars · [[TITLE]]</title>
<style type="text/css">
@import url('https://fonts.googleapis.com/css2?family=Google+Sans+Flex:wght@300;400;500;600&family=Instrument+Serif:ital@0;1&display=swap');
:root { color-scheme: dark; supported-color-schemes: dark; }
u + .body .gmail-screen { background: #000000; mix-blend-mode: screen; }
u + .body .gmail-difference { background: #000000; mix-blend-mode: difference; }
html, body { margin: 0 !important; padding: 0 !important; width: 100% !important; background: #0F0F0F !important; }
body, table, td, p, a { font-family: 'Google Sans Flex', 'Helvetica Neue', Arial, sans-serif; }
table { border-collapse: collapse !important; border-spacing: 0 !important; }
img { border: 0; outline: none; text-decoration: none; -ms-interpolation-mode: bicubic; }
a { text-decoration: none; }
.regulars-heading { font-family: 'Instrument Serif', Georgia, 'Times New Roman', serif !important; font-style: italic !important; font-weight: 400 !important; }
@media only screen and (max-width: 520px) {
.outer-padding { padding-left: 20px !important; padding-right: 20px !important; }
.regulars-container { width: 100% !important; max-width: 480px !important; }
.regulars-heading { font-size: 36px !important; line-height: 1.06 !important; }
.hero-image { height: 230px !important; }
}
</style>
<!--[if mso]>
<style type="text/css">
body, table, td, p, a { font-family: Arial, Helvetica, sans-serif !important; }
.regulars-heading { font-family: Georgia, 'Times New Roman', serif !important; font-style: italic !important; }
</style>
<![endif]-->
</head>
<body class="body" style="margin:0; padding:0; width:100%; background-color:#0F0F0F; background-image:linear-gradient(#0F0F0F,#0F0F0F); -webkit-text-size-adjust:100%; -ms-text-size-adjust:100%;">
<!-- Preheader -->
<div style="display:none; max-height:0; overflow:hidden; opacity:0; color:transparent; font-size:1px; line-height:1px;">
[[PREHEADER]]
</div>
<!-- Background -->
<table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" bgcolor="#0F0F0F" style="width:100%; background-color:#0F0F0F; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<tr>
<td align="center" class="outer-padding" style="padding:40px 24px 48px; background-color:#0F0F0F; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<!-- Main container -->
<table role="presentation" width="480" cellpadding="0" cellspacing="0" border="0" bgcolor="#0F0F0F" class="regulars-container" style="width:100%; max-width:480px; background-color:#0F0F0F; background-image:linear-gradient(#0F0F0F,#0F0F0F); font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; color:#FAF9F6;">
<!-- Logo -->
<tr>
<td style="padding:0 0 48px; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<img src="https://img.playbook.com/o26f6RyvKch88MHWADPBd6NVEs0fck67ZJqza4zRHk0/Z3M6Ly9wbGF5Ym9v/ay1hc3NldHMtcHVi/bGljL2UyMTYzZTU3/LTNjODItNGNkYS04/NTg2LWYwMzdhNTcw/ZDBjNw" alt="Regulars" width="72" style="display:block; width:72px; height:auto;">
</td>
</tr>
<!-- Hero image -->
<tr>
<td style="padding:0 0 38px; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<div style="border-radius:24px; overflow:hidden; background-color:#0F0F0F; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<img src="[[HERO_SRC]]" alt="[[HERO_ALT]]" width="480" class="hero-image" style="display:block; width:100%; max-width:480px; height:260px; object-fit:cover; object-position:center; border-radius:24px;">
</div>
</td>
</tr>
<!-- Content -->
<tr>
<td style="background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<!-- Title (statement, no eyebrow) -->
<h1 class="regulars-heading" style="margin:0 0 24px; padding:0; max-width:440px; font-family:'Instrument Serif',Georgia,'Times New Roman',serif; font-size:40px; line-height:1.05; font-weight:400; font-style:italic; letter-spacing:-0.4px; color:#FAF9F6;">
<span class="gmail-screen"><span class="gmail-difference">[[TITLE]]</span></span>
</h1>
<!-- Paragraph 1 (max 3 lines) -->
<p style="margin:0 0 18px; padding:0; max-width:440px; font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; font-size:14px; line-height:1.75; color:#F0F0F0; font-weight:300;">
<span class="gmail-screen"><span class="gmail-difference">[[TEXT_1]]</span></span>
</p>
<!-- Paragraph 2 (optional, max 3 lines; delete this block if unused; a bold lead is <strong style="font-weight:600; color:#FAF9F6;">...</strong>) -->
<p style="margin:0 0 18px; padding:0; max-width:440px; font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; font-size:14px; line-height:1.75; color:#F0F0F0; font-weight:300;">
<span class="gmail-screen"><span class="gmail-difference">[[TEXT_2]]</span></span>
</p>
<!-- Button (image, per dark mode rule; delete this block if there is no clear action) -->
<p style="margin:10px 0 24px; padding:0;">
<a href="[[BUTTON_HREF]]" target="_blank" style="display:inline-block; text-decoration:none;"><img src="[[BUTTON_SRC]]" alt="[[BUTTON_ALT]]" width="[[BUTTON_W]]" height="41" style="display:block; width:[[BUTTON_W]]px; height:41px; border:0;"></a>
</p>
<!-- Reply prompt -->
<p style="margin:0; padding:0; max-width:440px; font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; font-size:14px; line-height:1.75; color:#F0F0F0; font-weight:300;">
<span class="gmail-screen"><span class="gmail-difference">Questions? Just reply to this email.</span></span>
</p>
</td>
</tr>
<!-- Signature -->
<tr>
<td style="padding-top:24px; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<table role="presentation" cellpadding="0" cellspacing="0" border="0" bgcolor="#0F0F0F" style="background-color:#0F0F0F; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<tr>
<td width="62" valign="top" style="background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<img src="https://img.mailinblue.com/3836384/images/content_library/original/6adb4b1061d48f2c837f78d0.jpg" alt="Hans Christian Angel" width="62" height="62" style="display:block; width:62px; height:62px; border-radius:16px;">
</td>
<td valign="top" style="padding-left:18px; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<p style="margin:0; padding:0; font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; font-size:13px; line-height:1.4; color:#FAF9F6; font-weight:500;">
<span class="gmail-screen"><span class="gmail-difference">Hans Christian Angel</span></span>
</p>
<p style="margin:7px 0 0; padding:0; font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; font-size:12px; line-height:1.7; color:#8D8D8D; font-weight:300;">
<a href="mailto:hc@getregulars.com" style="color:#8D8D8D; text-decoration:none;"><span class="gmail-screen"><span class="gmail-difference">hc@getregulars.com</span></span></a>
<br>
<a href="tel:+4523416465" style="color:#8D8D8D; text-decoration:none;"><span class="gmail-screen"><span class="gmail-difference">+45 23 41 64 65</span></span></a>
</p>
</td>
</tr>
</table>
</td>
</tr>
<!-- Socials -->
<tr>
<td style="padding-top:36px; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0" bgcolor="#0F0F0F" style="width:100%; border-top:1px solid #242424; background-color:#0F0F0F; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<tr>
<td style="padding-top:20px; font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; font-size:11px; line-height:1.6; letter-spacing:0.2px; color:#FAF9F6; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<a href="https://www.instagram.com/getregulars/" target="_blank" style="color:#FAF9F6; text-decoration:none;"><span class="gmail-screen"><span class="gmail-difference">Instagram</span></span></a>
<span class="gmail-screen"><span class="gmail-difference">     </span></span>
<a href="https://www.linkedin.com/company/getregulars/" target="_blank" style="color:#FAF9F6; text-decoration:none;"><span class="gmail-screen"><span class="gmail-difference">LinkedIn</span></span></a>
<span class="gmail-screen"><span class="gmail-difference">     </span></span>
<a href="https://www.getregulars.com/" target="_blank" style="color:#FAF9F6; text-decoration:none;"><span class="gmail-screen"><span class="gmail-difference">Website</span></span></a>
</td>
</tr>
</table>
</td>
</tr>
<!-- Footer -->
<tr>
<td style="padding-top:20px; font-family:'Google Sans Flex','Helvetica Neue',Arial,sans-serif; font-size:11px; line-height:1.7; color:#8D8D8D; font-weight:300; background-image:linear-gradient(#0F0F0F,#0F0F0F);">
<span class="gmail-screen"><span class="gmail-difference">Memberships in Apple &amp; Google Wallet. Built for Modern Hospitality.</span></span>
<br><br>
<a href="{{ unsubscribe }}" style="color:#8D8D8D; text-decoration:none;"><span class="gmail-screen"><span class="gmail-difference">Unsubscribe</span></span></a>
<span style="color:#8D8D8D;"><span class="gmail-screen"><span class="gmail-difference"> · </span></span></span>
<a href="https://maps.app.goo.gl/NorLv3Y36BtJ5ceP8" target="_blank" style="color:#8D8D8D; text-decoration:none;"><span class="gmail-screen"><span class="gmail-difference">Aarhus, Denmark</span></span></a>
</td>
</tr>
</table>
<!-- /Main container -->
</td>
</tr>
</table>
</body>
</html>
```