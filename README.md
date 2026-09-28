# Code Stats

A single-file web UI for project statistics. Point it at a project folder and it
scans the entire tree **in your browser** (File System Access API) and renders a
dashboard — no server, no install, nothing leaves your machine.

## Use

1. Open `index.html` in **Chrome** or **Edge** (double-click is fine — no server needed).
2. Click **Choose project folder** and pick a project.
3. The scan runs live with a progress line; results render as it completes.
4. **Download report (JSON)** saves the full raw dataset. **Scan another folder** reruns.

## What it reports

- **Tiles**: total files / folders, max depth, total lines / characters / size,
  text vs binary counts, empty files, average & median lines per file, distinct
  extensions, longest path / filename / single line, files touched in the last
  30 days, duplicate-name groups, CRLF vs LF file counts, scan errors.
- **Charts** (top 12 + other, client-side, no libraries): lines by file type,
  files by extension, files by directory depth, lines-per-file distribution.
- **Tables** (click headers to sort): top files by lines, by size, most recently
  modified; top directories by file count and line count; file-type breakdown
  with language names; duplicate name+size groups.

Scan options: skip-list of directory names (`.git`, `node_modules` by default,
with quick-add chips like `dist`, `__pycache__`, `target`) and a max file size
for line counting (default 10 MB).

Binary detection: extension list plus a null-byte sniff of the first 8 KB.
