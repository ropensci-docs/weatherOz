# Get a List of Available BOM Satellite Imagery

Fetch a listing of BOM GeoTIFF satellite imagery from
<ftp://ftp.bom.gov.au/anon/gen/gms/> to determine which files are
currently available for download. Files are available at ten minute
update frequency with a 24-hour delete time. It is useful to know the
most recent files available and then specify in the
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)
function. Ported from
[bomrang](https://CRAN.R-project.org/package=bomrang).

## Usage

``` r
get_available_imagery(product_id = "all")
```

## Arguments

- product_id:

  `Character`. BOM product ID of interest for which a list of available
  images will be returned. Defaults to all images currently available.

## Value

A `vector` of all available files for the requested Product ID(s).

## Details

Valid BOM satellite Product IDs for GeoTIFF files include:

- IDE00420:

  AHI cloud cover only 2km FD GEOS GIS

- IDE00421:

  AHI IR (Ch13) greyscale 2km FD GEOS GIS

- IDE00422:

  AHI VIS (Ch3) greyscale 2km FD GEOS GIS

- IDE00423:

  AHI IR (Ch13) Zehr 2km FD GEOS GIS

- IDE00425:

  AHI VIS (true colour) / IR (Ch13 greyscale) composite 1km FD GEOS GIS

- IDE00426:

  AHI VIS (true colour) / IR (Ch13 greyscale) composite 2km FD GEOS GIS

- IDE00427:

  AHI WV (Ch8) 2km FD GEOS GIS

- IDE00430:

  AHI cloud cover only 2km AUS equirect. GIS

- IDE00431:

  AHI IR (Ch13) greyscale 2km AUS equirect. GIS

- IDE00432:

  AHI VIS (Ch3) greyscale 2km AUS equirect. GIS

- IDE00433:

  AHI IR (Ch13) Zehr 2km AUS equirect. GIS

- IDE00435:

  AHI VIS (true colour) / IR (Ch13 greyscale) composite 1km AUS
  equirect. GIS

- IDE00436:

  AHI VIS (true colour) / IR (Ch13 greyscale) composite 2km AUS
  equirect. GIS

- IDE00437:

  AHI WV (Ch8) 2km AUS equirect. GIS

- IDE00439:

  AHI VIS (Ch3) greyscale 0.5km AUS equirect. GIS

## References

Australian Bureau of Meteorology (BOM) high-definition satellite images
<https://www.bom.gov.au/australia/satellite/index.shtml>

## See also

Other BOM:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
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
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

## Author

Adam H. Sparks, <adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # interactive()
# Check availability of AHI VIS (true colour) / IR (Ch13 greyscale) composite
# 1km FD GEOS GIS images
imagery <- get_available_imagery(product_id = "IDE00425")

imagery
}
```
