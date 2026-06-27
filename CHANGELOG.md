
All notable changes to Predinex Stellar are documented here.
Entries are grouped by delivery area so each stakeholder can scan the section relevant to them.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versions follow [Semantic Versioning](https://semver.org/).

---

## [Unreleased]

### ⛓ Contract
- Fixed pool counter off-by-one: first pool now starts at ID 1 and `get_pool_count` returns the actual count instead of `count + 1` (closes #597)
- `get_pools_batch` added for efficient batch pool queries, reducing N+1 contract calls to 2 (closes #604)

### 🌐 Web
- Updated `getMarkets` and `fetchAllPools` to use the corrected pool count from `get_pool_count`

### 📖 Docs
<!-- README, RELEASE, architectural docs, inline documentation -->
- Added comprehensive preview deployment documentation (`docs/preview-deployments.md`)
- Added quick start guide for preview deployment setup in `docs/preview-deployments.md`
- Updated README with preview deployment information

### ⚙️ Ops & CI
<!-- GitHub Actions workflows, scripts/, tooling, dependency updates -->
- Added automated preview deployment workflow for pull requests (`.github/workflows/preview-deploy.yml`)
- Preview deployments automatically post URLs to PR comments
- Added PR template with preview deployment checklist
- Added preview deployment issue template
- Added setup script for configuring preview deployments (`scripts/setup-preview-deployments.sh`)
- Added Vercel configuration file (`web/vercel.json`)
- Fixed `tag-release.yml` to use `PAT_TOKEN` instead of `GITHUB_TOKEN` so tag pushes trigger downstream CI workflows (closes #600)

---

## [v0.1.0] - 2026-04-25

### ⛓ Contract
- Initial Clarity prediction-market contract with pool creation, betting, and settlement logic.

### 🌐 Web
- Next.js frontend with wallet connection (Stacks/WalletConnect), market browsing, and dashboard.
- Dispute resolution UI with community voting.
- Lazy-loaded route bundles for `/dashboard` and `/disputes` to reduce initial JS weight.

### 📖 Docs
- `RELEASE.md` release checklist and version-tagging guide.
- `web/docs/` — AppKit integration, contract events, contract versioning, market-list caching, route chunking.

### ⚙️ Ops & CI
- GitHub Actions: `ci.yml` (build + lint), `security-audit.yml`, `tag-release.yml`.
- Dependency caching strategy documented in `web/DEVELOPMENT.md`.
