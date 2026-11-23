# Research Knowledge Hub

個人研究知識庫：集中整理論文閱讀心得、演算法與技術知識，以及研究主題。

## Project goals
- 以固定六大章節保存論文心得。
- 將跨論文出現的演算法、模型與研究方法整理成獨立知識頁。
- 透過研究主題、站內搜尋與交叉連結找回既有知識。

## Tech stack
- MkDocs
- Material for MkDocs
- Markdown / YAML
- GitHub Pages

## Local preview
```bash
python -m venv .venv
# Windows PowerShell:
.venv\\Scripts\\Activate.ps1
# macOS / Linux:
source .venv/bin/activate

pip install -r requirements.txt
mkdocs serve
```
Open the local address printed by MkDocs (usually http://127.0.0.1:8000).

## Build
```bash
mkdocs build --strict
```

## Content workflow
1. Read `AGENTS.md`.
2. Copy a template from `templates/`.
3. Add the new Markdown file under `docs/papers/` or `docs/knowledge/`.
4. Update the corresponding index, topic page, and `mkdocs.yml` navigation.
5. Preview and build the site.
6. Commit and push to GitHub.

## Public content reminder
Only publish material you have the right to share. Do not upload full-text publisher PDFs or private course documents to the public repository. Prefer DOI and official links.


## 發布前設定

請先將 `mkdocs.yml` 的 `site_url` 中 `YOUR_GITHUB_NAME` 替換成自己的 GitHub 使用者名稱，再依照 GitHub Pages 設定發布。
