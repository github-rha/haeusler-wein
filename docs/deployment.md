# Deployment & DNS

This website is deployed with **GitHub Pages** and served on the custom domain **haeusler-wein.ch**.

## Deployment

- Hosting: GitHub Pages
- Repo: github.com/github-rha/haeusler-wein
- Branch: `main`
- Publish directory: repository root (`/`)
- Deploy trigger: every push to `main`
- HTTPS: enabled via GitHub Pages (Enforce HTTPS)

Deploy workflow:

    git add .
    git commit -m "Update site"
    git push

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

## GitHub Pages settings

Configured in: Repository → Settings → Pages

- Source: `main` branch
- Folder: `/ (root)`
- Custom domain: `haeusler-wein.ch`
- Enforce HTTPS: enabled

## Troubleshooting

Check DNS:

    dig haeusler-wein.ch +short

Expected: only the 185.199.108–111.153 IPs.
