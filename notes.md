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
- Main dataset (aqi.csv): 1,126-day calendar, 1 missing day (2025-01-01), filled by interpolation and flagged in was_filled
- Older dataset (city_day.csv): 399 of 1,858 days have no AQI (about 21%)
- Missing share by year: 2015: 62%, 2016: 10%, 2017: 61%, 2018: 1%, 2019: 2%, 2020: 0%
- Longest gap: 171 days, 2017-04-14 to 2017-10-01
- Second longest: 124 days, 2015-06-01 to 2015-10-02
- 50 separate gaps in total; the top two gaps make up about 295 of the 399 missing days
- Decision: fill gaps of 3 days or less only. Don't fill the long gaps.
- Decision: use 2018-2020 as the reliable part of the older dataset. 2015 and 2017 are too incomplete for full-year analysis.
- Concern: the big gaps fall in the warmer, probably cleaner months, so monthly averages from all years could be biased
- Saved data/patna_clean.csv