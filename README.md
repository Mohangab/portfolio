# Mohan Venkatesh Kola — Personal Website

Static personal site (plain HTML + CSS + a few lines of vanilla JS). No build step, no frameworks.

- `index.html` – the single page (About, Experience, Skills, Projects, Education, Contact)
- `assets/style.css` – styles (dark/light theme, mobile-first)
- `assets/favicon.svg` – favicon
- `resume.pdf` – downloadable resume
- `.github/workflows/deploy.yml` – deploys to GitHub Pages on every push to `main`

## Preview locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```
(or just open `index.html` in a browser)

## GitHub Pages

Already enabled: Settings → Pages → **Source: GitHub Actions**. Every push to `main` redeploys.
Live at **https://mohangab.github.io/portfolio/** — use this until you buy a domain.

## Adding a custom domain (when you buy one)

1. **Repo Settings → Pages → Custom domain**: enter your domain (e.g. `example.com` or `www.example.com`) and Save.
2. **DNS at your registrar**:
   - Apex domain (`example.com`): add four `A` records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
     (optional IPv6 `AAAA`: `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`).
   - Subdomain (`www.example.com`): add a `CNAME` record `www` → `mohangab.github.io`.
   - Best: do both, so `example.com` and `www` both work.
3. Wait for DNS (minutes to a few hours), then tick **Enforce HTTPS** in Settings → Pages.
4. *(Optional)* commit a file named `CNAME` at the repo root containing just your domain:
   ```bash
   echo "example.com" > CNAME && git add CNAME && git commit -m "Add custom domain" && git push
   ```
   With the Actions deploy, the Settings value is what counts; the file is just a record.
5. *(Recommended)* verify the domain under your GitHub profile → Settings → Pages to prevent takeover.
6. Update `og:url` in `index.html` to the new domain.
