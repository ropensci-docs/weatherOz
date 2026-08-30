# Get DPIRD Weather Data by the Minute

Fetch nicely formatted minute weather station data from the DPIRD
Weather 2.0 API for a maximum 24-hour period.

## Usage

``` r
get_dpird_minute(
  station_code,
  start_date_time = lubridate::now() - lubridate::hours(24L),
  minutes = 1440L,
  values = "all",
  api_key = get_key(service = "DPIRD")
)
```

## Arguments

- station_code:

  A `character` string or `factor` from
  [`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)
  of the BOM station code for the station of interest.

- start_date_time:

  A `character` string representing the start date and time of the query
  in the format “yyyy-mm-dd-hh-mm” (ISO8601). Defaults to 24 hours
  before the current local system time, returning the most recent 24
  hour observations rounded to the nearest minute. This function does
  its best to decipher many date and time formats but prefers ISO8601.

- minutes:

  An `integer` value that provides the number of observations to be
  returned. Defaults to 1440 minutes for 24 hours of observations.

- values:

  A `vector` of weather values to query from the API. See **Available
  Values** section for valid available codes. Defaults to all available
  values, `all`.

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
with `station_code` and the date interval queried together with the
requested weather variables.

## Note

Please note this function converts date-time columns from Coordinated
Universal Time ‘UTC’ returned by the API to Australian Western Standard
Time ‘AWST’.

## Available Values

- all (which will return all of the following values),

- airTemperature,

- dateTime,

- dewPoint,

- rainfall,

- relativeHumidity,

- soilTemperature,

- solarIrradiance,

- wetBulb,

- wind,

- windAvgSpeed,

- windMaxSpeed, and

- windMinSpeed

## See also

Other DPIRD:
[`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md),
[`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md),
[`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

## Author

Adam H. Sparks, <adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{

# Note that you need to supply your own API key

get_dpird_minute(
  station_code = "SP",
  start_date_time = "2023-02-01 13:00:00",
  minutes = 1440,
  values = c("airTemperature",
             "solarIrradiance",
             "wind"),
  api_key = "your_api_key"
)
} # }
```
