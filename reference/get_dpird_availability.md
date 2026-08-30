# Get the Availability for DPIRD Weather Stations

Fetch the availability metadata of weather stations in the DPIRD weather
station network from the Weather 2.0 API.

## Usage

``` r
get_dpird_availability(
  station_code = NULL,
  start_date = NULL,
  end_date = NULL,
  values = "availability",
  api_key = get_key(service = "DPIRD")
)
```

## Arguments

- station_code:

  A `character` string of the DPIRD station code for the station of
  interest. Defaults to `NULL`, returning metadata for all stations
  during the requested `start_date` and `end_date` interval.

- start_date:

  A `character` string representing the beginning of the range to query
  in the format “yyyy-mm-dd” (ISO8601). This function will return data
  inclusive of this date. Defaults to `NULL`, returning data for the
  current year-to-date. Must be sent along with an `end_date`.

- end_date:

  A `character` string representing the end of the range query in the
  format “yyyy-mm-dd” (ISO8601). This function will return data
  inclusive of this date. Defaults to `NULL`, returning data for the
  current year-to-date. Must be sent with a `start_date`.

- values:

  A `character` string with the type of availability metadata to return.
  See **Available Values** for a full list of valid values. Defaults to
  `availability`, returning metadata for all stations.

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
with `station_code` and the requested metadata.

## Available Values

- availability (which will return all of the following values),

- availabilityCurrentHour,

- availabilityLast7DaysSince9AM,

- availabilityLast7DaysSince12AM,

- availabilityLast14DaysSince9AM,

- availabilityLast14DaysSince12AM,

- availabilityLast24Hours,

- availabilityMonthToDateSince12AM,

- availabilityMonthToDateTo9AM,

- availabilitySince9AM,

- availabilitySince12AM,

- availabilityTo9AM,

- availabilityYearToDateSince12AM, and

- availabilityYearToDateTo9AM

## See also

Other DPIRD:
[`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md),
[`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md),
[`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

Other metadata:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

## Author

Adam H. Sparks, <adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# Note that you need to supply your own API key

# Here we check the up time for the current year for Westonia
WS001 <- get_dpird_availability(station_code = "WS001",
                                api_key = "your_api_key")

# Here we check the up time for 2017 for Binnu
BN <- get_dpird_availability(
  station_code = "BI",
  start_date = "20170101",
  end_date = "20171231",
  api_key = "your_api_key"
)
} # }
```
