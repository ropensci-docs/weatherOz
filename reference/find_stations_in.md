# Find Stations Within a Geospatially Defined Geographic Area of Interest

Given an [sf](https://CRAN.R-project.org/package=sf) polygon or a
bounding box as a vector with the minimum and maximum longitude and
latitude values, find DPIRD or BOM stations in the SILO network that
fall within that defined area or the station nearest the centroid of the
area of interest.

## Usage

``` r
find_stations_in(
  x,
  centroid = FALSE,
  api_key = NULL,
  which_api = "all",
  include_closed = FALSE,
  crs = "EPSG:7844"
)
```

## Arguments

- x:

  One of two types of object:

  - A `Vector` A four-digit vector defining a bounding box of the area
    of interest in this order, ‘xmin’, ‘ymin’, ‘xmax’, ‘ymax’, or

  - An object of class [sf](https://CRAN.R-project.org/package=sf)
    defining the area of interest.

- centroid:

  `Boolean` A value of `TRUE` or `FALSE` indicating whether you want the
  centroid only to be used to find the nearest station to the centre of
  the area of interest. If “n” polygons are supplied, “n” stations are
  returned. Defaults to `FALSE` with all stations within the area of
  interest returned.

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

- crs:

  A `string` value that provides the coordinate reference system, AKA,
  "projection" to be used for the point extraction. Defaults to GDA
  2020, EPSG:7844. **NOTE** This will override any `crs` value that your
  . `polygon` provides unless you specify it again here, *e.g.*,
  `crs = sf::st_crs(polygon_object_name)`.

## Value

a [data.table](https://CRAN.R-project.org/package=data.table) object of
weather station(s) within the defined area of interest in an unprojected
format, EPSG:4326, WGS 84 – WGS84 - World Geodetic System 1984, used in
GPS format.

## See also

Other DPIRD:
[`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md),
[`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md),
[`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

Other SILO:
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md),
[`silo_daily_values`](https://docs.ropensci.org/weatherOz/reference/silo_daily_values.md)

Other metadata:
[`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md),
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

## Examples

``` r
if (FALSE) { # interactive()

# using a (generous) bounding box for Melbourne, Vic using only the SILO API
# for BOM stations, so no API key is needed.

bbox <- find_stations_in(
  x = c(144.470215, -38.160476, 145.612793, -37.622934),
  which_api = "SILO",
  include_closed = TRUE
)
bbox

# Use the same bounding box but only find a single station nearest
# the centroid using only the SILO API for BOM stations

centroid <- find_stations_in(
  x = c(144.470215, -38.160476, 145.612793, -37.622934),
  which_api = "SILO",
  include_closed = TRUE,
  centroid = TRUE
)
centroid

# Use the `south_west_agricultural_region` data to fetch stations only in the
# south-western portion of WA and plot it with {ggplot2} showing open/closed
# stations just to be sure they're inside the area of interest.

# As this is in WA, we can use the DPIRD network, so we need our API key.
# Using the `south_west_agricultural_region` {sf} object provided.

sw_wa <- find_stations_in(
  x = south_west_agricultural_region,
  api_key = "your_api_key",
  include_closed = TRUE
)

sw_wa
}
```
