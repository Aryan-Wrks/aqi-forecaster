# Learning notes

## Day 1
- What I did:
- Any errors I hit and how I fixed them:

## Day 2
- Main dataset: aqi.csv (CPCB daily bulletin AQI), Patna only
  - 1,125 rows, 2022-04-01 to 2025-04-30, 0 duplicates, 1 missing day (2025-01-01)
  - AQI mean about 180, min 36, max 424
  - Main pollutants: PM2.5 and PM10 (PM2.5,PM10 on 567 days)
- Analysis dataset: city_day.csv (Rohan Rao), Patna only
  - 1,858 rows, 2015-06-01 to 2020-07-01
  - 1,459 of 1,858 days have AQI (about 21% missing)
- The two datasets have 0 overlapping days, so I did not merge them
- Bug I hit: str.contains("Patna") also matched Visakhapatnam, so I used an exact match
- Error I hit: city_day.csv was extracted as a folder, which caused a PermissionError

## Day 3
- Main dataset: calendar has 1,126 days, 1 missing (2025-01-01), filled by interpolation (flagged was_filled)
- Rule: fill gaps of 3 days or less only
- Older dataset: AQI missing by year: (paste your numbers)
- Longest gap in older dataset: (start to end, number of days)
- Saved data/patna_clean.csv