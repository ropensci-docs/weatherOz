# Find the Nearest Town With a BOM Forecast

For a given `latitude` and `longitude`, find the nearest town that the
BOM provides a forecast for.

## Usage

``` r
find_forecast_towns(longitude = 149.2, latitude = -35.3, distance_km = 100)
```

## Arguments

- longitude:

  A `numeric` value of longitude in decimal degree (DD) format. By
  default, Canberra (approximately).

- latitude:

  A `numeric` value of latitude in decimal degree (DD) format. By
  default, Canberra (approximately).

- distance_km:

  A `numeric` value of the distance in kilometres from the `latitude`
  and `longitude` point beyond which values will not be returned.

## Value

A
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
of all forecast towns (in this package) sorted by distance from
`latitude` and `longitude`, ascending.

## See also

Other BOM:
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md),
[`parse_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_coastal_forecast.md),
[`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)

Other metadata:
[`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md),
[`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md),
[`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md),
[`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md),
[`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md),
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

## Author

Hugh Parsonage, <hugh.parsonage@gmail.com>, and James Goldie,
<me@jamesgoldie.dev>, and Adam H. Sparks, <adamhsparks@gmail.com>

## Examples

``` r
if (FALSE) { # interactive()

# find forecast towns near Esperance, WA
find_forecast_towns(longitude = 121.8913, latitude = -33.8614)
}
```
