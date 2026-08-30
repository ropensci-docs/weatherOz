# Get DPIRD Weather Data in Summarised Formats

Fetch nicely formatted individual station weather summaries from the
DPIRD Weather 2.0 API.

## Usage

``` r
get_dpird_summaries(
  station_code,
  start_date,
  end_date = Sys.Date(),
  interval = c("daily", "15min", "30min", "hourly", "monthly", "yearly"),
  values = "all",
  api_key = get_key(service = "DPIRD")
)
```

## Arguments

- station_code:

  A `character` string or `factor` from
  [`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)
  of the BOM station code for the station of interest.

- start_date:

  A `character` string or `Date` object representing the beginning of
  the range to query in the format “yyyy-mm-dd” (ISO8601). Data returned
  is inclusive of this date.

- end_date:

  A `character` string or `Date` object representing the end of the
  range query in the format “yyyy-mm-dd” (ISO8601). Data returned is
  inclusive of this date. Defaults to the current system date.

- interval:

  A `character` string that indicates the time interval to `monthly` or
  `yearly`. For intervals shorter than 1 day, the time period covered
  will be midnight to midnight, with the end_date time interval being
  before midnight - hour/minute values are for the end of the time
  period. Data for shorter intervals (`15min`, `30min`) are available
  from January of the previous year.

- values:

  A `character` string with the type of summarised weather to return.
  See **Available Values** for a full list of valid values. Defaults to
  `all` with all available values being returned.

- api_key:

  A `character` string containing your API key from DPIRD,
  <https://www.dpird.wa.gov.au/online-tools/apis/>, for the DPIRD
  Weather 2.0 API. Defaults to automatically detecting your key from
  your local .Renviron, .Rprofile or similar. Alternatively, you may
  directly provide your key as a string here. If nothing is provided,
  you will be prompted on how to set up your R session so that it is
  auto-detected.

## Value

a
[`data.table::data.table()`](https://rdrr.io/pkg/data.table/man/data.table.html)
with `station_code` and the date interval queried together with the
requested weather variables in alphabetical order. The first ten columns
will always be:

- `station_code`,

- `station_name`,

- `longitude`,

- `latitude`,

- `year`,

- `month`,

- `day`,

- `hour`,

- `minute`, and if `month` or finer is present,

- `date` (a combination of year, month, day, hour, minute as
  appropriate).

## Note

Please note this function converts date-time columns from Coordinated
Universal Time ‘UTC’ to Australian Western Standard Time ‘AWST’.

## Start Dates

The earliest available data start from August of 2000 for Vasse, “VA”.

## Column Name Details

Column names are converted from the default returns of the API to be
snake_case formatted and where appropriate, the names of the values that
are analogous between SILO and DPIRD data are named using the same name
for ease of interoperability, *e.g.*, using
[`rbind()`](https://rdrr.io/r/base/cbind.html) to create a `data.table`
that contains data from both APIs. However, use with caution and don't
mix datasets of different time-steps, *i.e.*, this function gets many
summary values not just “daily” time-step data. The functions that
access the SILO API only provide access to daily data, so don't mix
(sub)hourly, monthly or yearly data from DPIRD with SILO.

## Available Values

- all (which will return all of the following values),

- airTemperature,

- airTemperatureAvg,

- airTemperatureMax,

- airTemperatureMaxTime,

- airTemperatureMin,

- airTemperatureMinTime,

- apparentAirTemperature,

- apparentAirTemperatureAvg,

- apparentAirTemperatureMax,

- apparentAirTemperatureMaxTime,

- apparentAirTemperatureMin,

- apparentAirTemperatureMinTime,

- barometricPressure,

- barometricPressureAvg,

- barometricPressureMax,

- barometricPressureMaxTime,

- barometricPressureMin,

- barometricPressureMinTime,

- battery,

- batteryMinVoltage,

- batteryMinVoltageDateTime,

- chillHours,

- deltaT,

- deltaTAvg,

- deltaTMax,

- deltaTMaxTime,

- deltaTMin,

- deltaTMinTime,

- dewPoint,

- dewPointAvg,

- dewPointMax,

- dewPointMaxTime,

- dewPointMin,

- dewPointMinTime,

- erosionCondition,

- erosionConditionMinutes,

- erosionConditionStartTime,

- errors,

- etoShortCrop,

- etoTallCrop,

- evapotranspiration,

- evapotranspirationShortCrop,

- evapotranspirationTallCrop,

- frostCondition,

- frostConditionMinutes,

- frostConditionStartTime,

- heatCondition,

- heatConditionMinutes,

- heatConditionStartTime,

- observations,

- observationsCount,

- observationsPercentage,

- panEvaporation,

- panEvaporation12AM,

- rainfall,

- relativeHumidity,

- relativeHumidityAvg,

- relativeHumidityMax,

- relativeHumidityMaxTime,

- relativeHumidityMin,

- relativeHumidityMinTime,

- richardsonUnits,

- soilTemperature,

- soilTemperatureAvg,

- soilTemperatureMax,

- soilTemperatureMaxTime,

- soilTemperatureMin,

- soilTemperatureMinTime,

- solarExposure,

- wetBulb,

- wetBulbAvg,

- wetBulbMax,

- wetBulbMaxTime,

- wetBulbMin,

- wetBulbMinTime,

- wind,

- windAvgSpeed, and

- windMaxSpeed

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
[`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)

Other data fetching:
[`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md),
[`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md),
[`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md),
[`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md),
[`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md),
[`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md),
[`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md),
[`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md),
[`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md),
[`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md),
[`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md),
[`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md),
[`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)

## Author

Adam H. Sparks, <adamhsparks@gmail.com>, and Rodrigo Pires,
<rodrigo.pires@dpird.wa.gov.au>

## Examples

``` r
if (FALSE) { # \dontrun{
# Note that you need to supply your own API key
# Use default for end date (current system date) to get rainfall

wd <- get_dpird_summaries(
  station_code = "CL001",
  start_date = "20171028",
  api_key = "your_api_key",
  interval = "yearly",
  values = "rainfall"
)

# Only for wind and erosion conditions for daily time interval

wd <- get_dpird_summaries(
  station_code = "BI",
  start_date = "20220501",
  end_date = "20220502",
  api_key = "your_api_key",
  interval = "daily",
  values = c(
    "wind",
    "erosionCondition",
    "erosionConditionMinutes",
    "erosionConditionStartTime"
  )
)
} # }
```
