# Operations — haeusler-wein.ch

## Deployment

```
  Edit content / markup
         │
         ▼
  git commit + git push to main
         │
         ▼
  ┌──────────────────────────────┐
  │  GitHub Pages                │
  │  • managed Jekyll build      │
  │  • static files served via   │
  │    CDN, HTTPS enforced       │
  └──────────────────────────────┘
         │
         ▼
  haeusler-wein.ch
```

- **Hosting**: GitHub Pages.
- **Repo**: github.com/github-rha/haeusler-wein.
- **Branch**: `main`.
- **Publish directory**: repository root (`/`).
- **Deploy trigger**: every push to `main`.
- **HTTPS**: enabled via GitHub Pages ("Enforce HTTPS").
- **Zero backend** — the site is static files only. There is no server process, database, or container to operate.

Deploy workflow:

    git add .
    git commit -m "Update site"
    git push

## GitHub Pages settings

Configured in: Repository → Settings → Pages.

- Source: `main` branch
- Folder: `/ (root)`
- Custom domain: `haeusler-wein.ch`
- Enforce HTTPS: enabled

## DNS (Hostpoint)

DNS is managed at Hostpoint. **Nameservers remain unchanged**:

- ns.hostpoint.ch
- ns2.hostpoint.ch
- ns3.hostpoint.ch

Only DNS records were changed.

### Removed (old Hostpoint web hosting)

The following records were removed because they pointed to the old hosting:

- A: `haeusler-wein.ch` → 217.26.52.25
- A: `*.haeusler-wein.ch` → 217.26.52.25
- AAAA: `haeusler-wein.ch` → 2a00:d70:0:b:2002:0d91:3419
- AAAA: `*.haeusler-wein.ch` → 2a00:d70:0:b:2002:0d91:3419

### Added (GitHub Pages)

Apex domain (`haeusler-wein.ch`) A records:

- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

`www` subdomain:

- CNAME: `www` → `github-rha.github.io`

### Email records

Mail-related records (MX / SPF / DKIM / mail CNAMEs like autoconfig/autodiscover) were **not changed**.

## Workflow

- Source of truth is the Git repository.
- Pushing to `main` deploys the site automatically.
- No manual copying of files to servers.
- Structural or architectural changes:
  - done on a feature branch
  - go through a pull request (even for solo work)
  - squash-merged

### Change discipline

- Make the smallest possible change.
- One logical change per commit.
- Avoid touching unrelated files.
- Explain *why* a change is needed before implementing it.

If a change cannot be explained clearly in 2–3 sentences, it is probably too complex.

## Monitoring

| What                      | How                                         |
|---------------------------|---------------------------------------------|
| Site availability         | GitHub Pages status (status.github.com)     |
| Build / deploy failures   | GitHub Actions notifications (email)        |
| DNS                       | `dig haeusler-wein.ch +short` — expect only the 185.199.108–111.153 IPs |

No external monitoring service. The site is small and largely static; if something breaks, it is noticed by the owner directly.

## Recovery

| Scenario                  | Recovery path                               |
|---------------------------|---------------------------------------------|
| Bad deploy                | Revert the commit on `main`; Pages redeploys automatically. |
| Accidentally broken content | Restore previous `_data/content.yml` from git history. |
| GitHub Pages outage       | Wait — no fallback hosting is configured (intentional, see vision). |
| Lost DNS config           | Re-create the records above at Hostpoint. |

The Git repository is the disaster recovery mechanism. Everything that
defines the site lives in version control.
