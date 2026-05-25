# Agent Notes

This repo is a static single-page restaurant bill splitter. The whole app lives in `index.html`; there is no build step or framework.

## App Shape

- `index.html` contains HTML, CSS, and JavaScript.
- `assets/banks/` contains local bank/app logo assets used by the payment dropdown.
- `package.json` only provides a local static server with `npm run dev`.
- `README.md` explains usage, deployment, and current user-facing behavior.
- Export image depends on the CDN-loaded `html2canvas` script.
- Current app version is `v1.0.3`.

## Core Behaviors

- Friends are stored in the global `friends` array.
- Menu items are stored in the global `items` array.
- Item names can contain line breaks and should remain readable in the input table and receipt.
- Item price fields sanitize to numeric decimal input before parsing.
- If no people are selected for an item, that item is split by everyone.
- VAT and service charge are applied per person from their item subtotal.
- VAT is calculated on `subtotal + service`.
- Payment details are optional and only shown when at least one payment field has a value. Bank/app selection uses a compact custom dropdown with local logo image assets and abbreviations such as `SCB` shown before the full name to reduce selection mistakes.
- Some downloaded bank SVGs are intentionally cropped via `viewBox`/dimension edits to show icon-only marks in the dropdown: `bay.svg`, `bbl.svg`, `scb.svg`, `kbank.svg`, and `gsb.svg`.

## Receipt Output

The output intentionally has two distinct sections:

- **Restaurant-style receipt**: itemized bill for checking. It shows item name, shared-by, original item amount, subtotal, service, VAT, and grand total.
- **Payment split cards**: screenshot/share section. Each card should stay compact and show only name plus final amount. Payment details appear below the cards.

When an item is shared by every current friend, the itemized receipt should show `All` in the shared-by column instead of listing every name.

## Design Constraints

- Keep the receipt compact and readable on mobile.
- Numeric amounts should use tabular, easy-to-read number styling.
- Keep `.item-shared` left-aligned even when table action cells are right-aligned.
- Payment cards must handle long names and large amounts without overflowing.
- Itemized bill rows use inline shared-by text and light row guides for scanning. Avoid adding duplicate dotted/dashed lines.
- Keep receipt section dividers separated from row guide lines. Item rows are wrapped in `.thermal-items`, charges are in `.thermal-breakdown.thermal-section`, and the grand total is in `.thermal-total-section.thermal-section` so only one visual line appears between sections.
- Payment cards use a compact two-column grid: flexible name text plus a right-aligned non-wrapping amount. Preserve `minmax(0, 1fr)` and long-text wrapping on names when adjusting card layout.
- Preserve the vintage receipt visual language unless the user explicitly asks for a larger redesign.

## Verification

Useful quick checks after editing:

```bash
node -e "const fs=require('fs'); const html=fs.readFileSync('index.html','utf8'); const js=html.match(/<script>([\\s\\S]*)<\\/script>/)[1]; new Function(js); console.log('embedded script syntax ok');"
```

For layout work, run locally:

```bash
npm run dev
```

Then open `http://localhost:3000`.
