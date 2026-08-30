# Get a BOM Coastal Waters Forecast

Fetch the BOM daily Coastal Waters Forecast for a specified state or
region.

## Usage

``` r
get_coastal_forecast(state = "AUS")
```

## Arguments

- state:

  Australian state or territory as full name or postal code. Fuzzy
  string matching via
  [`base::agrep()`](https://rdrr.io/r/base/agrep.html) is done. Defaults
  to `AUS` returning all state forecasts, see details for further
  information.

## Value

A
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
of an Australia BOM Coastal Waters Forecast.

## Details

Allowed state and territory postal codes, only one state per request or
all using 'AUS':

- AUS:

  Australia, returns forecast for all states, NT and ACT

- ACT:

  Australian Capital Territory (will return NSW)

- NSW:

  New South Wales

- NT:

  Northern Territory

- QLD:

  Queensland

- SA:

  South Australia

- TAS:

  Tasmania

- VIC:

  Victoria

- WA:

  Western Australia

## References

Forecast data come from Australian Bureau of Meteorology (BOM) Weather
Data Services  
<https://www.bom.gov.au/catalogue/data-feeds.shtml>.

And also,

Location data and other metadata come from the BOM anonymous FTP server
with spatial data  
<ftp://ftp.bom.gov.au/anon/home/adfd/spatial/>, specifically the DBF
file portion of a shapefile,  
<ftp://ftp.bom.gov.au/anon/home/adfd/spatial/IDM00003.dbf>.

## See also

[parse_coastal_forecast](https://docs.ropensci.org/weatherOz/reference/parse_coastal_forecast.md)

Other BOM:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md),
[`parse_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_coastal_forecast.md),
[`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)

Other data fetching:
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
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

## Author

Dean Marchiori, <deanmarchiori@gmail.com>, and Paul Melloy,
<paul@melloy.com.au>

## Examples

``` r
if (FALSE) { # interactive()

get_coastal_forecast(state = "NSW")
}
```
