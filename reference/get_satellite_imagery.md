# Get BOM Satellite Imagery

Fetch BOM satellite GeoTIFF imagery from
<ftp://ftp.bom.gov.au/anon/gen/gms/> and return a
[terra](https://CRAN.R-project.org/package=terra) `SpatRaster` S4 class
(see `[terra::rast()]`) or
[stars](https://CRAN.R-project.org/package=stars) S3 `stars` object of
GeoTIFF files. Files are available at ten minutes update frequency with
a 24-hour delete time. It is suggested to check file availability first
by using
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md).
Ported from [bomrang](https://CRAN.R-project.org/package=bomrang) with
modifications.

## Usage

``` r
get_satellite_imagery(product_id, scans = 1, compat = "terra")
```

## Arguments

- product_id:

  `Character`. BOM product ID to download and import as a
  [terra](https://CRAN.R-project.org/package=terra) `SpatRaster` S4
  class (see `[terra::rast()]`) or
  [stars](https://CRAN.R-project.org/package=stars) S3 `stars` class
  object. A vector of values from
  [`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md)
  may be used here. Value is required.

- scans:

  `Integer`. Number of scans to download, starting with most recent and
  progressing backwards, *e.g.*, 1 - the most recent single scan
  available , 6 - the most recent hour available, 12 - the most recent 2
  hours available, etc. Negating will return the oldest files first.
  Defaults to 1. Value is optional.

- compat:

  `Character`. A string indicating the R package with which the returned
  imagery should be formatted for use, one of `terra` or `stars`.
  Defaults to `terra`.

## Value

A [terra](https://CRAN.R-project.org/package=terra) `SpatRaster` S4
class (see `[terra::rast()]`) or
[stars](https://CRAN.R-project.org/package=stars) S3 `stars` class
object as selected by the user by specifying `compat` of GeoTIFF images
with layers named by BOM product ID, timestamp and band.

## Details

Valid BOM satellite Product IDs for use with `product_id` include:

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

## Note

The original [bomrang](https://CRAN.R-project.org/package=bomrang)
version of this function supported local file caching using
[hoardr](https://CRAN.R-project.org/package=hoardr). This version does
not support this functionality any longer due to issues with CRAN and
[hoardr](https://CRAN.R-project.org/package=hoardr).

## References

Australian Bureau of Meteorology (BOM) high-definition satellite
images  
<https://www.bom.gov.au/australia/satellite/index.shtml>.

## See also

[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md)

Other BOM:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
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
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md)

## Author

Adam H. Sparks, <adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # interactive()
# Fetch AHI VIS (true colour) / IR (Ch13 greyscale) composite 1km FD
# GEOS GIS {terra} `SpatRaster`` object for most recent single scan
 available

imagery <- get_satellite_imagery(product_id = "IDE00425", scans = 1)
plot(imagery)

# Get a list of available image files and use that to specify files for
# download, downloading the two most recent files available

avail <- get_available_imagery(product_id = "IDE00425")
imagery <- get_satellite_imagery(product_id = avail, scans = 2)
plot(imagery)
}
```
