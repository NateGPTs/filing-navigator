# Filing Navigator

A demo web app that helps judges and court staff navigate long Indiana court filings. Built as a class project for AI For Impact.

Open a text-based PDF and the app shows the PDF on the right and a sidebar on the left with:

- **Contents:** an auto-generated table of contents from the filing's headings, plus the start of each exhibit or attachment.
- **Key info:** case number (decoded), court, judge, parties, attorneys, important dates, and a plain-English summary of what the filing asks the court to do.

Every item links to the PDF page it came from, so a person can check it. The tool highlights and links; it doesn't make decisions.

## How it works

- **Pattern matching (regular expressions)** handles predictable formats: Indiana case numbers, standard section headings, exhibit cover pages, attorney numbers, and dates.
- **Claude** handles two fuzzy tasks only: confirming non-standard headings and summarizing "the ask." Claude must quote the wording it relied on, and the app checks that quote against the extracted text.
- **PDF.js** renders the PDF and extracts text page by page. **jsPDF** generates the built-in fictional sample filing.

## Running it

It's a single file, `index.html`. Open it in a browser or serve it with any static host (for example GitHub Pages).

**Note on the Claude features:** they use the claude.ai artifact runtime (`window.claude.use("sample")`), which exists only when the page runs as a published artifact on claude.ai. Anywhere else, those two features show "unavailable" and everything else still works. To run them elsewhere, add a small server that calls the Anthropic API. Never put an API key in front-end code.

## Status

- [x] Upload, table of contents, exhibits, key info panel
- [ ] Citations panel (cases, Indiana Code, court rules, record references)
- [ ] Color-coded highlighting with legend and toggles

## Disclaimer

Student demo, not legal advice. The sample filing is fictional.
