# Get BOM Radar Imagery

Fetch BOM radar imagery from <ftp://ftp.bom.gov.au/anon/gen/radar/> and
return a [magick](https://CRAN.R-project.org/package=magick) image
object. Files available are the most recent radar snapshot which are
updated approximately every 6 to 10 minutes. It is suggested to check
file availability first by using
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md).

## Usage

``` r
get_radar_imagery(product_id, path = NULL, download_only = FALSE)
```

## Arguments

- product_id:

  `Character`. BOM product ID to download and import. Value is required.

- path:

  `Character`. A character string with the name where the downloaded
  file is saved. If not provided, the default value `NULL` is used which
  saves the file in an R session temp directory.

- download_only:

  `Boolean`. Whether the radar image is loaded into the environment as a
  [magick](https://CRAN.R-project.org/package=magick) object or just
  downloaded. Defaults to `FALSE`

## Value

A [magick](https://CRAN.R-project.org/package=magick) object of the most
recent radar image snapshot published by the BOM. If
`download_only = TRUE` there will be a `NULL` return value with the
download path printed in the console as a message.

## Details

Valid BOM Radar Product IDs for radar imagery can be obtained from
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md).

## References

Australian Bureau of Meteorology (BOM) radar images  
<https://www.bom.gov.au/weather-and-climate/rain-radar-and-weather-maps>

## See also

[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md)

Other BOM:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md),
[`parse_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_coastal_forecast.md),
[`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

## Author

Dean Marchiori, <deanmarchiori@gmail.com>

## Examples

``` r
if (FALSE) { # interactive()

# Fetch most recent radar image for Wollongong 256km radar
imagery <- get_radar_imagery(product_id = "IDR032")
imagery
}
```
