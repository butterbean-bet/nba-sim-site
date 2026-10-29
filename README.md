# nba-sim-site

Static NBA pick'em board (Underdog / PrizePicks), same dark UX as nfl-sim-site.

## Files
- `index.html` — site
- `data.json` — last embedded payload
- `.nojekyll` — GitHub Pages

Track record: `/workspace/nba-sim/data/track_record.csv`

## Publish (wait for user OK — do not run yet)

```bash
cd /workspace/nba-sim-site
git init
gh repo create butterbean-bet/nba-sim-site --public --source=. --remote=origin
git add index.html .nojekyll README.md
# optional: omit data.json from public repo if preferred
git commit -m "NBA pick'em site"
git branch -M main
git push -u origin main
gh api -X POST repos/butterbean-bet/nba-sim-site/pages \
  -f build_type=legacy -f source[branch]=main -f source[path]=/
```

Expected URL: https://butterbean-bet.github.io/nba-sim-site/
