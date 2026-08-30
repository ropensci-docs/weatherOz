# Get a List of Available BOM Radar Imagery

Fetch a listing of available BOM radar imagery from
<ftp://ftp.bom.gov.au/anon/gen/radar/> to determine which files are
currently available for download. The files available are the most
recent radar imagery for each location, which are updated approximately
every 6 to 10 minutes by the BOM. Ported from bomrang.

## Usage

``` r
get_available_radar(radar_id = "all")
```

## Arguments

- radar_id:

  `Numeric`. BOM radar of interest for which a list of available images
  will be returned. Defaults to all images currently available.

## Value

A
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
of all selected radar locations with location information and
`product_ids`.

## Details

Valid BOM radar ID for each location required.

## References

Australian Bureau of Meteorology (BOM) radar image
<https://www.bom.gov.au/weather-and-climate/rain-radar-and-weather-maps>.

## See also

Other BOM:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md),
[`parse_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_coastal_forecast.md),
[`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)

Other metadata:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

## Author

Dean Marchiori, <deanmarchiori@gmail.com>, and Adam H. Sparks,
<adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # interactive()

# Check availability radar imagery for Wollongong (radar_id = 3)
imagery <- get_available_radar(radar_id = 3)

imagery
}
```
