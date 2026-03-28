# Build Doc — phoenix-sharepoint-theme
**Owner:** GIT-PHOENIX-HUB | **Last Updated:** 2026-03-27

## Objectives
1. Confirm the PowerShell theme installer has been applied to the Phoenix Electric M365 tenant.
2. Make the GitHub Pages homepage functional — replace placeholder links with real SharePoint site URLs.
3. Add a README documenting setup prerequisites and usage.
4. Resolve two unmerged remote branches.

## End State
A fully applied Phoenix Electric brand on SharePoint Online with a functional GitHub Pages hub page that links to live SharePoint document libraries. The PowerShell installer is idempotent and documented. Any future theme changes flow through this repo.

## Stack Decisions
| Decision | Choice | Rationale |
|----------|--------|-----------|
| Theme deployment | PowerShell + SPO Management Shell | Only supported method for custom tenant-level SharePoint themes |
| Homepage | Vanilla HTML/CSS | Zero dependencies, served directly from GitHub Pages, no build step |
| Auth | Interactive M365 login (OIDC) | No service principal needed for manual one-time theme application |

## Architecture Targets
- Add `.github/workflows/pages.yml` to formally configure GitHub Pages deployment from `main`.
- Replace `href="#"` placeholders in `index.html` with real SharePoint site URLs when available.
- Consider whether the PowerShell script and the HTML homepage belong in the same repo long-term, or if the homepage should move to a dedicated `phoenix-intranet-home` repo.

## Success Criteria
- [ ] PowerShell script confirmed run against production M365 tenant — `PhoenixElectric-Dark` visible in tenant theme gallery
- [ ] GitHub Pages homepage links all resolve to real SharePoint URLs
- [ ] README added with prerequisites (PowerShell module, M365 admin rights) and usage instructions
- [ ] `copilot/review-plan-build-install` branch reviewed and either merged or closed
- [ ] `shane7777777777777-patch-1` branch reviewed and either merged or closed

## Dependencies & Blockers
| Dependency | Status | Owner |
|-----------|--------|-------|
| M365 tenant admin access to run PowerShell installer | Unknown — not confirmed | Shane |
| Real SharePoint site URLs for homepage links | Not yet collected | Shane |
| Decision: combine or split PowerShell script and homepage | Needs input | Shane |

## Change Process
All changes to this repository follow the Phoenix Electric governance model:

1. **Branch:** Create feature branch from `main`
2. **Develop:** Make changes with clear, atomic commits
3. **PR:** Open pull request with description of changes
4. **Review:** Required approval from `@GIT-PHOENIX-HUB/humans-maintainers`
5. **CI:** All status checks must pass (when configured)
6. **Merge:** Squash merge to `main`
7. **No force push.** No direct commits to `main`. No deletion without `guardian-override-delete` label.

## NEEDS SHANE INPUT
- Has the PowerShell theme installer been run against the Phoenix Electric M365 tenant? If yes, document the date and which themes are active.
- What are the real SharePoint site URLs for the homepage navigation cards (Accounting, Reports, Employees, Construction, Service, Pricebook, Vendors, Taxes, Field Pub, AI Zone)?
- Should the GitHub Pages homepage link out to the real `phoenix-ops` SharePoint site, or does it need its own navigation logic?
- Should the PowerShell script and HTML homepage remain in the same repo, or split into separate repos?
