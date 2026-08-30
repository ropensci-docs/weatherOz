# Get Weather Forecast Data from MET Weather API

Retrieves weather forecast data from the Norwegian Meteorological
Institute locationforecast API and returns the parsed metadata together
with a tidy hourly `data.table`. The response headers `Expires` and
`Last-Modified` are provided both in their raw RFC 1123 form and parsed
to `POSIXct` for downstream logic.

## Usage

``` r
get_metno_forecast(
  latitude,
  longitude,
  format = c("compact", "complete"),
  api_key = get_key(service = "METNO"),
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

  Numeric. Latitude in decimal degrees for the forecast location. Must
  be within Australian limits (-44 to -10).

- longitude:

  Numeric. Longitude in decimal degrees for the forecast location. Must
  be within Australian limits (112 to 154).

- format:

  Character. Either `"compact"` (default) or `"complete"` for the MET
  Weather API locationforecast endpoint variant.

- api_key:

  Character. Email address required for the User-Agent header in
  accordance with MET Weather API terms of service.

- timeout:

  Numeric. Request timeout in seconds (default: 30).

- max_retries:

  Integer. Maximum number of retry attempts on transient failures
  (default: 3).

- retry_delay:

  Numeric. Base delay between retries in seconds for exponential backoff
  (default: 1).

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

A named list with elements:

- `data`:

  Hourly forecast as a `data.table`.

- `raw`:

  The full parsed GeoJSON response (list).

- `metadata`:

  A list containing request parameters, status code, retrieval
  timestamp, header information (`expires_raw`, `expires`,
  `last_modified_raw`, `last_modified`), and cache provenance in
  `metadata$cache`.

## See also

Other METNO:
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
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
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
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
forecast <- get_metno_forecast(
  latitude = -31.95,
  longitude = 115.86,
  api_key = "your.email@example.com"
)
forecast$metadata$expires
utils::head(forecast$data)
} # }
```
