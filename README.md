# 📚 kdp-autopublish

> Automate Amazon KDP (Kindle Direct Publishing) with Playwright — from manuscript to live listing without touching the UI manually.

## Features
- Full 3-step wizard automation: Details → Content → Pricing
- Uploads EPUB/PDF manuscript and cover (PDF full-wrap or JPG/PNG)
- Sets pricing across 10+ Amazon markets
- Scrapes existing catalog to detect already-published books
- Generates PIL covers programmatically (3000×3000px, gradient)
- Builds DOCX from HTML content

## Important Rules (learned from experience)
- ⚠️ **Never assign ISBN** — Amazon provides one free automatically
- ⚠️ **Always trigger Preview** before clicking Next on /content step
- ⚠️ **Never restart mid-task** — KDP IPC state is fragile

## Setup
```bash
pip install playwright pillow python-docx python-dotenv
playwright install chromium
cp .env.example .env
python kdp_publish.py --config book_config.json
```

## .env
```
KDP_COOKIES=./kdp_cookies.json
MANUSCRIPT_PATH=./manuscript.epub
COVER_PATH=./cover.pdf
```

## Book config format
```json
{
  "title": "My Book Title",
  "subtitle": "A subtitle",
  "author": "Author Name",
  "description": "Book description",
  "keywords": ["keyword1", "keyword2"],
  "categories": ["Fiction > Literary"],
  "price_usd": 4.99
}
```

## License
MIT © Sabino Gervasio
