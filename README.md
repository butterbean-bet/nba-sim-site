# nba-sim-site

Static NBA board (Underdog / PrizePicks) + **10k Monte Carlo win%** on the Games tab.
Same dark UX as nfl-sim-site.

Live: https://butterbean-bet.github.io/nba-sim-site/

## Files
- `index.html` — site (embedded `data.json`)
- `data.json` — last payload
- `.nojekyll` — GitHub Pages

Pipeline: `/workspace/nba-sim/run.py --sims 10000 --update-site` then commit/push here.
Track record CSV: `/workspace/nba-sim/data/track_record.csv`

Win% is board context only — not sportsbook tickets.
