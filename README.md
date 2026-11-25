# XAUUSD Levels

A GitHub Action runs once a day, Monday to Friday, at 04:00 Kenya time (01:00 UTC). That is 1 hour after the Asian session open (Tokyo open, 09:00 Tokyo = 00:00 UTC = 03:00 Kenya time). It reads the GLD options chain and writes levels.json.

The page only reads that file, so the options-derived levels stay frozen until the next run. Spot price, candles, market profile and prior highs and lows come live from Binance in the browser.

All files live in the repo root except the workflow, which must be at .github/workflows/analyze.yml.

## Setup
1. Create a new public GitHub repository.
2. Add every file to the repo root. Create the workflow as .github/workflows/analyze.yml (use "Create new file" and type that path).
3. Settings > Actions > General > Workflow permissions: choose "Read and write permissions" and save.
4. Settings > Pages: Source "Deploy from a branch", branch main, folder / (root), save.
5. Actions tab > "Daily levels analysis" > Run workflow. When it finishes, the sample banner disappears.

## Notes
- GitHub cron can run several minutes late. The page shows the real analysis time.
- The stale-data warning fires after 26 hours Tuesday to Friday, and after 74 hours over the weekend and on Monday.
- At 04:00 Kenya time the US options market is closed, so the levels use the previous day's published open interest.
