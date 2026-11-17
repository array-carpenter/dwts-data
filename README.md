# dwts-data

Every scored dance from *Dancing with the Stars* (US), seasons 1 to 35, plus every Kalshi elimination market so far.

Built for [Advanced Dancing With The Stars Analytics](https://thespade.substack.com) on The Spade. Data runs through Season 35, Week 9 (November 10, 2026).

## Files

| File | Rows | One row per |
|---|---|---|
| `data/dances.csv` | 3,501 | scored dance |
| `data/couple_weeks.csv` | 2,853 | couple per week |
| `data/cast.csv` | 437 | celebrity per season |
| `data/ratings_celebrities.csv` | 268 | celebrity (6+ scored dances) |
| `data/ratings_pros.csv` | 27 | pro (40+ scored dances) |
| `data/kalshi/markets.csv` | 178 | settled Kalshi elimination market |
| `data/kalshi/trades.csv.gz` | 159,188 | Kalshi trade |

### dances.csv

`season`, `week`, `night`, `running_order`, `couple` (as written on Wikipedia), `celebrity`, `pro`, `dance`, `total_score`, `n_judges`, `judge_1` to `judge_5` (in the order the scores were listed that week), `result`.

Group dances, team dances, trios, and dance-offs are not included. `result` is blank where the table did not list one.

### couple_weeks.csv

`season`, `week`, `celebrity`, `pro`, `dances` (that week), `avg_judge_score` (per judge, out of 10), `couples_that_week`, `eliminated` (1 if the couple went home that week), `finale_week`.

### cast.csv

`season`, `celebrity`, `pro`, `known_for`, `status` (as written on Wikipedia), `finish` (T = tied after a double elimination), `birth_date`, `sex`, `wikipedia`, `wikidata`.

### ratings_celebrities.csv / ratings_pros.csv

Ratings from the mixed model in the post, in points per judge per dance.

- `rating`: points a celebrity (or pro) adds with the partner held constant.
- `raw`: plain average above the rest of the field that week.
- `range_low`, `range_high` (pros only): 90% range, widened to match a split-half repeat test.

### kalshi/markets.csv

`ticker`, `event`, `season`, `contestant` (`NONE` = no elimination), `title`, `result`, `open_time`, `close_time` (UTC), `volume` (contracts), `preshow_vwap_3h` (volume-weighted YES price in the 3 hours before 8 p.m. ET showtime), `preshow_last_price`.

### kalshi/trades.csv.gz

`ticker`, `time` (UTC), `yes_price` (dollars), `contracts`, `taker_side`, `block_trade`, `trade_id`.

## Sources

- Scores, results and cast: Wikipedia season pages for *Dancing with the Stars (American TV series)*.
- Birth dates and sex: Wikidata.
- Markets and trades: Kalshi public API, series `KXDWTSELIMINATION`. Only settled markets are included.

## License

Data from Wikipedia and Wikidata is shared under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Kalshi data is provided as-is for research; check Kalshi's terms before commercial use.

If you use this, credit Ray Carpenter / The Spade and link back here.
