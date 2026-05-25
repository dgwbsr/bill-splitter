# Bill Splitter

A single-page bill splitting app for restaurant meals. Add friends, menu items, VAT, service charge, and payment details, then export the split as an image, CSV, or print-ready receipt.

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

Open `index.html` directly in a browser, or run a simple local server:

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
# bill-splitter
