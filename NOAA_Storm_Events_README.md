NOAA Storm Events Details Dataset — Column Explanations

Overview

This README explains the most important columns commonly found in the NOAA Storm Events **details** dataset (`StormEvents_details-ftp_v1.0_dYYYY_cXXXXXXXX.csv`).


Official NOAA source:
https://www.ncei.noaa.gov/pub/data/swdi/stormevents/csvfiles/

---

# Event Identification Columns

| Column | Explanation |
|---|---|
| BEGIN_YEARMONTH | Year and month when the event began (`YYYYMM`) |
| BEGIN_DAY | Day of month the event started |
| BEGIN_TIME | Local start time (`HHMM`) |
| END_YEARMONTH | Year and month when the event ended |
| END_DAY | Day event ended |
| END_TIME | Local end time |
| EPISODE_ID | Identifier grouping related storm events into a larger weather episode |
| EVENT_ID | Unique identifier for the individual event |
| STATE | State where event occurred |
| STATE_FIPS | Numeric FIPS code for the state |
| YEAR | Event year |
| MONTH_NAME | Month name |
| EVENT_TYPE | Type of event (Tornado, Flood, Flash Flood, Thunderstorm Wind, etc.) |

---

# Location Columns

| Column | Explanation |
|---|---|
| CZ_TYPE | Zone type (`C` = county, `Z` = forecast zone, `M` = marine) |
| CZ_FIPS | County or zone FIPS code |
| CZ_NAME | County or forecast zone name |
| WFO | National Weather Service Forecast Office issuing the report |
| BEGIN_DATE_TIME | Exact local start timestamp |
| CZ_TIMEZONE | Time zone abbreviation |
| END_DATE_TIME | Exact local end timestamp |

---

# Human Impact Columns

| Column | Explanation |
|---|---|
| INJURIES_DIRECT | Number of direct injuries |
| INJURIES_INDIRECT | Number of indirect injuries |
| DEATHS_DIRECT | Number of direct deaths |
| DEATHS_INDIRECT | Number of indirect deaths |

---

# Damage Columns

| Column | Explanation |
|---|---|
| DAMAGE_PROPERTY | Estimated property damage |
| DAMAGE_CROPS | Estimated crop damage |
| DAMAGE_PROPERTY_NUM | Numeric property damage value (commonly created during preprocessing) |
| DAMAGE_CROPS_NUM | Numeric crop damage value |
| DAMAGE_TOTAL_USD | Combined total damage in USD |

---

# Meteorological / Physical Characteristics

| Column | Explanation |
|---|---|
| MAGNITUDE | Measured magnitude of the event |
| MAGNITUDE_TYPE | Type of magnitude measurement |
| FLOOD_CAUSE | Cause of flood (Heavy Rain, Ice Jam, Dam Break, etc.) |
| CATEGORY | Hurricane category if applicable |
| TOR_F_SCALE | Tornado Fujita or Enhanced Fujita scale |
| TOR_LENGTH | Tornado path length |
| TOR_WIDTH | Tornado width |
| TOR_OTHER_WFO | Another NWS office involved |
| TOR_OTHER_CZ_STATE | Other tornado county state |
| TOR_OTHER_CZ_FIPS | Other tornado county FIPS |
| TOR_OTHER_CZ_NAME | Other tornado county name |

---

# Geographic Coordinate Columns

| Column | Explanation |
|---|---|
| BEGIN_RANGE | Distance from reference location at event start |
| BEGIN_AZIMUTH | Direction from reference location |
| BEGIN_LOCATION | Named start location |
| END_RANGE | Distance at end location |
| END_AZIMUTH | Direction at end location |
| END_LOCATION | Named end location |
| BEGIN_LAT | Start latitude |
| BEGIN_LON | Start longitude |
| END_LAT | End latitude |
| END_LON | End longitude |

---

# Narrative / Description Columns

| Column | Explanation |
|---|---|
| EPISODE_NARRATIVE | Description of the larger weather episode |
| EVENT_NARRATIVE | Description of the specific event impacts and evolution |
| SOURCE | Source of the report (trained spotter, emergency manager, public, etc.) |

---


# Common Storm Event Types

Frequently used EVENT_TYPE categories include:

- Thunderstorm Wind
- Tornado
- Flash Flood
- Flood
- Hail
- Hurricane
- Tropical Storm
- Winter Storm
- Ice Storm
- Heavy Rain
- High Wind
- Lightning
- Coastal Flood
- Storm Surge/Tide

---



