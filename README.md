# IsoVault site (local)

How to run locally:

```bash
python -m pip install --upgrade pip
# prefer pipx, fallback to pip
pipx install mkdocs-material || pip install mkdocs-material
pip install mkdocs-minify-plugin mkdocs-redirects
mkdocs serve
```

Build & deploy (publish to gh-pages):

```bash
mkdocs gh-deploy --clean --force -b gh-pages
```
