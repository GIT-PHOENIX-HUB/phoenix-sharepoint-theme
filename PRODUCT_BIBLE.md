# Product Bible — phoenix-sharepoint-theme
**Owner:** GIT-PHOENIX-HUB | **Last Updated:** 2026-03-27

## Purpose
SharePoint Online branding package for Phoenix Electric. Applies the Phoenix Electric color theme (Red `#FF1A1A`, Gold `#D4AF37`, Black `#0a0a0a`) to a Microsoft 365 tenant via PowerShell. Includes three theme variants — Dark (primary), Gold (finance/accounting pages), and Light. Also provides a branded GitHub Pages homepage (`index.html`) styled as the Phoenix Ops SharePoint landing page with navigation cards for all major business areas.

## Stack
| Layer | Technology | Version |
|-------|-----------|---------|
| Scripting | PowerShell | 5.1+ (Windows) |
| SharePoint Module | Microsoft.Online.SharePoint.PowerShell | Latest (auto-installs) |
| Frontend | HTML/CSS (vanilla) | — |
| Fonts | Google Fonts — Cinzel, Inter | — |
| CI/CD | None | — |
| Deploy Target | SharePoint Online tenant / GitHub Pages | — |

## Architecture
Two independent deliverables in one repo:

1. `Phoenix-SharePoint-Theme.ps1` — PowerShell script that connects to SharePoint Online admin, registers three custom themes in the tenant theme gallery, and optionally applies a theme to a specific site URL.
2. `index.html` — Standalone branded homepage served via GitHub Pages. Provides a visual hub with navigation cards for all SharePoint document libraries (Accounting, Reports, Employees, Construction, Service, Pricebook, Vendors, Taxes, Field Pub, AI Zone).

```
phoenix-sharepoint-theme/
  Phoenix-SharePoint-Theme.ps1   # PowerShell theme installer (3 theme variants)
  index.html                     # GitHub Pages branded homepage
  assets/
    Phoenix_Transparent.png      # Phoenix logo (transparent, used in index.html)
    Phoenix_Black_Background.jpg # Phoenix logo with black background
  CODEOWNERS                     # * @GIT-PHOENIX-HUB/humans-maintainers
```

## Auth & Security
- PowerShell script connects via `Connect-SPOService` using SharePoint Online Management Shell — interactive login, no credentials stored in repo.
- Auth model is OIDC / Microsoft 365 tenant authentication.
- The script accepts `-AdminUrl` and `-SiteUrl` as parameters — no hardcoded tenant identifiers in tracked code.
- No secrets, tokens, or vault references in any tracked file.

## Integrations
| Integration | Method | Purpose |
|-------------|--------|---------|
| SharePoint Online | PnP PowerShell / SPO Management Shell | Apply custom tenant themes |
| GitHub Pages | Static HTML | Serve branded homepage from `main` branch |

## File Structure
| Path | Purpose |
|------|---------|
| `Phoenix-SharePoint-Theme.ps1` | Theme installer — 3 variants: PhoenixElectric-Dark, PhoenixElectric-Gold, PhoenixElectric-Light |
| `index.html` | Branded GitHub Pages homepage with navigation cards |
| `assets/Phoenix_Transparent.png` | Logo used as animated backdrop in index.html |
| `assets/Phoenix_Black_Background.jpg` | Alternative logo asset |
| `CODEOWNERS` | All files require @GIT-PHOENIX-HUB/humans-maintainers approval |

## Current State
- **Status:** minimal / early stage
- **Last Commit:** 2026-03-27 — Add CODEOWNERS (2026-02-07 for substantive content)
- **Open PRs:** None on main
- **Open Branches:** 2 remote — `copilot/review-plan-build-install` (unmerged), `shane7777777777777-patch-1` (unmerged)
- **Known Issues:**
  - 2 remote branches (`copilot/review-plan-build-install`, `shane7777777777777-patch-1`) are unmerged — contents and relevance unknown.
  - No README in the repo — purpose and usage are undocumented beyond the PowerShell script's inline synopsis.
  - `index.html` navigation links are all `href="#"` placeholders or internal paths (e.g., `/ACCOUNTING`) — none point to real SharePoint URLs. Page is decorative, not functional.
  - PowerShell script has only been committed — no record of whether it has been run against the tenant.
  - No automated deployment pipeline to apply theme on changes.

## Branding & UI
Primary brand palette used across all theme variants:
| Token | Value | Use |
|-------|-------|-----|
| Phoenix Red | `#FF1A1A` | Primary brand color, buttons, headers |
| Phoenix Gold | `#D4AF37` | Accent, AI zone highlight, Finance theme primary |
| Deep Black | `#0a0a0a` | Page background (dark mode) |
| White | `#FFFFFF` | Primary text (dark mode) |

Three SharePoint theme variants registered:
- `PhoenixElectric-Dark` — Red primary, dark background (main tenant theme)
- `PhoenixElectric-Gold` — Gold primary, same dark background (Finance/Accounting)
- `PhoenixElectric-Light` — Red primary, standard light backgrounds

Fonts: Cinzel (display/headers), Inter (body) — loaded from Google Fonts.

## Action Log
| Date | Hash | Description |
|------|------|-------------|
| 2026-03-27 | 8136aee | Add CODEOWNERS for Phoenix Electric governance |
| 2026-02-07 | 143e3ba | Rename to index.html for GitHub Pages |
| 2026-02-07 | e39b069 | Phoenix Ops SharePoint Theme — Initial commit |

## Key Milestones
| Date | Milestone |
|------|-----------|
| 2026-02-07 | Repo created with PowerShell installer and branded homepage |
| 2026-03-27 | CODEOWNERS added — governance baseline established |
| 2026-03-27 | PRODUCT_BIBLE and BUILD_DOC written |
