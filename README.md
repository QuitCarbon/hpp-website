# Home Power Planner website (GitHub Pages)

This repository publishes a simple static website to GitHub Pages at the custom domain:

www.HomePowerPlanner.org

The site content lives in the `site/` directory and is deployed by a GitHub Actions workflow.

## How it works

- Static files: `site/` contains `index.html`, two sub‑pages, a minimal CSS file, and a `CNAME` file with the custom domain.
- Deployment: `.github/workflows/deploy-pages.yml` uploads the `site/` folder and deploys it to GitHub Pages on every push to `main` (and via manual run).
- No build step: this is a pure static site; no package manager is required.

## Update the website

1) Edit files under `site/` (e.g. `site/index.html`, `site/subpage-1.html`, `site/subpage-2.html`, `site/assets/styles.css`).
2) Commit your changes on a branch and open a Pull Request.
3) Merge to `main`. The Pages workflow will deploy automatically (see the Actions tab).

Local preview: open `site/index.html` directly in your browser (double‑click) or serve locally with any static server.

## Custom domain and DNS

- Domain: `www.HomePowerPlanner.org` is set via the `site/CNAME` file.
- DNS: create a CNAME record so that `www.homepowerplanner.org` points to `quitcarbon.github.io` (Organization Pages host).
  - Name/Host: `www`
  - Type: `CNAME`
  - Target/Value: `quitcarbon.github.io`
- After DNS propagates, verify Pages settings:
  - Repo → Settings → Pages: ensure the custom domain is set to `www.homepowerplanner.org` and HTTPS is enabled.

References:
- Quickstart: https://docs.github.com/en/pages/quickstart
- Custom domains: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

## Access (so others can update the site)

- Ensure collaborators have write access to this repo. In particular, add Cooper with at least write permission so they can push PRs.
- Path: Repo → Settings → Collaborators and teams → Add people → invite Cooper's GitHub username.

## Troubleshooting

- Action didn’t run: confirm your commit landed on `main` or trigger the workflow manually (Actions → Deploy static site to GitHub Pages → Run workflow).
- Domain not resolving: wait for DNS propagation (can take up to 24 hours). Verify the `CNAME` record and Pages custom domain settings.
- Mixed content/redirects: enable HTTPS in Pages settings after the certificate is issued.
