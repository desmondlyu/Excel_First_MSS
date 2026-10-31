# Excel-First MSS Editor

Browser-based, Excel-first NOR Flash MSS editing prototype.

## Scope

- Load .xlsx/.xls workbooks locally in the browser
- Filter and edit existing MSS cells
- Review edits, bulk change selected rows, undo and redo
- Export a modified copy; original file is not overwritten

## Safety status

**Prototype, not production-qualified.** Do not use the exported file as an authoritative MSS without comparing it against the original in Excel and running the existing PE/TE strict comparison process. Excel formatting, formulas, objects and other workbook features may not round-trip perfectly. Macro-enabled files are intentionally excluded.

## Development

Open `index.html` through a local HTTP server (for example `python -m http.server 8000`). The XLSX library is loaded from a CDN and requires network access. No workbook is uploaded to a server by this app.
