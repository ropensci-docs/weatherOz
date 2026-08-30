# Find the Nearest Weather Stations to a Given Geographic Point or Known Station

Find nearby weather stations given geographic coordinates or a station
code for both of the DPIRD and SILO weather station networks. Either a
combination of `latitude` and `longitude` or `station_code` must be
provided. A DPIRD API key is only necessary to search for stations in
the DPIRD network. If you are not interested in DPIRD stations in
Western Australia, you may use this function to query only SILO stations
for all of Australia without using a key.

## Usage

``` r
find_nearby_stations(
  longitude = NULL,
  latitude = NULL,
  station_code = NULL,
  distance_km = 100,
  api_key = NULL,
  which_api = "silo",
  include_closed = FALSE
)
```

## Arguments

- longitude:

  A `numeric` value of longitude in decimal degree (DD) format. Optional
  and defaults to `NULL`. Required if `station_code` is not provided.

- latitude:

  A `numeric` value of latitude in decimal degree (DD) format. Optional
  and defaults to `NULL`. Required if `station_code` is not provided.

- station_code:

  A `string` with the station code for the station of interest. Optional
  and defaults to `NULL`. Required if `longitude` and `latitude` are not
  provided.

- distance_km:

  A `numeric` value for distance to limit the search from the station or
  location of interest. Defaults to 100 km.

- api_key:

  A `character` string containing your API key from DPIRD,
  <https://www.dpird.wa.gov.au/online-tools/apis/>, for the DPIRD
  Weather 2.0 API. If left as `NULL`, defaults to automatically
  detecting your key from your local .Renviron, .Rprofile or similar.
  Alternatively, you may directly provide your key as a string here. If
  nothing is provided, you will be prompted on how to set up your R
  session so that it is auto-detected. Only used when `which_api` is
  `DPIRD` or `all`.

- which_api:

  A `string` value that indicates which API to use. Defaults to `silo`
  only. Valid values are `all`, for both SILO (BOM) and DPIRD weather
  station networks; `silo` for only stations in the SILO network; or
  `dpird` for stations in the DPIRD network.

- include_closed:

  A `Boolean` value that indicates whether closed stations in the DPIRD
  network should be included in the results. Defaults to `FALSE` with
  closed stations not included.

## Value

A
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
with `station_code`, `station_name`, `latitude`, `longitude`, `elev_m`,
`state`, `owner`, and `distance`. Data are sorted by increasing distance
from station or location of interest.

## Note

You can request your own API key from DPIRD for free by filling out the
form found at <https://www.dpird.wa.gov.au/online-tools/apis/>.

## See also

Other DPIRD:
[`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md),
[`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md),
[`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

Other SILO:
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md),
[`silo_daily_values`](https://docs.ropensci.org/weatherOz/reference/silo_daily_values.md)

Other metadata:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

## Author

Rodrigo Pires, <rodrigo.pires@dpird.wa.gov.au>, and Adam H. Sparks,
<adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{

# Note that queries to the DPIRD API require you to have your own API key.

# Query WA only stations and return DPIRD's stations nearest to the
# Northam, WA station, "NO", returning stations with 50 km of this station

wa_stn <- find_nearby_stations(
  station_code = "NO",
  distance_km = 50,
  api_key = "your_api_key",
  which_api = "dpird"
)

# Query stations nearest DPIRD's Northam, WA station, "NO" and return both
# DPIRD and SILO/BOM stations within 50 km of this station.

wa_stn <- find_nearby_stations(
  station_code = "NO",
  distance_km = 50,
  api_key = "your_api_key",
  which_api = "all"
)

# Query Wagga Wagga BOM station finding stations within 200 km of it, note
# that it is not necessary to provide an `api_key` for SILO queries of
# nearby stations.

wagga_stn <- find_nearby_stations(
  latitude = -35.1583,
  longitude = 147.4575,
  distance_km = 200,
  which_api = "silo"
)
} # }
```
