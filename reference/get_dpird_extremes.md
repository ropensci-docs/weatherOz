# Get DPIRD Extreme Weather Event Summaries

Fetch nicely formatted individual extreme weather summaries from the
DPIRD Weather 2.0 API.

## Usage

``` r
get_dpird_extremes(
  station_code,
  values = "all",
  api_key = get_key(service = "DPIRD")
)
```

## Arguments

- station_code:

  A `character` string or `factor` from
  [`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)
  of the BOM station code for the station of interest.

- values:

  A `character` string with the type of extreme weather to return. See
  **Available Values** for a full list of valid values. Defaults to
  `all`, returning the full list of values unless otherwise specified.

- api_key:

  A `character` string containing your API key from DPIRD,
  <https://www.dpird.wa.gov.au/online-tools/apis/>, for the DPIRD
  Weather 2.0 API. Defaults to automatically detecting your key from
  your local .Renviron, .Rprofile or similar. Alternatively, you may
  directly provide your key as a string here. If nothing is provided,
  you will be prompted on how to set up your R session so that it is
  auto-detected.

## Value

a
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
of one row with `station_code`, `station_name`, `latitude`, `longitude`,
`date_time` of the query and the extreme weather information according
to the value(s) selected.

## Available Values

- all (which will return all of the following values),

- erosionCondition,

- erosionConditionLast7Days,

- erosionConditionLast7DaysDays,

- erosionConditionLast7DaysMinutes,

- erosionConditionLast14Days,

- erosionConditionLast14DaysDays,

- erosionConditionLast14DaysMinutes,

- erosionConditionMonthToDate,

- erosionConditionMonthToDateDays,

- erosionConditionMonthToDateMinutes,

- erosionConditionMonthToDateStartTime,

- erosionConditionSince12AM,

- erosionConditionSince12AMMinutes,

- erosionConditionSince12AMStartTime,

- erosionConditionYearToDate,

- erosionConditionYearToDateDays,

- erosionConditionYearToDateMinutes,

- erosionConditionYearToDateStartTime,

- frostCondition,

- frostConditionLast7Days,

- frostConditionLast7DaysDays,

- frostConditionLast7DaysMinutes,

- frostConditionLast14Days,

- frostConditionLast14DaysDays,

- frostConditionLast14DaysMinutes,

- frostConditionMonthToDate,

- frostConditionMonthToDateDays,

- frostConditionMonthToDateMinutes,

- frostConditionMonthToDateStartTime,

- frostConditionSince9AM,

- frostConditionSince9AMMinutes,

- frostConditionSince9AMStartTime,

- frostConditionTo9AM,

- frostConditionTo9AMMinutes,

- frostConditionTo9AMStartTime,

- frostConditionYearToDate,

- frostConditionYearToDate,

- frostConditionYearToDateMinutes,

- frostConditionYearToDateStartTime,

- heatCondition,

- heatConditionLast7Days,

- heatConditionLast7DaysDays,

- heatConditionLast7DaysMinutes,

- heatConditionLast14Days,

- heatConditionLast14DaysDays,

- heatConditionLast14DaysMinutes,

- heatConditionMonthToDate,

- heatConditionMonthToDateDays,

- heatConditionMonthToDateMinutes,

- heatConditionMonthToDateStartTime,

- heatConditionSince12AM,

- heatConditionSince12AMMinutes,

- heatConditionSince12AMStartTime,

- heatConditionYearToDate,

- heatConditionYearToDateDays,

- heatConditionYearToDateMinutes, and

- heatConditionYearToDateStartTime

## See also

Other DPIRD:
[`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md),
[`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md),
[`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

## Author

Rodrigo Pires, <rodrigo.pires@dpird.wa.gov.au>, and Adam Sparks,
<adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# Query Bonnie Rock station for wind erosion and heat extreme events
# Note that you need to supply your own API key

xtreme <- get_dpird_extremes(
  station_code = "BR",
  values = c("erosionCondition",
           "heatCondition"),
  api_key = "your_api_key"
)
} # }
```
