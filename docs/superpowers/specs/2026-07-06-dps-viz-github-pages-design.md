# dps-viz: GitHub Pages plot gallery — Design

## Purpose
Host standalone Plotly HTML plot exports on GitHub Pages with a simple landing
page that links to each plot.

## Repo
- Name: `dps-viz`
- Visibility: public (required for GitHub Pages on a free personal account)
- Owner: `fcovi-cmcc` (GitHub account, authenticated via `gh`)
- Pages source: `main` branch, root — static files only, no build step

## Structure
```
dps-viz/
├── index.html
└── plots/
    └── 2025110100_R025_01_restart_oce_modified_dps2_depth_profile_lite.html
```

## index.html
- Plain HTML/CSS, no framework or build tooling
- Heading + a `<ul>` of links, one per plot
- Each entry: a friendly, human-readable title (proposed by Claude, editable)
  linking to the file under `plots/`
- List is maintained by hand: adding a new plot means adding one file under
  `plots/` and one `<li>` entry to `index.html`. No auto-discovery script.

## Deployment
1. `gh repo create dps-viz --public --source=. --push`
2. Enable GitHub Pages (source: `main` branch, `/` root) via `gh api` or repo settings
3. Verify the published URL serves `index.html` and the plot loads

## Out of scope / noted but not solved now
- The current plot file is ~29.5MB. Well under GitHub's 100MB hard limit, but
  if many similarly-sized plots accumulate, repo size will grow quickly.
  No action needed today; revisit if it becomes a problem.
- No auto-generated index, no CI/build pipeline, no styling framework.
