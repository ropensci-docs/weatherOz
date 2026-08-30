# Get DataDrill Weather Data in the APSIM Format From SILO

Fetch APSIM .met file formatted weather data from the weather data from
the SILO API of spatially interpolated weather data (DataDrill). The
daily climate surfaces have been derived either by splining or kriging
the observational data. The returned values contain “source” columns,
which denote how the observations were derived. The grid spans 112° to
154°, -10° to -44° with resolution 0.05° latitude by 0.05° longitude
(approximately 5 km × 5 km).

## Usage

``` r
get_data_drill_apsim(
  longitude,
  latitude,
  start_date,
  end_date = Sys.Date(),
  api_key = get_key(service = "SILO")
)
```

## Arguments

- longitude:

  A single `numeric` value representing the longitude of the
  point-of-interest.

- latitude:

  A single `numeric` value representing the latitude of the
  point-of-interest.

- start_date:

  A `character` string or `Date` object representing the beginning of
  the range to query in the format “yyyy-mm-dd” (ISO8601). Data returned
  is inclusive of this date.

- end_date:

  A `character` string or `Date` object representing the end of the
  range query in the format “yyyy-mm-dd” (ISO8601). Data returned is
  inclusive of this date. Defaults to the current system date.

- api_key:

  A `character` string containing your API key, an e-mail address, for
  the request. Defaults to automatically detecting your key from your
  local .Renviron, .Rprofile or similar. Alternatively, you may directly
  provide your key as a string here. If nothing is provided, you will be
  prompted on how to set up your R session so that it is auto-detected.

## Value

An [apsimx](https://CRAN.R-project.org/package=apsimx) object of class
‘met’ with attributes.

## Details

Note that when saving, comments from SILO will be included, but these
will not be printed as a part of the resulting `met` object in your R
session.

## Included Values

- rain (mm):

  Rainfall

- maxt (degrees C):

  Maximum temperature

- mint (degrees C):

  Minimum temperature

- vp (hPa):

  Vapour pressure

- evap_pan (mm):

  Class A pan evaporation

- radiation (Mj/m¹):

  Solar exposure, consisting of both direct and diffuse components

## Value information

Solar radiation: total incoming downward shortwave radiation on a
horizontal surface, derived from estimates of cloud oktas and sunshine
duration².

Evaporation and evapotranspiration: an overview of the variables
provided by SILO is available here,
<https://data.longpaddock.qld.gov.au/static/publications/Evapotranspiration_overview.pdf>.

## Data codes

Where the source code is a 6 digit string comprising the source code for
the 6 variables. The single digit code for each variable is:

- 0:

  an actual observation;

- 1:

  an actual observation from a composite station;

- 2:

  a value interpolated from daily observations;

- 3:

  a value interpolated from daily observations using the anomaly
  interpolation method for CLIMARC data;

- 6:

  a synthetic pan value; or

- 7:

  an interpolated long term average.

## Saving objects

To save “met” objects the
[`apsimx::write_apsim_met()`](https://rdrr.io/pkg/apsimx/man/write_apsim_met.html)
is reexported. Note that when saving, comments from SILO will be
included, but these will not be printed as a part of the resulting `met`
object in your R session.

## References

1.  Rayner, D. (2005). Australian synthetic daily Class A pan
    evaporation. Technical Report December 2005, Queensland Department
    of Natural Resources and Mines, Indooroopilly, Qld., Australia, 40
    pp.

2.  Morton, F. I. (1983). Operational estimates of areal
    evapotranspiration and their significance to the science and
    practice of hydrology, *Journal of Hydrology*, Volume 66, 1-76.

## See also

Other SILO:
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md),
[`silo_daily_values`](https://docs.ropensci.org/weatherOz/reference/silo_daily_values.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
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
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
`reexports`

## Author

Rodrigo Pires, <rodrigo.pires@dpird.wa.gov.au>, and Adam Sparks,
<adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# requires an API key as your email address
# Source data from latitude and longitude coordinates (gridded data) for
# max and minimum temperature and rainfall for Southwood, QLD.
wd <- get_data_drill_apsim(
  latitude = -27.85,
  longitude = 150.05,
  start_date = "20220101",
  end_date = "20221231",
  api_key = "your_api_key"
)
} # }
```
