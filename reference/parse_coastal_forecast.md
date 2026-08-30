# Parse BOM Coastal Waters Forecast XML Files

Parse local BOM daily coastal waters forecast XML file(s) for a
specified state or territory or all of Australia.

## Usage

``` r
parse_coastal_forecast(state, filepath)
```

## Arguments

- state:

  Required value of an Australian state or territory as full name or
  postal code. Fuzzy string matching via
  [`base::agrep()`](https://rdrr.io/r/base/agrep.html) is done.

- filepath:

  A string providing the directory location of the coastal forecast
  file(s) to parse. See Details for more.

## Value

A
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
of an Australia BOM Coastal Waters Forecast.

## Details

Allowed state and territory postal codes, only one state per request or
all using `AUS`.

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

The `filepath` argument will only accept a directory where files are
located for parsing. DO NOT supply the full path including the file
name. This function will only parse the requested state or all of
Australia in the same fashion as
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
provided that the files are all present in the directory.

## References

Forecast data come from Australian Bureau of Meteorology (BOM) Weather
Data Services  
<https://www.bom.gov.au/catalogue/data-feeds.shtml>.

Location data and other metadata come from the BOM anonymous FTP server
with spatial data  
<ftp://ftp.bom.gov.au/anon/home/adfd/spatial/>, specifically the DBF
file portion of a shapefile,  
<ftp://ftp.bom.gov.au/anon/home/adfd/spatial/IDM00003.dbf>.

## See also

[get_coastal_forecast](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md)

Other BOM:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md),
[`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)

Other parse:
[`metno_get_dominant_symbol()`](https://docs.ropensci.org/weatherOz/reference/metno_get_dominant_symbol.md),
[`metno_resample_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_resample_data_table.md),
[`metno_timeseries_to_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_timeseries_to_data_table.md),
[`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)

## Author

Dean Marchiori, <deanmarchiori@gmail.com>, and Paul Melloy,
<paul@melloy.com.au>

## Examples

``` r
if (FALSE) { # interactive()
# parse the coastal forecast for Queensland

#download to tempfile() using basename() to keep original name
utils::download.file(url = "ftp://ftp.bom.gov.au/anon/gen/fwo/IDQ11290.xml",
              destfile = file.path(tempdir(),
              basename("ftp://ftp.bom.gov.au/anon/gen/fwo/IDQ11290.xml")),
              mode = "wb")

parse_coastal_forecast(state = "QLD", filepath = tempdir())
}
```
