# Repository Guidelines

## Project Structure & Module Organization
- `Company/`: Investor relations downloads (monthly updates, quarterly earnings, annual reports). Keep original filenames and add new versions alongside older ones.
- `MOPS/`: Regulatory filings pulled from the MOPS source; follow the existing `YYYYMM_2412_<code>.pdf` naming and update `metadata.json` when adding sources or notes.
- `GoodInfo/`: Research notes or cleaned outputs (e.g., `stage2-cleaning-revenue-report-2412.md`). Add new analyses here instead of mixing with raw documents.
- `README.md`: Lists upstream URLs; update links if sources move.

## Build, Test, and Development Commands
- The repo is primarily data; there is no build pipeline. If you add scripts, prefer self-contained `python` or `bash` with clear invocation examples (e.g., `python scripts/download.py --dest Company/`).
- Avoid commands that mutate files silently; document any generated outputs and paths.

## Coding Style & Naming Conventions
- Preserve source filenames; for new files use lowercase with hyphens for text/markdown (e.g., `q2-2025-notes.md`) and keep PDF names consistent with existing patterns.
- Markdown: use `##`-level headings, short bullet lists, and include source URLs inline.
- JSON (e.g., `MOPS/metadata.json`): two-space indentation, stable key ordering, and concise values (source URL, retrieval date, checksum if available).

## Testing Guidelines
- No automated tests exist. If you add scripts, include a quick check command in the script docstring or header comment (e.g., `# Usage: python scripts/validate_links.py`).
- Validate added files open correctly and, for data transformations, spot-check a few records against the source.

## Commit & Pull Request Guidelines
- Commits should be small, descriptive, and mention the data source and date range (e.g., “Add 2025-03 MOPS filings (AI1, AI3)”). Avoid unrelated bundling.
- In pull requests, include: summary of changes, data origin URLs, and any verification steps performed (e.g., “opened PDFs, compared totals to site”).
- If adding generated artifacts, note the generation command and input sources in the description or a short `notes.md` alongside the output.

## Markdown Consistency
- Keep headings tight (title uses `#`, primary sections `##`), prefer hyphen bullets, and wrap tables with pipes for alignment.
- Use inline code for paths/commands (`Company/`, `GoodInfo/`, `python scripts/...`), and keep language consistent with existing files (English section titles, Chinese content acceptable where source data requires).
