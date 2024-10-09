---
layout: default
permalink: /documentation/weather/
---
# Integration with weather information and data cycle
The information for the weather is a key part of the solution, it is use to calculate important information regarding the performance and alerts of the inverters. Since the information from the weather can vary from preferences and costs, the solution support the use of a weather service.

## Integration with weather
Currently one service for weather is supported and must implement the interface `tech.renovus.solarec.weather.WeatherService` and implement the `retrieveWeatherData` method. The method will be call for each inverter service that might required additional information.

Currently 3 services is available
- `tech.renovus.solarec.weahter.disabled.DisabledWeatherServiceImpl` (solarec.service.weather.provider = disabled)
- `tech.renovus.solarec.weahter.meteoblue.MeteoblueWeatherServiceImpl` (solarec.service.weather.provider = meteoblue)
- `tech.renovus.solarec.weahter.openmeteo.OpenMeteoWeatherServiceImpl` (solarec.service.weather.provider = openmeteo)

In order to determinate the service to be use, you need to the set the `solarec.service.weather.provider` property in the `application.properties` files.

The data that needs to be retrieve are:
- Temperature °C (`DataTypeVo.TYPE_SOLAR_STATION_AMBIENT_TEMPERATURE = 503`)
- Irradiation W/m2 (`DataTypeVo.TYPE_SOLAR_STATION_IRRADIATION = 505`)
- Cloud cover % (`DataTypeVo.TYPE_SOLAR_STATION_TOTAL_CLOUD_COVER	= 506`)
- Precipitation ,, (`DataTypeVo.TYPE_SOLAR_STATION_PRECIPITATION	= 507`)

##Data usage

| Description                                      | Code   | overview | power_curve | performance | climate | anomaly_detection | alerts | inverter | Data Grid | Weather | Certificate |
|--------------------------------------------------|--------|----------|-------------|-------------|---------|-------------------|--------|----------|-----------|---------|-------------|
| TYPE_SOLAR_STATION_AMBIENT_TEMPERATURE           | 503    | use      |             |             | use     |                   |        | added    |           | added   |             |
| TYPE_SOLAR_STATION_MODULE_TEMPERATURE            | 504    | use      |             |             | use     |                   |        | added    |           |         |             |
| TYPE_SOLAR_STATION_IRRADIATION                   | 505    | use      | use         | use         | use     |                   | use    | added    |           | added   |             |
| TYPE_SOLAR_STATION_TOTAL_CLOUD_COVER             | 506    |          |             |             |         |                   |        |          |           | added   |             |
| TYPE_SOLAR_STATION_PRECIPITATION                 | 507    |          |             |             |         |                   |        |          |           | added   |             |
