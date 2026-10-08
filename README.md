# JellyBean6 — Mobile Phone Shop Website

A catalogue website for a mobile phone retail shop. Enquiry-based: customers browse
phones and contact the shop on **WhatsApp** or by **phone call**. There is no shopping
cart and no payment gateway by design.

Built as a single self-contained `index.html` — no framework, no dependencies, no build step.

## Pages

| Route | Contents |
|---|---|
| `#/` | Hero with *No Cost EMI* / *0% Down Payment*, brand tiles, 8 featured phones, shop highlights |
| `#/products` | All phones with brand + price filters, custom min/max range, sorting |
| `#/product/<id>` | Gallery, colour & storage variants, full specification table, WhatsApp / Call buttons |
| `#/contact` | Address, phone, business hours with a live *Open now* badge, map, WhatsApp CTA |

A floating WhatsApp button is present on every page.

## Features

- 12 sample phones across Samsung, Apple, Xiaomi, Redmi and Vivo, priced in INR
- Selecting a colour or storage variant updates the price, the EMI figure **and** the
  pre-filled WhatsApp message together
- Every WhatsApp link opens with a message naming the exact phone, colour, variant and price
- Phone images are generated as inline SVG, so nothing is broken if no photos are supplied
- Business hours compute *Open now* / *Closed now* from the visitor's local time
- Mobile responsive — verified with no horizontal overflow from 320px upwards

## Running it

Open `index.html` directly in a browser, or serve the folder:

```bash
python -m http.server 8000
# then visit http://127.0.0.1:8000/index.html
```

Serving over HTTP is only needed for the embedded Google Map; everything else works
straight from the file system.

## Customising

Everything a shop owner would change lives at the top of the `<script>` block in `index.html`:

- **`SHOP`** — phone number, address, business hours, Instagram handle, map location.
  Edit it once and the header, footer, contact page and every call/WhatsApp link update together.
- **`PRODUCTS`** — the phone catalogue. Each entry accepts an optional
  `image: "images/phone.png"` to replace the generated SVG illustration with a real photo.
- **`images/`** — logo files (`logo.png` is the full lockup, `logo-mark.png` the icon tile).

## Before going live

The phone number (`+91 98765 43210`) and the store address are **placeholders**.
Replace them in the `SHOP` object before publishing, or enquiries will go nowhere.
