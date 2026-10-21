# Last Ember

Website for Last Ember, a late-night burger bar in Belgrade (open Tue to Sun, 20:00 to 03:00).
Plain HTML, CSS and JavaScript. No build step, no frameworks, no server needed.

## Folder structure

```
last-ember/
├── index.html            page structure and all sections
├── css/
│   └── style.css         all styles (colours and fonts are at the top, in :root)
├── js/
│   ├── translations.js   every piece of text, in English and Serbian
│   └── app.js            menu, cart, booking, forms, language switch, scroll animation
└── assets/
    └── favicon.svg       browser tab icon
```

## How to run it

Open `index.html` in a browser. That's it.

If you want a local server (useful for testing on a phone in the same Wi-Fi):

```
npx serve .
```
or
```
python3 -m http.server 8000
```

## How to edit common things

| What | Where |
|---|---|
| Any text, in either language | `js/translations.js`. Each entry is `["English", "Srpski"]`. |
| Dishes, prices, allergens, extras | `js/app.js`, the `MENU`, `EXTRAS` and `COMBOS` lists |
| Weekly specials | `js/app.js`, the `SPECIALS` list (0 = Sunday, 1 = Monday...) |
| FAQ and legal pages | `js/app.js`, the `FAQ` and `LEGAL` lists |
| Promo codes | `js/app.js`, `PROMOS` (now `EMBER10`, `NIGHT15`, `FIRST20`) |
| Delivery neighbourhoods | `js/app.js`, `IN_ZONE` and `NEAR` |
| Opening hours logic | `js/app.js`, `isOpenAt()` and `nextOpening()` |
| Colours and fonts | `css/style.css`, the `:root` block at the top |
| Address, phone, email | `index.html` (contact section and footer) and `js/translations.js` |

The default language is English. The EN / SR button switches everything and the choice is remembered in the browser.

## What works and what is simulated

Works fully in the browser:
- Scroll-built burger hero (static version for people with reduced motion turned on)
- Menu with categories, search, filters, dish details, allergens and extras
- Cart: quantities, extras, pickup or delivery, delivery fee (free over 2,000 RSD), promo codes, tip, time slots and pre-ordering when closed, saved between visits
- Order confirmation styled as a kitchen ticket, with status steps
- Table booking (Mondays blocked), loyalty club sign-up, contact form, newsletter
- Delivery area check, live open/closed status, today highlighted in hours and specials
- Gallery with full-screen view, cookie notice, English and Serbian

Simulated (there is no backend):
- Orders, bookings, messages and sign-ups are not sent anywhere. Each form has a
  `submit` or `click` handler in `js/app.js` that currently shows a success message.
  To make them real, send the data from those handlers to your own API, a form
  service (Formspree, Netlify Forms, Basin) or an ordering system.

## Putting it online for free

- **Netlify**: drag the whole `last-ember` folder onto https://app.netlify.com/drop
- **GitHub Pages**: push the folder to a repository, then Settings → Pages → deploy from the main branch
- **Vercel** or **Cloudflare Pages**: import the folder, no build command, output directory `.`

## Notes

- Fonts load from Google Fonts (Big Shoulders Display, Instrument Sans, IBM Plex Mono). Without internet the page falls back to system fonts.
- The brand, people, reviews and press mentions are fictional placeholders. Replace them before using the site for a real business.
