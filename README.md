# CV Optimizer

A single-page app that suggests small-to-medium edits to your CV so it matches a job description. It uses Claude (Opus) through the Anthropic TypeScript SDK, straight from the browser.

## Run it

Open `index.html` in a browser, or serve the folder if your browser blocks module scripts from `file://`:

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Use it

1. Paste your Anthropic API key. It is saved in this browser's localStorage only.
2. Upload your CV as `.docx`. It is remembered in the browser, so you only do this once.
3. Paste the job description (plus optional extra instructions) and click **Suggest changes**.
4. Review the CV on an A4-style page. Text Claude wants to change is highlighted in yellow (a small caret marks where words would be inserted). Each change has a numbered comment in the right margin showing exactly how it would read, and why. **Accept**, **Reject**, or **Edit** to write your own version. Accepted text turns green on the page, your own edits blue. Click a highlight or a comment to jump between them.
5. Click **Download .docx** to get `<your file> - tailored.docx`. The original file is untouched.

## Limits

- Old binary `.doc` files are not supported. In Word, use Save As → Word Document (`.docx`).
- A changed paragraph keeps its paragraph style (bullets, spacing, heading). Unchanged words keep their formatting. New words take the formatting of the words they replace.
- The A4 view is an approximation. Page breaks and fonts can differ slightly from Word, and two-column (table) layouts are shown as a single column.
- Text inside text boxes, and paragraphs containing images or fields, are shown but never edited.
- Your API key is used from the browser (`dangerouslyAllowBrowser`). That is fine for personal local use, but don't host this page publicly with a key in it.
