# Resample data.table to different time frequencies

Resample data.table to different time frequencies

## Usage

``` r
metno_resample_data_table(dt_data, freq)
```

## Arguments

- dt_data:

  data.table with time column

- freq:

  Character frequency: "hourly", "daily", "weekly", or "monthly"

## Value

A resampled data.table

## See also

Other METNO:
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`metno_get_dominant_symbol()`](https://docs.ropensci.org/weatherOz/reference/metno_get_dominant_symbol.md),
[`metno_timeseries_to_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_timeseries_to_data_table.md)

Other parse:
[`metno_get_dominant_symbol()`](https://docs.ropensci.org/weatherOz/reference/metno_get_dominant_symbol.md),
[`metno_timeseries_to_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_timeseries_to_data_table.md),
[`parse_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_coastal_forecast.md),
[`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)

## Author

Rodrigo Pires, <rodrigo.pires@dpird.wa.gov.au>
