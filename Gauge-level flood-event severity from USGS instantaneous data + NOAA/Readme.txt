These are the two dataset regarding the flood events in the LA.

Explanations regarding each of them is provided below:
flood_events_louisiana.csv:   
Each row is one flood event at one USGS streamgage, where a "flood" is a period when the observed gage height rose above that gauge's NOAA/NWS action stage. It carries the gauge's identity (USGS ID, NWS ID, name, latitude/longitude), the event's start, peak, and end times in both local and UTC, the action-stage threshold, the peak gage height and peak discharge, timing (rise time and total hours above threshold), several severity measures, drainage area, and data-quality fields (number of observations, missing-data fraction, provisional fraction, and a quality flag). One row = one event at one gauge. 
The columns and description regarding each of them are provided below:
 
Column	Explanation
usgs_site_id	USGS streamgage identifier. It should be stored as text so its leading zero is preserved.
nws_location_id	NOAA/NWS location or SHEF identifier corresponding to the gauge.
station_name	Name of the streamgage or monitoring location.
latitude	Gauge latitude in decimal degrees.
longitude	Gauge longitude in decimal degrees.
event_id	Sequential event number within each gauge’s processed record. It is not globally unique.
event_start_time	Event start time converted to the gauge’s listed local time zone.
peak_time	Local time of maximum discharge during the event.
event_end_time	Local time of the final above-action-stage observation in the event.
event_start_time_utc	Event start time in UTC.
peak_time_utc	Time of maximum event discharge in UTC.
event_end_time_utc	Event end time in UTC.
action_stage_ft	Current NOAA/NWS action-stage threshold for the gauge, in feet.
peak_gage_height_ft	Maximum observed stage during the event, in feet.
peak_discharge_cfs	Maximum observed discharge during the event, in cubic feet per second.
rise_time_hours	Hours from the first action-stage exceedance to the time of maximum discharge.
duration_above_threshold_hours	Estimated total time stage remained above action stage. Observation intervals longer than six hours are capped at six hours in this calculation.
flood_severity	Paper-style severity: peak discharge divided by rise time. Units are approximately cfs per hour.
flood_severity_norm	flood_severity divided by drainage area. This provides a basin-size-normalized version of the paper-style severity.
severity_excess_vol_cfs_hr	Integrated discharge above the discharge observed at event onset. Units are cfs·hr.
severity_excess_depth_in	severity_excess_vol_cfs_hr converted to equivalent runoff depth over the drainage basin, in inches.
severity_stage_ft_hr	Integrated stage above the action-stage threshold. Units are ft·hr. It combines height above threshold and duration.
severity_pctl_vol_cfs_hr	Integrated discharge above the gauge’s 95th-percentile discharge. Units are cfs·hr.
severity_pctl_depth_in	The 95th-percentile excess volume normalized by drainage area and converted to inches of excess runoff.
peak_pctl	Percentile rank of the event’s peak discharge relative to all available instantaneous discharge observations at that gauge.
drainage_area_sqmi	Gauge drainage area in square miles, obtained from USGS monitoring-location metadata.
number_of_observations	Number of instantaneous observations included between the detected event start and end.
missing_data_fraction	Estimated fraction of observations missing within the event period, based on the median sampling interval.
provisional_fraction	Fraction of event discharge observations carrying provisional or estimated quality flags.
quality_flag	Event-quality warning. Possible flags include left_censored, right_censored, zero_rise_time, no_discharge, data_gap, and mostly_provisional; otherwise it is ok.
year	Calendar year of the event’s UTC start time.
flood_events_by_zip_year.csv:
The gauge events summarized to ZIP code by year. Each row is one ZIP in one year, reporting how many gauges it contains, how many flood events occurred, the maximum and mean severity that year, the worst peak discharge, and how far above action stage the worst event crested. One row = one ZIP-year.

Again, the column names' description are provided below:
Column	Explanation
zip	2022 ZCTA containing the gauge point. It is not necessarily a postal-service ZIP boundary.
year	Event-start year inherited from the gauge-level file.
n_gauges	Number of unique gauges in the ZCTA that had at least one detected event in that year.
n_events	Total number of gauge-event records in that ZCTA during that year.
max_severity_pctl_depth_in	Largest severity_pctl_depth_in among all events in the ZCTA-year.
mean_severity_pctl_depth_in	Mean severity_pctl_depth_in across all events in the ZCTA-year.
max_peak_pctl	Highest event peak-discharge percentile among all events in the ZCTA-year.
max_peak_discharge_cfs	Highest absolute peak discharge among all events and gauges in the ZCTA-year.
max_peak_stage_above_action_ft	Maximum difference between event peak stage and gauge action stage: peak_gage_height_ft − action_stage_ft.
gauge_list	Comma-separated list of unique USGS gauge IDs represented in that ZCTA-year.

Definitions:
Flood event: following the framework of Khajehei et al. (2020), a flood is defined as the interval during which observed streamgage stage exceeds the National Weather Service action stage for that gauge. The event begins at the first exceedance and ends when stage falls back below the threshold (with brief dips bridged so one flood isn't split into several).  
The main equations are provided below:
Severity: the paper defines severity as peak magnitude divided by flood rise time, where rise time is the hours from the initial action-stage exceedance to the peak. This measures how rapidly a flood builds.
This is the main severity index that can be used: 
Flood_Severity = Peak_Dsicharge_csf/Rise_time_hours

But there are other definitions that can be used as well:
flood_severity_norm: is the above definition divided by drainage area of the basin-area-normalized.
  Also, the dataset includes a complementary severity based on run theory — the excess flow integrated over the event, which equals intensity × duration and rises with both how high and how long a flood is:  
S = ∑max(Qi−Qthr,0)⋅Δti
Which is normalized by drainage area to inches of excess runoff (severity_pctl_depth_in) so it is comparable across gauges. The threshold Qthr is set at a high percentile of the gauge's own flow record.  

Other definitions from above are also provided here:
severity_excess_vol_cfs_hr :  Measures integrated flow above the discharge at event onset.
severity_excess_depth_in :    This is more comparable across differently sized basins than raw cfs·hr.
severity_stage_ft_hr  : Measures how far and how long stage remained above action stage. It does not require a discharge rating curve or drainage area.
severity_pctl_vol_cfs_hr :    Measures integrated flow above the gauge’s 95th-percentile discharge.
severity_pctl_depth_in :   Measures the same excess volume as equivalent runoff depth in inches.
Citations:

Khajehei, S., Ahmadalipour, A., Shao, W., & Moradkhani, H. (2020). A place-based assessment of flash flood hazard and vulnerability in the contiguous United States. Scientific Reports, 10, 448. https://doi.org/10.1038/s41598-019-57349-z

Yevjevich, V. (1967). An objective approach to definitions and investigations of continental hydrologic droughts. Hydrology Paper 23, Colorado State University. (Origin of the run-theory severity–duration–intensity framework.)