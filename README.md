# Executive Dashboard — QuickBooks Report-Pack Analyzer

Drop in a **QuickBooks report-pack PDF** (or Excel export) for a distribution
business and get an instant, interactive **executive dashboard** — Sales, Products,
Inventory, and Receivables — with KPIs, charts, drill-downs, Excel/PDF export, and a
grounded analyst chat. Entirely client-side; no server, no build step.

> **Live demo:** https://quickbooks-executive-dashboard.vercel.app
>
> This public demo ships with a **fictional sample company ("Demo Gummies Co")** so it
> can be shared safely. Upload your own QuickBooks report pack to analyze real data —
> everything stays in your browser.

---

## What it does

Finance teams often live inside static QuickBooks PDFs. This tool parses a report
pack (Sales by Customer, Sales Detail, Inventory Valuation/Movement, A/R & A/P aging,
P&L, Balance Sheet, Cash Flow) into one navigable dashboard:

- **Sales** — by customer, by SKU, trend, and line-level detail.
- **Products** — per-SKU profile: units moved, on-hand, average cost, value.
- **Inventory** — valuation and movement history.
- **Receivables** — aging buckets, per-customer and per-invoice detail.
- **KPIs & charts** — computed from the parsed data, not hardcoded.

## Key features

- **Real parser** — extracts text from the PDF with pdf.js and detects QuickBooks
  report sections; reads `.xlsx` exports too.
- **Real computation** — net sales, COGS, gross margin, aging, inventory-at-date are
  all derived from the imported data.
- **Filters** — period / year / quarter / month / SKU / customer / custom date range.
- **Exports** — styled **Excel** (ExcelJS) and **PDF** (jsPDF + autotable).
- **Analyst chat** — a grounded assistant with tool-calling over the actual figures
  (`get_metrics`, `list_invoice_lines`, `get_open_invoices`, `get_inventory`, …), plus
  a **deterministic offline analyst** fallback that returns exact computed numbers
  when no host model is available.
- **Share** — export a standalone snapshot HTML with the current data embedded.
- **Persistence** — imported reports are kept in the browser between visits.

## Use it

1. Open the live demo (or `index.html` locally).
2. It loads with the **Demo Gummies Co** sample so you can explore immediately.
3. Click **Import** and drop your own QuickBooks report-pack PDF/Excel to analyze
   real data. Nothing leaves your browser.

## Tech

Single self-contained HTML file. Vanilla JS, no framework, no build step. CDN
libraries: Chart.js, pdf.js, SheetJS (xlsx), ExcelJS, jsPDF (+ autotable).

**AI note:** the "AI analyst" chat uses the host model runtime when the page runs
inside a compatible host; on a plain static host (e.g. Vercel) it automatically falls
back to the **built-in offline analyst**, which answers from the computed figures.
Both are grounded — the assistant does not invent numbers.

## Privacy & security

- The public demo contains **no real company data** — the company, customers,
  investors, SKUs and financials are all fictional samples.
- No API keys are used or stored.
- For real use, keep any copy that has your actual books embedded **private** — do not
  publish it. On a shared host without access control, treat anything you deploy as
  public.

## Deploy

Static site — deploys as-is to Vercel, Netlify, GitHub Pages, or any static host.
No environment variables, no server functions required.

## License

See [LICENSE](LICENSE). Provided for review and evaluation.
