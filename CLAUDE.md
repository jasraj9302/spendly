# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Run the development server (http://localhost:5001)
python app.py

# Install dependencies (use a virtualenv)
pip install -r requirements.txt

# Run tests
pytest

# Run a single test file
pytest tests/test_auth.py

# Run a single test by name
pytest tests/test_auth.py::test_login_success
```

## Architecture

**Spendly** is a Flask web app for personal expense tracking, built incrementally as an educational project. Students implement features step by step; placeholder routes in `app.py` indicate what's coming.

### Stack
- **Backend:** Flask 3.1.3, Jinja2 templates, SQLite (via `database/db.py`)
- **Frontend:** Vanilla HTML/CSS/JS — no build step, no frameworks
- **Testing:** pytest + pytest-flask

### Key files
- `app.py` — all routes; currently renders static pages, placeholders for auth/expense CRUD
- `database/db.py` — database layer stub (students implement this)
- `templates/base.html` — master layout; all pages use `{% extends "base.html" %}` with blocks: `title`, `head`, `content`, `scripts`
- `static/css/style.css` — global styles with CSS custom properties (design tokens: `--ink`, `--paper`, `--accent`, `--border`, etc.)
- `static/css/landing.css` — landing-page-only styles
- `static/js/main.js` — JS stub for students to populate

### Planned route structure (being built out step by step)
| Route | Step | Purpose |
|---|---|---|
| `/` | done | Landing page |
| `/register`, `/login` | done (UI), Step 3 (logic) | Auth forms |
| `/logout` | Step 3 | Clear session |
| `/profile` | Step 4 | User profile |
| `/expenses/add` | Step 7 | Add expense form |
| `/expenses/<id>/edit` | Step 8 | Edit expense |
| `/expenses/<id>/delete` | Step 9 | Delete expense |

### CSS conventions
- Design tokens are CSS variables defined on `:root` in `style.css`
- Responsive breakpoints: 900px (tablet) and 600px (mobile)
- Component naming: `.btn-primary`, `.btn-ghost`, `.form-input`, `.auth-card`, `.mock-card`
- Landing page sections: `.hero`, `.features`, `.cta-section`; legal pages: `.legal-page`

### Template pattern
Every page template:
```jinja
{% extends "base.html" %}
{% block title %}Page Title{% endblock %}
{% block content %}
  <!-- page body -->
{% endblock %}
```

### Currency
The app uses Indian Rupee (₹) as the default currency.
