# Bill Splitter

A single-page bill splitting app for restaurant meals. Add friends, menu items, VAT, service charge, and payment details, then export the result as an image, CSV, or print-ready receipt.

Current version: `v1.0.2`

## Features

- Add friends and menu items with quantity and numeric-only price entry.
- Enter long or multi-line item names without losing readability.
- Select who shared each item. If no one is selected, the item is split by everyone.
- Apply VAT and service charge to each person's subtotal.
- Choose payment destination details with a compact bank/app logo dropdown for easier selection.
- Export the split as a PNG image, CSV, or printout.

## Receipt Output

The output is split into two sections:

- **Restaurant-style receipt**: a compact itemized bill with item name, shared-by marker, item amount, and charges breakdown. Items shared by everyone show `All` in the shared-by column.
- **Per-person payment cards**: compact share-friendly cards with each person's name and final amount only, plus payment info below.

The itemized receipt is intended for checking the bill. The payment cards are intended for screenshots and sharing in chat.

## How To Use

1. Enter the restaurant name and date.
2. Add everyone in the **Friends** section.
3. Set VAT and service charge percentages.
4. Add payment details if you want them shown in the share output. Use the bank/app logo dropdown to avoid choosing the wrong bank.
5. Add each menu item, selecting the people who shared it. Item names can wrap to new lines, and price fields accept numbers only. Leave all checkboxes empty to split that item by everyone.
6. Use **Export as Image**, **Export CSV**, or **Print** from the receipt panel.

## Project Structure

```text
.
├── index.html
├── package.json
├── vercel.json
├── .gitignore
└── README.md
```

## Run Locally

Open `index.html` directly in a browser, or run the included local server:

```bash
npm run dev
```

Then visit:

```text
http://localhost:3000
```

## Deploy To Vercel

This project is a static site with no build step.

1. Push this folder to a GitHub repository.
2. Import the repository in Vercel.
3. Use these settings:
   - Framework Preset: `Other`
   - Build Command: leave empty
   - Output Directory: `.`

Vercel will serve `index.html` from the project root.
