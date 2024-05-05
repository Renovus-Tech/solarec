---
layout: default
permalink: /documentation/weather/
---
# Integration with weather information and data cycle
The information for the weather is a key part of the solution, it is use to calculate important information regarding the performance and alerts of the inverters. Since the information from the weather can vary from preferences and costs, the solution support the use of a weather service.

## Integration with weather
Currently one service for weather is supported and must implement the interface `tech.renovus.solarec.weather.WeatherService` and implement the `retrieveWeatherData` method. The method will be call for each inverter service that might required additional information.

Currently 1 services is available
- `tech.renovus.solarec.weahter.meteoblue.MeteoblueWeatherServiceImpl`

The data that needs to be retrieve is:
- Temperature (`DataTypeVo.TYPE_SOLAR_STATION_AMBIENT_TEMPERATURE = 503`)
- Irradiation (`DataTypeVo.TYPE_SOLAR_STATION_IRRADIATION = 505`)
- Cloud cover (`DataTypeVo.TYPE_SOLAR_STATION_TOTAL_CLOUD_COVER	= 506`)
- Precipitation (`DataTypeVo.TYPE_SOLAR_STATION_PRECIPITATION	= 507`)
