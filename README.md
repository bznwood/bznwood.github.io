# Bozeman Woodworkers Guild website

Static site for the Bozeman Woodworkers Guild, published with GitHub Pages.

- Live site: https://bznwood.com/ (also https://bznwood.github.io/, which redirects)
- Edit `index.html` and push; GitHub Pages redeploys automatically.

## Publishing (one-time setup)

Repo **Settings → Pages → Build and deployment**: Source = "Deploy from a branch",
Branch = `main`, folder = `/ (root)`, then Save.

## Handing off the account

The `bznwood` GitHub account is dedicated to the guild. To hand it off, the new
maintainer should change the account email and password, set up their own
two-factor authentication, and update recovery codes. Alternatively, add them as a
collaborator (Settings → Collaborators) so they can edit without sharing login.

## Custom domain (bznwood.com)

DNS is hosted in AWS Route 53 (hosted zone `bznwood.com`). Records pointing at GitHub Pages:

| Name | Type | Value |
|---|---|---|
| `bznwood.com` | A | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| `bznwood.com` | AAAA | `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153` |
| `www.bznwood.com` | CNAME | `bznwood.github.io` |

The `CNAME` file in this repo tells GitHub Pages to serve the site at `bznwood.com`;
`www.bznwood.com` and `bznwood.github.io` redirect to it. Keep "Enforce HTTPS" on in
Settings → Pages. If the domain registration is handed off, transfer the Route 53
hosted zone (or recreate these records) along with it.
