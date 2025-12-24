# FlASK_BLOG Tutorial

**Repository:** https://github.com/chsu02/flask_blog.git

---
## Contents
Refer to this <a href="https://www.digitalocean.com/community/tutorials/how-to-make-a-web-application-using-flask-in-python-3" target="_blank">tutorial</a>
## Overview
A tiny example blog application built with Flask following the DigitalOcean "How To Make a Web Application Using Flask in Python 3" tutorial. This repository demonstrates a minimal CRUD app using SQLite and server-side rendered templates.

---

## Features ✨
- List posts on the home page
- Create new posts
- View a single post
- Edit and delete posts
- Uses SQLite for storage (no external DB required)

---

## Prerequisites ⚙️
- Python 3.8+ installed (recommended: 3.10+)
- Recommended: create and use a virtual environment

---

## Using uv (Astral) — optional 📦
`uv` is a fast, cross-platform Python package and project manager from Astral that can replace tools like `pip`, `pipx`, and `virtualenv`. It provides fast installs, lockfiles, Python version management, and a pip-compatible interface.

**Install**
- macOS / Linux (recommended installer):

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

- Windows or pip-based install:

```powershell
python -m pip install uv
```

See https://docs.astral.sh/uv/getting-started/installation/ for other install options.

**Quick uv workflow (from this repo)**

```bash
# create a project venv (creates .venv)
uv venv --python 3.11

# install project dependencies from requirements.txt
uv pip sync requirements.txt

# initialize the database
uv run python init_db.py

# run the dev server (Flask)
uv run -- python -m flask --app app --debug run
```

**Windows PowerShell**

```powershell
uv venv --python 3.11
uv pip sync requirements.txt
uv run python init_db.py
uv run -- python -m flask --app app --debug run
```

**Notes**
- `uv` manages environments and packages; it is *not* an HTTP server. For an ASGI server, use `uvicorn` (a different project).
- Use `uv python install` / `uv python pin` to install or pin Python versions, and `uv lock` / `uv sync` for reproducible installs.
- `uv` supports macOS, Linux, and Windows.

Link: https://docs.astral.sh/uv/

---

## Quick Start (Linux / macOS)
1. Create and activate a virtual environment:

```bash
python -m venv venv
source venv/bin/activate
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Initialize the database (creates `database.db` and sample posts):

```bash
python init_db.py
```

4. Run the app:

```bash
export FLASK_APP=app.py
export FLASK_ENV=development    # optional, enables debug reloading
flask run
```

---

## Quick Start (Windows PowerShell)
```powershell
python -m venv venv
venv\Scripts\Activate.ps1
pip install -r requirements.txt
python init_db.py
$env:FLASK_APP = "app.py"
$env:FLASK_ENV = "development"
flask run
```

> The app will be available at http://127.0.0.1:5000/ by default.

---

## Important Notes 🔒
- The app currently sets `app.config['SECRET_KEY'] = 'your secret key'` in `app.py` for simplicity. **Do not use this in production** — set a random secret key (use environment variables or a config file).
- The database is a local SQLite file named `database.db` in the project root.

---

## Routes / Usage 📚
- GET `/` — list all posts
- GET `/create` & POST `/create` — create a new post
- GET `/<id>` — view a single post
- GET `/<id>/edit` & POST `/<id>/edit` — edit a post
- POST `/<id>/delete` — delete a post

---

## Project Structure 🔧
- `app.py` — main Flask application (routes)
- `init_db.py` — creates `database.db` and inserts sample posts
- `schema.sql` — DB schema for the `posts` table
- `templates/` — HTML templates (`index.html`, `create.html`, `edit.html`, `post.html`, `base.html`)
- `static/` — static assets (CSS)

---

## Contributing 🤝
Improvements, bug fixes, and documentation updates are welcome. Create a PR and describe the change.

---

## License
No license specified. Add a `LICENSE` file if you want to define reuse terms.

---

If you'd like, I can also add a short `CONTRIBUTING.md`, set up a basic test, or add recommended environment variable support for the secret key. 💡