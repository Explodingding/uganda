# Uganda Sustainable Resources — Research Portal

Evidence-based web portal supporting comparative research: **Lommel (Belgium) silica industry** as a case study for **balanced resource development in Uganda** (glass sand, development minerals, reclamation, and renewable co-location).

- **Framework report (PDF):** [`public/documents/Lommel_Uganda_Sustainable_Resource_Management_Report.pdf`](public/documents/Lommel_Uganda_Sustainable_Resource_Management_Report.pdf)
- **Live site:** deploy to [Netlify](https://www.netlify.com/) from this repository
- **GitHub:** [github.com/Explodingding/uganda](https://github.com/Explodingding/uganda)

## Local development

Requirements: **Node.js 22+** (see `.nvmrc`).

```bash
npm install
npm run dev
```

Open `http://localhost:4321`.

## Deploy on Netlify (automatic from GitHub)

1. Push this folder to `Explodingding/uganda` on GitHub (`main` branch).
2. In Netlify: **Add new site** → **Import an existing project** → GitHub → select `uganda`.
3. Netlify reads [`netlify.toml`](netlify.toml):
   - Build: `npm run build`
   - Publish: `dist`
   - Node: `22`
4. Save. Every push to `main` rebuilds the site.

Update `site` in `astro.config.mjs` after Netlify assigns your URL (or custom domain).

## Adding research data (no hallucinations)

| File | Purpose |
|------|---------|
| `src/data/bibliography.json` | Add every new reference **before** citing it |
| `src/data/resources.json` | Resource catalog (silica, limestone, salt, …) |
| `src/data/fact-checks.json` | Corrections between draft report and verified sources |
| `public/documents/` | PDFs and annexes |

Each catalog entry must list `source_ids` that exist in `bibliography.json`.

## Tech stack

- [Astro](https://astro.build/) static site generator
- Static output suitable for Netlify CDN
- No server-side database — content travels with the repo for academic reproducibility

## Fact-check note (important)

The framework PDF groups **Kristal Solar Park** with quarry-lake floating solar. Verified sources distinguish:

- **Kristal Solar Park** — 99.5 MW **ground-mounted** PV, Lommel ([Stad Lommel](https://www.lommel.be/kristal-solar-park))
- **Floating PV** — 7 MWp on Sibelco’s **De Schans** quarry, Mol/Dessel ([floatingpv.be](https://www.floatingpv.be/en/))

The portal documents this in `/lommel` and `src/data/fact-checks.json`.

## License

Academic / research use — confirm rights for third-party PDFs and government reports before redistribution.
