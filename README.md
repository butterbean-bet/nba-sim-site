# nba-sim-site

Static NBA board (Underdog / PrizePicks) + **10k Monte Carlo win%** on the Games tab,
with **Polymarket and Kalshi** mid-price win % next to the sim when a public
game-winner market exists. Same dark UX as nfl-sim-site.

Live: https://butterbean-bet.github.io/nba-sim-site/

## Files
- `index.html` — site (embedded `data.json`)
- `data.json` — last payload
- `.nojekyll` — GitHub Pages

## Noon refresh

Do **not** run `/workspace/nba-sim/run.py --update-site`. That command wipes
the Track Record sim % and Pick'em history. Safe sequence:

```bash
cd /workspace/nba-sim
python3 run.py --sims 10000                 # output/games_DATE.json only
# Patch data.json by hand: replace tabs.Games (and sim / date / updated)
# from that file. Leave Pick'em, Player Props, Track Record, and Injuries
# untouched. Re-embed the payload in index.html as `const D=...;`.
python3 markets.py --update-site            # adds Polymarket + Kalshi
cd /workspace/nba-sim-site
git add data.json index.html
git commit -m "Noon refresh $(date +%F)"
git push origin main
```

`markets.py` lives in `/workspace/nba-sim/`. It uses only free public endpoints
(Polymarket Gamma API, Kalshi trade-api/v2). No Odds API, no auth. A 10+ point
gap vs the sim is flagged. Logged player-prop legs are matched when a market
exists; if the market line differs from the Underdog line, that is noted
instead of treating them as the same prop.

Track record CSV: `/workspace/nba-sim/data/track_record.csv`

Win% is board context only — not sportsbook tickets.
