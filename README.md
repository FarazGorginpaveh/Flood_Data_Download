# Flood_Data_Download
NOAA Storm Events Database
The dataset is event-based, where each row represents a single recorded event (e.g., flood, flash flood, high wind) reported by the National Weather Service. The files are organized by year, and the naming convention reflects both the data year and the file update date. For example, a file labeled “d1996” contains events that occurred in 1996, while the “cYYYYMMDD” portion indicates the date the file was last updated.

Each event includes detailed temporal information. The primary fields are BEGIN_YEARMONTH, BEGIN_DAY, and BEGIN_TIME, along with their corresponding END fields. These represent the start and end of the event, where time is recorded in HHMM format (e.g., 1710 corresponds to 17:10). However, the dataset also provides combined timestamp fields (BEGIN_DATE_TIME and END_DATE_TIME), which are more convenient and reliable for analysis. These fields allow direct conversion to standard datetime formats for time-series analysis. It is important to note that although the file is organized by year, the exact event timing should always be determined from these timestamp fields.

Spatially, events are reported at the county or forecast zone level. The key fields include STATE and CZ_NAME (county or zone name), along with CZ_FIPS and CZ_TYPE. While CZ_TYPE may indicate forecast zones rather than exact county boundaries, CZ_NAME is commonly used as a proxy for county-level analysis in the literature. This allows aggregation of events to the county level without requiring additional spatial processing.

Each event also contains descriptive and impact-related variables. These include EVENT_TYPE (e.g., Flood, Flash Flood), DAMAGE_PROPERTY and DAMAGE_CROPS (economic impacts), and counts of injuries and fatalities. In addition, narrative fields provide textual descriptions of each event, which can be useful for qualitative analysis or natural language processing.

The dataset distinguishes between EPISODE_ID and EVENT_ID, where an episode represents a broader weather system and events represent individual occurrences within that system. This means that a single storm system may generate multiple events across different counties.

For flood-specific analysis, the dataset can be filtered using EVENT_TYPE equal to “Flood” or “Flash Flood.” After filtering, the data can be aggregated by county and time (e.g., daily, monthly, or yearly) to derive indicators such as flood frequency, duration, and reported damages.
