# Phase 2 — S1P1 full-flow verification

Use `V17_S1P1_MSS_Flow.xlsx` **locally**; do not commit proprietary MSS data into this public repository.

## Features added

- Toggle a read-only visual Flow View of the **existing order**, showing indentation and heuristic flow-control markers.
- Search and filter by `Command` and `ASC` columns where present.
- Identify spec/parameter columns by header name instead of Excel letter.
- Prevent direct inline/batch edits to `Seq. No.`, `Test_NO`, and `Test_Item`; prevent edits to detected flow-control rows.
- Preserve asterisk-only no-spec placeholders in bulk edits.

## Acceptance checklist

1. Load the complete MSS; verify row count and headers against the original Excel file.
2. Toggle Flow View and Excel Grid; no row or value should change solely from toggling.
3. Check representative `for`/brace/control rows and indent depth against original Excel; these are **hints**, not a parsed hierarchy.
4. Search `Command` and `ASC` values, then clear filters; all original rows must return in the same order.
5. Bulk-edit a normal spec field on two selected non-control rows; confirm change preview and export have exactly these two edits.
6. Verify editing `Seq. No.`, `Test_NO`, `Test_Item` or a detected control row is blocked.
7. Undo and redo the edit; verify all affected values, especially `*` or `***`, are correct.
8. Export a new copy, re-open it in Excel, and compare all unedited data and worksheet structure against the original.
9. Run existing strict PE/TE MSS comparison if an appropriate pair of workbooks is available.
10. Check performance and browsing on ~1,880 rows. The grid intentionally pages results (100 per page).

## Known limitations

- This is a prototype: Excel workbook formatting, formulas and advanced objects **are not guaranteed to round-trip**.
- Flow markers are identified heuristically from text, not executed or parsed Test Programs.
- Header-based role classification may need adaptation to product-specific MSS formats.
- Edit history is held in memory during this browser session; no persistent autosave.
- Sequence-changing operations (row insertion/deletion/sorting/reordering) remain intentionally unsupported.
- `Command`/`ASC` are informational MSS metadata; they do not prove actual Pattern execution.
