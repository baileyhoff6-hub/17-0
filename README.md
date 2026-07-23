# 17-0

A browser game where you build an all-time NFL roster by spinning for team-season combinations, then simulate a 17-game season to see if you can go undefeated.

Play it: [17-0football.org](https://17-0football.org)

## How it works

You get six spins. Each one lands on a real team from a real season, anywhere from 2000 to 2025. You choose whether to raid that roster's offense or defense, then take two starters from it. One reroll per spin lets you swap either the team or the year, but not both. Any team-season you've already used won't come up again.

Kickers are a free bonus on any spin and don't cost you a pick, though skipping one entirely costs you points in the simulation.

Once your twelve slots are filled, the season runs. Position weights decide how much each pick matters: quarterback is 20% of your offensive rating, the offensive line 13%, edge rusher 12%, kicker 2%. Opponents are generated with random ratings each week, so the same roster won't always produce the same record.

There's also a draft board mode that drops the spin constraint entirely and lets you pick the highest-rated player at each position across the whole pool.

## The data

830 team-seasons covering 2000 through 2025. Every player is real and every roster reflects who actually started for that team that year.

Identifying starters took three different methods, because no single source covers the full range:

| Seasons | Source | Method |
|---|---|---|
| 2013–2025 | nflverse snap counts | Aggregate regular-season snaps per player, take the leaders at each position |
| 2001–2012 | nflverse depth charts | Count weeks listed as first-string |
| 2000 | nflverse play-by-play | Derive participation from who threw, ran, caught, tackled, sacked, and kicked |

The 2000 season needed extra work. Play-by-play never names offensive linemen, since they don't touch the ball, so 23 of 31 teams came back with none. Those were backfilled using the highest-rated linemen from Madden 2001.

Player ratings are Madden overall ratings for that player's season, matched by name and team across 26 years of rating data. About 94% matched directly. The rest were resolved by name-only matching, fuzzy matching, or estimated from their position's median. Estimated ratings are marked with an asterisk in the game.

## Running it

It's a single self-contained HTML file. Open `index.html` in any browser. No build step, no dependencies, no server.

## Credits

Snap counts, depth charts, and play-by-play data from [nflverse](https://github.com/nflverse/nflverse-data), originally sourced from Pro Football Reference. Madden ratings compiled from publicly available season data.

## Disclaimer

A fan-made project. Not affiliated with, endorsed by, or licensed by the National Football League, the NFL Players Association, or Electronic Arts. Player names and statistics are used for identification only. Simulated season results are invented and do not reflect real outcomes.
