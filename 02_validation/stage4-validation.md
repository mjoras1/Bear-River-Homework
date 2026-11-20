# Stage 4 validation

Validation was performed on November 19, 2026 (Mountain Time). USGS observations are live and provisional values may change.

## Hand calculation

For daily means of 12, a missing day, 18, and 30 cfs:

`sum = 12 + 18 + 30 = 60 cfs`

`mean = 60 / 3 available values = 20.0 cfs`

The app's mean-calculation check returned 20.0 cfs from 3 values. The missing day was not included in the denominator, and a synthetic chart check confirmed that gaps break the plotted line into separate segments.

## Live gage checks

The selected-gage panel was checked against each site's official USGS Water Data page, including its continuous discharge observation and location-details section.

| USGS site | Latest flow shown by app | Observation time (UTC) | Observation time (Mountain) | Drainage area shown by app | Official USGS page |
| --- | ---: | --- | --- | ---: | --- |
| 10039500 - Bear River at Border, WY | 81.4 cfs | 2026-11-20 02:30 UTC | Nov 19, 2026, 7:30 PM MST | 2,480 mi^2 | [USGS monitoring page](https://waterdata.usgs.gov/monitoring-location/USGS-10039500/) |
| 10126000 - Bear River near Corinne, UT | 914.0 cfs | 2026-11-20 02:30 UTC | Nov 19, 2026, 7:30 PM MST | 7,029 mi^2 | [USGS monitoring page](https://waterdata.usgs.gov/monitoring-location/USGS-10126000/) |
| 10020100 - Bear River above Reservoir, near Woodruff, UT | 52.5 cfs | 2026-11-20 02:45 UTC | Nov 19, 2026, 7:45 PM MST | 755 mi^2 | [USGS monitoring page](https://waterdata.usgs.gov/monitoring-location/USGS-10020100/) |

The official pages showed matching flow, observation time, and drainage-area values for all three sites. All three live readings were provisional; the app displayed the same approval status.

## Daily mean hydrograph check

Site `10039500` was checked for the 365 inclusive Mountain-time dates from November 20, 2025, through November 19, 2026. The USGS `daily` collection was queried for parameter `00060` and statistic `00003`. The response contained 364 values in `ft^3/s`; November 19, 2026 had no daily value and appeared as a chart gap.

The source request was the [USGS Water Data daily-values query](https://api.waterdata.usgs.gov/ogcapi/v1/collections/daily/items?monitoring_location_id=USGS-10039500&parameter_code=00060&statistic_id=00003&time=2025-11-20%2F2026-11-19). The downloaded source values and all 365 dates are preserved in [the daily mean CSV](./10039500-daily-mean-2025-11-20-to-2026-11-19.csv). An independent calculation from that CSV produced:

`sum of 364 available daily means = 49,199.4`

`mean = 49,199.4 / 364 = 135.163186813187 cfs`

The app displayed **135.2 cfs**, **364 daily values used**, and **1 missing day**, matching the independent result when rounded to one decimal place.

## Result

The hand calculation, the three live gage comparisons, and the 365-day mean-flow check passed for this validation snapshot. The observations are live; repeat the checks if the USGS data change before submission.
