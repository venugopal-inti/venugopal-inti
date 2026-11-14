# Venugopal Inti | Portfolio

Personal portfolio of **Venugopal Inti**, Desktop Support Engineer and IT Administrator based in Hyderabad, India.

**Live site:** https://venugopal-inti.vercel.app

## About

A single-page website that presents my experience, skills, certifications and feedback from managers. It opens like a laptop powering on (power button, startup checks, boot logo, login), then loads the main site. A recorded or synthesised voice introduction is available in English and Telugu.

## Features

- Liquid glass interface with an aurora background, glossy orbs and a pointer-following highlight
- Fully responsive layout with a bottom tab bar on phones
- Boot sequence with a skip option, shown once per browser tab
- Voice introduction in English and Telugu, with live captions
- Experience, daily runbook, skills, certifications, feedback and sample ServiceNow tickets
- Contact form powered by Formspree
- Respects reduced-motion settings; works without JavaScript for core content

## Tech

Plain HTML, CSS and JavaScript in one file (`index.html`). No build step, no framework.
Fonts: Inter, JetBrains Mono, Noto Sans Telugu (Google Fonts).

## Project structure

```
.
├── index.html          # the whole site
├── photo.jpg           # portrait used on the hero, intro and login screen
├── logos/              # company and issuer logos
│   ├── flipkart.png
│   ├── kotak.png
│   ├── ankura.png
│   ├── lalitha.png
│   ├── inox.png
│   ├── datapro.png
│   ├── google.png      # optional
│   ├── microsoft.png   # optional
│   ├── ibm.png         # optional
│   └── anthropic.png   # optional
├── intro.mp4 / intro.mp3        # optional, English voice introduction
├── intro-te.mp4 / intro-te.mp3  # optional, Telugu voice introduction
├── make_voice.py       # generates the mp3 files
└── Venugopal_Inti_Resume.pdf
```

If a logo file is missing, the site falls back to the company's website icon, then to a letter badge. The common extensions `.png`, `.jpg` and doubled names such as `flipkart.png.png` are all tried.

## Voice introduction

The page looks for media in this order, separately for each language:

1. `intro.mp4` or `intro-te.mp4`: your own video
2. `intro.mp3` or `intro-te.mp3`: your own audio, with the photo animating
3. The browser's built-in voice reading the script (voice quality depends on the device)

To generate the mp3 files:

```bash
pip install edge-tts
python make_voice.py
```

This creates `intro.mp3` (English, `en-IN-PrabhatNeural`) and `intro-te.mp3` (Telugu, `te-IN-MohanNeural`). Upload both next to `index.html`.

## Deploy

**GitHub and Vercel**

1. Upload the files above to the repository root.
2. Vercel redeploys automatically on each commit.
3. After updating, hard refresh (Ctrl + Shift + R) or open in a private window to avoid cached files.

**Custom domain:** add the domain in Vercel under Project Settings > Domains, then create the DNS records Vercel shows (an A record for the apex domain, a CNAME for `www`).

## Editing content

All content sits in the `<script>` block of `index.html`:

| What | Where |
| --- | --- |
| Jobs | `exps` array |
| Daily runbook | `runbook` array |
| Skills and ratings | `skills` and `groups` arrays |
| Certifications | `aiCerts` and `msCerts` arrays |
| Manager feedback | `appr` array |
| Sample tickets | `tickets` array |
| Voice script | `T` object inside the voice introduction block |
| Contact form | `formId` in the Formspree snippet |

The hero statistics (devices managed, tickets resolved) are in the `data-to` attributes of the stat tiles. Update them with figures you can back up.

## Contact

- Email: hello.venu25@gmail.com
- LinkedIn: https://www.linkedin.com/in/venugopal-inti-7567631ab
- Location: Hyderabad, Telangana, India

&copy; Venugopal Inti
