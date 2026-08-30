# Get DataDrill Weather Data From SILO

Fetch nicely formatted weather data from the SILO API of spatially
interpolated weather data (DataDrill). The daily climate surfaces have
been derived either by splining or kriging the observational data. The
returned values contain “source” columns, which denote how the
observations were derived. The grid spans 112° to 154°, -10° to -44°
with resolution 0.05° latitude by 0.05° longitude (approximately 5 km ×
5 km).

## Usage

``` r
get_data_drill(
  longitude,
  latitude,
  start_date,
  end_date = Sys.Date(),
  values = "all",
  api_key = get_key(service = "SILO")
)
```

## Arguments

- longitude:

  A single `numeric` value representing the longitude of the
  point-of-interest to the hundredths (*e.g.*, 0.05) of a degree.

- latitude:

  A single `numeric` value representing the latitude of the
  point-of-interest to the hundredths (*e.g.*., 0.05) of a degree.

- start_date:

  A `character` string or `Date` object representing the beginning of
  the range to query in the format “yyyy-mm-dd” (ISO8601). Data returned
  is inclusive of this date.

- end_date:

  A `character` string or `Date` object representing the end of the
  range query in the format “yyyy-mm-dd” (ISO8601). Data returned is
  inclusive of this date. Defaults to the current system date.

- values:

  A `character` string with the type of weather data to return. See
  **Available Values** for a full list of valid values. Defaults to
  `all` with all available values being returned.

- api_key:

  A `character` string containing your API key, an e-mail address, for
  the request. Defaults to automatically detecting your key from your
  local .Renviron, .Rprofile or similar. Alternatively, you may directly
  provide your key as a string here. If nothing is provided, you will be
  prompted on how to set up your R session so that it is auto-detected.

## Value

a
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
with the weather data queried with the weather variables in alphabetical
order. The first eight columns will always be:

- `longitude`,

- `latitude`,

- `elev_m` (elevation in metres),

- `date` (ISO8601 format, YYYYMMDD),

- `year`,

- `month`,

- `day`,

- `extracted` (the date on which the query was made)

## Column Name Details

Column names are converted from the default returns of the API to be
snake_case formatted and where appropriate, the names of the values that
are analogous between SILO and DPIRD data are named using the same name
for ease of interoperability, *e.g.*, using
[`rbind()`](https://rdrr.io/r/base/cbind.html) to create a `data.table`
that contains data from both APIs.

## Available Values

- all:

  Which will return all of the following values

- rain (mm):

  Rainfall

- max_temp (degrees C):

  Maximum temperature

- min_temp (degrees C):

  Minimum temperature

- vp (hPa):

  Vapour pressure

- vp_deficit (hPa):

  Vapour pressure deficit

- evap_pan (mm):

  Class A pan evaporation

- evap_syn (mm):

  Synthetic estimate¹

- evap_comb (mm):

  Combination (synthetic estimate pre-1970, class A pan 1970 onwards)

- evap_morton_lake (mm):

  Morton's shallow lake evaporation

- radiation (Mj/m²):

  Solar exposure, consisting of both direct and diffuse components

- rh_tmax (%):

  Relative humidity at the time of maximum temperature

- rh_tmin (%):

  Relative humidity at the time of minimum temperature

- et_short_crop (mm):

  FAO56⁴ short crop

- et_tall_crop (mm):

  ASCE⁵ tall crop⁶

- et_morton_actual (mm):

  Morton's areal actual evapotranspiration

- et_morton_potential (mm):

  Morton's point potential evapotranspiration

- et_morton_wet (mm):

  Morton's wet-environment areal potential evapotranspiration over land

- mslp (hPa):

  Mean sea level pressure

## Value information

Solar radiation: total incoming downward shortwave radiation on a
horizontal surface, derived from estimates of cloud oktas and sunshine
duration³.

Relative humidity: calculated using the vapour pressure measured at 9am,
and the saturation vapour pressure computed using either the maximum or
minimum temperature⁶.

Evaporation and evapotranspiration: an overview of the variables
provided by SILO is available here,
<https://data.longpaddock.qld.gov.au/static/publications/Evapotranspiration_overview.pdf>.

## Data codes

Data codes Where possible (depending on the file format), the data are
supplied with codes indicating how each datum was obtained.

- 0:

  Official observation as supplied by the Bureau of Meteorology

- 15:

  Deaccumulated rainfall (original observation was recorded over a
  period exceeding the standard 24 hour observation period)

- 25:

  Interpolated from daily observations for that date

- 26:

  Synthetic Class A pan evaporation, calculated from temperatures,
  radiation and vapour pressure

- 35:

  Interpolated from daily observations using an anomaly interpolation
  method

- 75:

  Interpolated from the long term averages of daily observations for
  that day of year

## References

1.  Rayner, D. (2005). Australian synthetic daily Class A pan
    evaporation. Technical Report December 2005, Queensland Department
    of Natural Resources and Mines, Indooroopilly, Qld., Australia, 40
    pp.

2.  Morton, F. I. (1983). Operational estimates of areal
    evapotranspiration and their significance to the science and
    practice of hydrology, *Journal of Hydrology*, Volume 66, 1-76.

3.  Zajaczkowski, J., Wong, K., & Carter, J. (2013). Improved historical
    solar radiation gridded data for Australia, *Environmental Modelling
    & Software*, Volume 49, 64–77. DOI:
    [doi:10.1016/j.envsoft.2013.06.013](https://doi.org/10.1016/j.envsoft.2013.06.013)
    .

4.  Food and Agriculture Organization of the United Nations, Irrigation
    and drainage paper 56: Crop evapotranspiration - Guidelines for
    computing crop water requirements, 1998.

5.  ASCE’s Standardized Reference Evapotranspiration Equation,
    proceedings of the National Irrigation Symposium, Phoenix, Arizona,
    2000.

6.  For further details refer to Jeffrey, S.J., Carter, J.O., Moodie,
    K.B. and Beswick, A.R. (2001). Using spatial interpolation to
    construct a comprehensive archive of Australian climate data,
    *Environmental Modelling and Software*, Volume 16/4, 309-330. DOI:
    [doi:10.1016/S1364-8152(01)00008-1](https://doi.org/10.1016/S1364-8152%2801%2900008-1)
    .

## See also

Other SILO:
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md),
[`silo_daily_values`](https://docs.ropensci.org/weatherOz/reference/silo_daily_values.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
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
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

## Author

Rodrigo Pires, <rodrigo.pires@dpird.wa.gov.au>, and Adam H. Sparks,
<adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# requires an API key as your email address
# Source data from latitude and longitude coordinates (gridded data) for
# max and minimum temperature and rainfall for Southwood, QLD.
wd <- get_data_drill(
  latitude = -27.85,
  longitude = 150.05,
  start_date = "20221001",
  end_date = "20221201",
  values = c("max_temp", "min_temp", "rain"),
  api_key = "your_api_key"
)
} # }
```
