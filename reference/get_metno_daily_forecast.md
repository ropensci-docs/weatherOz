# Get Daily Weather Forecast Data from MET Weather API

Retrieves daily aggregated weather forecast data from the Norwegian
Meteorological Institute (MET.NO) locationforecast API. This is a
convenience function that wraps `get_metno_forecast` and aggregates the
hourly forecast data into daily summaries.

## Usage

``` r
get_metno_daily_forecast(
  latitude,
  longitude,
  days = 9,
  api_key,
  timeout = 30,
  max_retries = 3,
  retry_delay = 1,
  use_cache = TRUE,
  cache_dir = NULL,
  allow_stale_on_error = TRUE
)
```

## Arguments

- latitude:

  Numeric. The latitude in decimal degrees for the forecast location.
  Must be within Australian limits (-44 to -10).

- longitude:

  Numeric. The longitude in decimal degrees for the forecast location.
  Must be within Australian limits (112 to 154).

- days:

  Numeric. The number of forecast days to return (1-9, default: 9).

- api_key:

  Character. Your email address, required for the User-Agent header as
  per MET Weather API terms of service.

- timeout:

  Numeric. Request timeout in seconds (default: 30).

- max_retries:

  Numeric. Maximum number of retry attempts for failed requests
  (default: 3).

- retry_delay:

  Numeric. Base delay between retries in seconds (default: 1.0).

- use_cache:

  Logical. Use session-scoped cache and conditional revalidation for
  MET.NO responses. Defaults to `TRUE`.

- cache_dir:

  Character. Optional directory path for cache files. If `NULL`
  (default), uses `file.path(tempdir(), "metno_cache")`.

- allow_stale_on_error:

  Logical. If `TRUE` (default), return stale cached data when MET.NO
  returns HTTP 429 (rate limit exceeded) and stale cache is available.

## Value

A `data.table` with daily aggregated weather forecasts, including:
`date`, `min_temperature`, `max_temperature`, `total_precipitation`,
`avg_wind_speed`, `max_wind_speed`, `avg_relative_humidity`,
`avg_pressure`, `avg_cloud_fraction`, and `dominant_weather_symbol`.

## Details

The `latitude` and `longitude` are truncated to 4 decimal places as per
MET Weather API Terms of Service. The daily aggregation includes minimum
and maximum temperatures, total precipitation, average and maximum wind
speeds, average relative humidity, average air pressure, average cloud
fraction, and a dominant weather symbol for the day.

## See also

Other METNO:
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`metno_get_dominant_symbol()`](https://docs.ropensci.org/weatherOz/reference/metno_get_dominant_symbol.md),
[`metno_resample_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_resample_data_table.md),
[`metno_timeseries_to_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_timeseries_to_data_table.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

## Author

Rodrigo Pires, <rodrigo.pires@dpird.wa.gov.au>

## Examples

``` r
if (FALSE) { # \dontrun{
# Example of how to use the function (replace with your actual email)
# daily_forecast <- get_metno_daily_forecast(
#   latitude = -27.5,
#   longitude = 153.0,
#   days = 7,
#   api_key = "your.email@example.com"
# )
# print(daily_forecast)
} # }
```
