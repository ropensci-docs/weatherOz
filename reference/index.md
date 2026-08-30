# Package index

## Data Fetching

### BOM

Functions that fetch BOM Data from the FTP server.

- [`get_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_coastal_forecast.md)
  : Get a BOM Coastal Waters Forecast
- [`get_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_precis_forecast.md)
  : Get a BOM Daily Précis Forecast
- [`get_radar_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_radar_imagery.md)
  : Get BOM Radar Imagery
- [`get_satellite_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_satellite_imagery.md)
  : Get BOM Satellite Imagery

### DPIRD

Functions that fetch data from the DPIRD Weather 2.0 API.

- [`get_dpird_extremes()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_extremes.md)
  : Get DPIRD Extreme Weather Event Summaries
- [`get_dpird_minute()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_minute.md)
  : Get DPIRD Weather Data by the Minute
- [`get_dpird_summaries()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_summaries.md)
  : Get DPIRD Weather Data in Summarised Formats
- [`get_dpird_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_apsim.md)
  : Get DPIRD Summary Weather Data in the APSIM Format From the Weather
  2.0 API

### SILO

Functions that fetch data from the SILO API.

- [`get_data_drill()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill.md)
  : Get DataDrill Weather Data From SILO
- [`get_patched_point()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point.md)
  : Get PatchedPoint Weather Data From SILO
- [`get_data_drill_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_data_drill_apsim.md)
  : Get DataDrill Weather Data in the APSIM Format From SILO
- [`get_patched_point_apsim()`](https://docs.ropensci.org/weatherOz/reference/get_patched_point_apsim.md)
  : Get PatchedPoint Weather Data in the APSIM Format From SILO

### MET Weather API forecast

Functions that fetch weather forecast data from the Norwegian
Meteorological Institute API.

- [`get_metno_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_forecast.md)
  : Get Weather Forecast Data from MET Weather API
- [`get_metno_daily_forecast()`](https://docs.ropensci.org/weatherOz/reference/get_metno_daily_forecast.md)
  : Get Daily Weather Forecast Data from MET Weather API

## Metadata Fetching

Functions that get metadata, *e.g.*, station uptime, dataset
availability, nearby stations or forecast locations, values that the
station records, etc.

- [`find_forecast_towns()`](https://docs.ropensci.org/weatherOz/reference/find_forecast_towns.md)
  : Find the Nearest Town With a BOM Forecast
- [`find_nearby_stations()`](https://docs.ropensci.org/weatherOz/reference/find_nearby_stations.md)
  : Find the Nearest Weather Stations to a Given Geographic Point or
  Known Station
- [`find_stations_in()`](https://docs.ropensci.org/weatherOz/reference/find_stations_in.md)
  : Find Stations Within a Geospatially Defined Geographic Area of
  Interest
- [`get_available_imagery()`](https://docs.ropensci.org/weatherOz/reference/get_available_imagery.md)
  : Get a List of Available BOM Satellite Imagery
- [`get_available_radar()`](https://docs.ropensci.org/weatherOz/reference/get_available_radar.md)
  : Get a List of Available BOM Radar Imagery
- [`get_dpird_availability()`](https://docs.ropensci.org/weatherOz/reference/get_dpird_availability.md)
  : Get the Availability for DPIRD Weather Stations
- [`get_stations_metadata()`](https://docs.ropensci.org/weatherOz/reference/get_stations_metadata.md)
  : Get Weather Station Metadata for Both DPIRD and SILO Weather
  Stations

## File Parsing

Functions that parse files that you already downloaded to your computer.

- [`parse_coastal_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_coastal_forecast.md)
  : Parse BOM Coastal Waters Forecast XML Files
- [`parse_precis_forecast()`](https://docs.ropensci.org/weatherOz/reference/parse_precis_forecast.md)
  : Parse BOM Précis Forecast XML Files

## Built in Datasets

Datasets included in {WeatherOz}.

- [`dpird_extreme_weather_values`](https://docs.ropensci.org/weatherOz/reference/dpird_extreme_weather_values.md)
  : A List of DPIRD Extreme Weather Data Values
- [`dpird_minute_values`](https://docs.ropensci.org/weatherOz/reference/dpird_minute_values.md)
  : A List of DPIRD Minute Weather Data Values
- [`dpird_summary_values`](https://docs.ropensci.org/weatherOz/reference/dpird_summary_values.md)
  : A List of DPIRD Summary Weather Data Values
- [`silo_daily_values`](https://docs.ropensci.org/weatherOz/reference/silo_daily_values.md)
  : A List of SILO Daily Weather Values
- [`south_west_agricultural_region`](https://docs.ropensci.org/weatherOz/reference/south_west_agriculture_region.md)
  : Western Australia Southwest Agriculture Region Geospatial Polygon

## Helper Functions

Functions intended to make using {weatherOz} a more enjoyable
experience.

- [`get_key()`](https://docs.ropensci.org/weatherOz/reference/get_key.md)
  : Get or Set Up API Keys
- [`metno_timeseries_to_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_timeseries_to_data_table.md)
  : Convert MET Weather API timeseries to data.table
- [`metno_resample_data_table()`](https://docs.ropensci.org/weatherOz/reference/metno_resample_data_table.md)
  : Resample data.table to different time frequencies
- [`metno_get_dominant_symbol()`](https://docs.ropensci.org/weatherOz/reference/metno_get_dominant_symbol.md)
  : Get dominant weather symbol from a collection
