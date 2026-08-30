# Get Weather Station Metadata for Both DPIRD and SILO Weather Stations

Download the latest station locations and metadata for stations in the
SILO and DPIRD networks. For BOM stations that exist in SILO, but lack
metadata from BOM, the rows will exist to indicate that the station is
in the SILO data set, but there is no corresponding BOM metadata
available.

## Usage

``` r
get_stations_metadata(
  station_code = NULL,
  station_name = NULL,
  which_api = "all",
  api_key = NULL,
  include_closed = FALSE,
  rich = FALSE
)
```

## Arguments

- station_code:

  An optional value that should be provided as a single `string` value
  or character `vector` of station codes for which to return metadata.
  If this or `station_name` are not provided, all station metadata is
  returned by default. If this and `station_name` are both provided,
  this takes precedence and values corresponding to this input will be
  returned.

- station_name:

  An optional value that should be provided as either a single `string`
  or character `vector` of station names for which to return metadata.
  Fuzzy matching is used, *e.g.*, using `c("brisbane", "melbourne")`
  will return rows for “Brisbane”, “Brisbane Aero”, “Mt Brisbane”, “City
  of Melbourne Bay”, “Selbourne Kirnbrae”, “Maroondah Weir Melbourne
  Water”, “Melbourne Airport” and “Melbourne Botanical Gardens”
  `station_name` values. If this or `station_code` are not provided, all
  station metadata is returned by default. Using `station_code` will
  always override this argument if both are provided.

- which_api:

  A `string` value that indicates which API to use. Valid values are
  `all`, for both SILO (BOM data) and DPIRD APIs; `silo` for only
  stations from the SILO API (BOM data); or `dpird` for stations from
  the DPIRD Weather 2.0 API. Defaults to `all`.

- api_key:

  A `character` string containing your API key from DPIRD,
  <https://www.dpird.wa.gov.au/online-tools/apis/>, for the DPIRD
  Weather 2.0 API. If left as `NULL`, defaults to automatically
  detecting your key from your local .Renviron, .Rprofile or similar.
  Alternatively, you may directly provide your key as a string here. If
  nothing is provided, you will be prompted on how to set up your R
  session so that it is auto-detected. Only used when `which_api` is
  `DPIRD` or `all`.

- include_closed:

  A `Boolean` string indicating whether to include closed stations'
  metadata. Use `TRUE` to include these. Defaults to `FALSE`.

- rich:

  A `Boolean` string indicating whether to return rich information about
  DPIRD's weather station(s), this does not affect the SILO stations'
  metadata, the variables for these observations will be `NA`. Defaults
  to `FALSE`.

## Value

A
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
of BOM weather stations' metadata for stations available from SILO and
weather stations' metadata for stations available from DPIRD's Weather
2.0 API with the following columns sorted by `state` and `station_name`.

|  |  |
|----|----|
| **station_code**: | Unique station code. `factor` |
| **station_name**: | Unique station name. `character` |
| **start**: | Date observations start. `date` |
| **end**: | Date observations end. `date` |
| **latitude**: | Latitude in decimal degrees. `numeric` |
| **longitude**: | Longitude in decimal degrees. `numeric` |
| **state**: | State in which the station is located. `character` |
| **elev_m**: | Station elevation in metres. `numeric` |
| **source**: | Organisation responsible for the data or station maintenance. `character` |
| **include_closed**: | Station include_closed, one of ‘open’ or ‘closed’. `character` |
| **wmo**: | World Meteorological Organisation, (WMO), number if applicable. `numeric` |
| **`rich` values** |  |
| **capabilities**: | a list of the station's capabilities (data that it records). `character` |
| **probe_height**: | temperature probe height in metres. `double` |
| **rain_gauge_height** | rain gauge height in metres. `double` |
| **wind_probe_heights**: | wind probe heights always 3 metres, although some have 10 metre probes. `integer` |

## Note

For stations in the SILO API, BOM does not report the exact date on
which stations opened or closed, only the year. Therefore the `start`
and `end` columns will indicate January 1 of the year that a station
opened or closed, whereas stations in the DPIRD network have the date to
the day. For BOM stations that are closed for the current year, this
indicates that the station closed sometime during the current year prior
to the request being made. `NA` in the current year indicates a station
is still open.

There are discrepancies between the BOM's official station metadata,
*e.g.* longitude and latitude values and SILO metadata. In these cases,
the BOM metadata is used as it is considered to be the authority on the
stations' locations.

The station names are returned by both APIs in full caps. For purposes
of cleaner graphs and maps where these data may be sued, this function
converts them to proper name formats/title case with the first letter of
every word capitalised excepting words like “at” or “on” and keeps
acronyms like “AWS” or “PIRSA” or state abbreviations in the station
names as all caps.

## References

Station location and other metadata are sourced from the Australian
Bureau of Meteorology (BOM) webpage, Bureau of Meteorology Site
Numbers:  
<https://www.bom.gov.au/climate/cdo/about/site-num.shtml> and
<https://www.bom.gov.au/climate/data/lists_by_element/stations.txt> and
the DPIRD Weather 2.0 API.

## See also

Other DPIRD:
[`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md),
[`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md),
[`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md)

Other SILO:
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`silo_daily_values`](https://docs.ropensci.org/weatherOz/reference/silo_daily_values.md)

Other metadata:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md)

## Author

Adam H. Sparks, <adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# fetch metadata for all stations available in {weatherOz}
get_stations_metadata(api_key = "your_api_key")
} # }
```
