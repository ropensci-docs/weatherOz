# Get DPIRD Summary Weather Data in the APSIM Format From the Weather 2.0 API

Automates the retrieval and conversion of summary data from the DPIRD
Weather 2.0 API to an APSIM .met file formatted weather data object.

## Usage

``` r
get_dpird_apsim(
  station_code,
  start_date,
  end_date = Sys.Date(),
  api_key = get_key(service = "DPIRD")
)
```

## Arguments

- station_code:

  A `character` string or `factor` from
  [`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)
  of the BOM station code for the station of interest.

- start_date:

  A `character` string or `Date` object representing the beginning of
  the range to query in the format “yyyy-mm-dd” (ISO8601). Data returned
  is inclusive of this date.

- end_date:

  A `character` string or `Date` object representing the end of the
  range query in the format “yyyy-mm-dd” (ISO8601). Data returned is
  inclusive of this date. Defaults to the current system date.

- api_key:

  A `character` string containing your API key from DPIRD,
  <https://www.dpird.wa.gov.au/online-tools/apis/>, for the DPIRD
  Weather 2.0 API. Defaults to automatically detecting your key from
  your local .Renviron, .Rprofile or similar. Alternatively, you may
  directly provide your key as a string here. If nothing is provided,
  you will be prompted on how to set up your R session so that it is
  auto-detected.

## Value

An [apsimx](https://CRAN.R-project.org/package=apsimx) object of class
‘met’ with attributes.

## Saving objects

To save “met” objects the
[`apsimx::write_apsim_met()`](https://rdrr.io/pkg/apsimx/man/write_apsim_met.html)
is reexported. Note that when saving, comments from SILO will be
included, but these will not be printed as a part of the resulting `met`
object in your R session.

## See also

Other DPIRD:
[`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md),
[`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md),
[`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

Other APSIM:
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
`reexports`

## Author

Adam H. Sparks, <adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# Get an APSIM format object for Binnu
# Note that you need to supply your own API key

wd <- get_dpird_apsim(
  station_code = "BI",
  start_date = "20220101",
  end_date = "20221231",
  api_key = "your_api_key"
)
} # }

```
