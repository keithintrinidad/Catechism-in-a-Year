# Catechism in a Year – PWA

**▶ Open the app: [keithintrinidad.github.io/Catechism-in-one-Year](https://keithintrinidad.github.io/Catechism-in-one-Year/)**. Use it in the browser, or install it on your phone (see [Installing on a phone](#installing-on-a-phone)).

A 365-day reading plan through the Catechism of the Catholic Church. Each day gives the paragraphs to read, with a link to that section of the Vatican's online text; a short study note; a word from Hebrew, Greek, Latin or Aramaic; the key Scripture passages, each linked to the YouVersion Bible app; a note on how Catholic teaching compares with Protestant and Anglican views; and a question for reflection. You can mark each day as read, keep your own notes, and read them all back in a journal. Every 30th day is a review day. It works offline once installed, and runs entirely in the browser as static files: no build step, no server code.

## About this app

This app was built by **Claude**, an AI model created by **Anthropic**, under the guidance of **Keith Francis** ([keithintrinidad](https://github.com/keithintrinidad)).

- **Original content.** The reading plan, its order, and all 365 days of study notes were written by Claude, drawing on Keith Francis's conversations with it about the Catechism, Scripture and its Hebrew and Greek background, and his journey through OCIA.
- **The Catechism text.** No text of the Catechism is reproduced. The app gives paragraph numbers and links to the text published on the Vatican's website.
- **Design and build.** Keith Francis directed the app's content, features, and packaging through conversation with Claude, but did not write the code directly.

It is a companion to three other apps, made the same way:

| App | Open the app | Source code |
|---|---|---|
| Rosary Helper | [keithintrinidad.github.io/Rosary-Helper](https://keithintrinidad.github.io/Rosary-Helper/) | [github.com/keithintrinidad/Rosary-Helper](https://github.com/keithintrinidad/Rosary-Helper) |
| Prayers for Catholics | [keithintrinidad.github.io/Catholic-Prayers](https://keithintrinidad.github.io/Catholic-Prayers/) | [github.com/keithintrinidad/Catholic-Prayers](https://github.com/keithintrinidad/Catholic-Prayers) |
| Bread of the Presence | [keithintrinidad.github.io/Bread-of-the-Presence](https://keithintrinidad.github.io/Bread-of-the-Presence/) | [github.com/keithintrinidad/Bread-of-the-Presence](https://github.com/keithintrinidad/Bread-of-the-Presence) |

## What's in the package

| File | Purpose |
|---|---|
| `index.html` | The app (Today, Plan, Journal and Settings tabs, light/dark, About page with credits and licence) |
| `data/plan.js` | The 365-day plan: titles, paragraph ranges, study notes, Scripture references and Vatican page links |
| `app.webmanifest` | Name, colours, icons and the app's identity used when installed |
| `sw.js` | Service worker: caches everything so the app works offline |
| `icons/` | App icons (192, 512, maskable 512, Apple touch, favicon) |
| `fonts/` | EB Garamond (Latin and Greek) and Frank Ruhl Libre (Hebrew), self-hosted (SIL OFL licences included) |
| `LICENSE.md` | The terms this project is shared under (see below) |

## Features

- **Today.** Opens the next day you haven't read, or, if you set a start date, the day scheduled for today (and tells you how many earlier days are unread).
- **Catechism links.** Each day links to the page (or pages) of the Vatican's online Catechism that contain its paragraphs. In Settings you can switch to *I'll read from my printed copy*, which hides the links.
- **Scripture links.** References open in the YouVersion Bible app if it is installed, or on bible.com, in the translation chosen in Settings (NRSV-CI by default). You can switch translations inside YouVersion at any time.
- **Mark as read and My notes.** Notes save automatically as you type.
- **Plan.** Progress bar and the full plan by phase, with ticks for days read and a ✎ for days with notes.
- **Journal.** All your notes in one place, searchable, and exportable as text.
- **Calendar file.** Settings can create an .ics file starting on any date, for Google Calendar, Apple Calendar or Outlook.
- **Backup and restore.** Download your progress and notes as a file, and restore them on another device.

## Deploying

Upload the folder contents as-is to any static host that serves **HTTPS** (service workers require it). All paths are relative, so it works at a domain root or in a subfolder.

- **GitHub Pages:** create the repository `Catechism-in-a-Year`, push the files to the repo root, then Settings → Pages → deploy from the `main` branch, root folder. The app will be live at [keithintrinidad.github.io/Catechism-in-one-Year](https://keithintrinidad.github.io/Catechism-in-one-Year/).
- **Netlify:** drag the unzipped folder onto app.netlify.com/drop.
- **Cloudflare Pages:** Create project → Direct upload → select the folder.

## Installing on a phone

- **Android (Chrome):** open the link → menu → *Install app* / *Add to Home screen*.
- **iPhone (Safari):** open the link → Share → *Add to Home Screen*.

After the first visit the app works fully offline. The Catechism and Bible links need an internet connection.

## Your entries

Progress, notes and settings are stored on each device only, in the browser's local storage. Nothing is sent anywhere. Use *Download a backup* in Settings to keep a copy or move to a new phone, and *Copy all as text* in the Journal to keep your notes elsewhere.

## The app's identity

`app.webmanifest` sets `"id": "catechism-in-a-year-app"`. Browsers resolve the id against the site's domain, so every app on keithintrinidad.github.io needs its own id; a relative id such as `"./"` would make all of them look like one app, and Android would say it is already installed. Don't change this id once people have installed the app, or their copy will be treated as a different app.

## Updating the app

1. Edit `index.html` for the app itself, or `data/plan.js` for the plan and notes.
2. In `sw.js`, change `VERSION` (e.g. `ccc-year-v3` → `ccc-year-v4`). Do this every release or installed copies may keep the old files.
3. Upload the changed files. Users get the update the next time they open the app while online.

## Testing locally

Service workers need `https://` or `localhost`, so opening the file directly won't register it:

```
python3 -m http.server 8080
```

then visit http://localhost:8080.

## License & authorship

This app is free to share and adapt, but never to sell, and any version made from it must stay free too. It is licensed under **CC BY-NC-SA 4.0**.

It was built by Claude (Anthropic) under the guidance of **Keith Francis** (keithintrinidad). Any copy or derivative must keep that credit. The same credit and a licence summary are shown inside the app itself, behind the (i) button, for anyone who only ever sees the installed app. The Catechism of the Catholic Church is © Libreria Editrice Vaticana and is only linked to, not reproduced. The fonts carry their own SIL Open Font License. Full terms are in `LICENSE.md`.
