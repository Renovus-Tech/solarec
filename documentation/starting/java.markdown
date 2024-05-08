---
layout: default
permalink: /documentation/starting/java
---
# Getting started with Java Code
- Using your prefer Git and IDE software clone the repository and make sure that all required components can build correctly.
- Create a database for the project (check the project [solarec-db](https://github.com/Renovus-Tech/solarec-db)).
- Adjust the **application.properties** file with all the required properties for the action that you are going to work on

Many of the codes requried to be executed are dynamically loaded from the database, therefore, check some examples at: [11.data.canary.sql](https://github.com/Renovus-Tech/solarec-db/blob/main/data/sample/11.data.canary.sql) from the **solarec-db** repository.

## Connect to a new inverter
- Make sure to have all the required API information
- Make sure to have all the required credentials to connect to API
- Register the inverter information and required parameters in the tables **data_definition** and **data_def_parameter**
- Create a client / location / generator and associate the required information from the **data_definition** and **data_def_parameters** tables

The code of an inverter is simple to create, you just need to create the brand name package at the **solarec.inverters** module **tech.renovus.solarec.inverters.brand** package. We recommend that all required classes of the inverter are stored in that package to avoid confusion with similar classes of other inverters.

The main class that must implemented is **tech.renovus.solarec.inverters.common.InverterService** and it executable is the one stored in the **data_definition** table.

The main method that you will have to implement is the **InverterData retrieveData() throws InveterServiceException**. This method is core of the services and is the one responsable for:
- Data validation
- Connect to the inverter API
- Extract the data from the inverter
- Convert the data to adjust the definitions of Solarec
- Generate the data that need so be saved in the database
- Generate alerts in case a user action is required
- Log all required information

The method is **not responsable** for:
- Save the data in the database
- Calculate performance
- Generate alerts regarding missing data

The data that needs to be retrieve are:

- DC Power (`DataTypeVo.TYPE_SOLAR_INVERTER_DC_POWER = 501`)
- AC Power (`DataTypeVo.TYPE_SOLAR_INVERTER_AC_POWER = 502`)
- Ambient Temperature (`DataTypeVo.TYPE_SOLAR_STATION_AMBIENT_TEMPERATURE = 503`): if not available in the inverter, the weather service can be use to retrieve it.
- Module Temperature (`DataTypeVo.TYPE_SOLAR_STATION_MODULE_TEMPERATURE = 504`): if not available in the inverter, the weather service can be use to retrieve it.
- Irradiation (`DataTypeVo.TYPE_SOLAR_STATION_IRRADIATION = 505`): if not available in the inverter, the weather service can be use to retrieve it.
- Total production (`DataTypeVo.TYPE_LOCATION_SOLAR_OUTPUT_CAPACITY = 500`): in KW, can be calculated as the sum of the AC Power of all inverters for that period.

The inverter service code will be execute every 24 hours by the **tech.renovus.solarec.scheduler.InvertersCheckScheduler** at the **solarec.schedule** module, for each enabled client + location + generator. In case the inverter does not provide the weather information, you can obtain that data from the **WeatherService**.

For samples, check the list of currently implemented brands at: [solarec-java / solarec.inveters / inverters](https://github.com/Renovus-Tech/solarec-java/tree/main/solarec.inverters/src/main/java/tech/renovus/solarec/inverters/brand).

## Connect to a new data grid service
- Make sure to have all the required API information
- Make sure to have all the required credentials to connect to API
- If required add properties to the application.properties configuration file

Currently one service for data grid is supported and must implement the interface **tech.renovus.solarec.grid.DataGridService**. You can enable / disable the active data grid service class by adding or removing the **@Service** annotation. 

The main method that you will have to implement is the **Collection<CtrDataVo> retrieveGridData(CountryVo ctrVo) throws DataGridServiceException**. This method is core of the services and is the one responsable for:
- Data validation
- Connect to the data grid API
- Extract the data from the grid
- Convert the data to adjust the definitions of Solarec
- Generate the data that need so be saved in the database
- Log all required information

The method is **not responsable** for:
- Save the data in the database
- Calculate performance

The data that needs to be retrieve is:

- Emissions Intensity CO2 per KWH (`DataTypeVo.TYPE_COUNTRY_EMISSIONS_INTENSITY_GCO2_PER_KWH = 901`)

The inverter service code will be execute every 6 hours by the **tech.renovus.solarec.scheduler.DataGridCheckScheduler** at the **solarec.schedule** module. The method will be call for each country that is used for any of the countries of the clients.

For samples, check the list of currently implemented services as: [solarec-java / solarec.inveters / grid](https://github.com/Renovus-Tech/solarec-java/tree/main/solarec.inverters/src/main/java/tech/renovus/solarec/grid).

## Connect to a new weather service
- Make sure to have all the required API information
- Make sure to have all the required credentials to connect to API
- If required add properties to the application.properties configuration file

Currently one service for data grid is supported and must implement the interface **tech.renovus.solarec.weather.WeatherService**. You can enable / disable the active data grid service class by adding or removing the **@Service** annotation. 

The main method that you will have to implement is the **Collection<StaDataVo> retrieveWeatherData(LocationVo locVo, StationVo station, Date dateFrom, Date dateTo) throws WeatherServiceException**. This method is core of the services and is the one responsable for:
- Data validation
- Connect to the data grid API
- Extract the data from the grid
- Convert the data to adjust the definitions of Solarec
- Generate the data that need so be saved in the database
- Log all required information

The method is **not responsable** for:
- Save the data in the database
- Calculate performance

The data that needs to be retrieve is:
- Temperature (`DataTypeVo.TYPE_SOLAR_STATION_AMBIENT_TEMPERATURE = 503`)
- Irradiation (`DataTypeVo.TYPE_SOLAR_STATION_IRRADIATION = 505`)
- Cloud cover (`DataTypeVo.TYPE_SOLAR_STATION_TOTAL_CLOUD_COVER	= 506`)
- Precipitation (`DataTypeVo.TYPE_SOLAR_STATION_PRECIPITATION	= 507`)

The weather service is not executed by any schduler, instead, it can be call from an **Inveter service**, in case the inverter does not provide the weather information.

For samples, check the list of currently implemented services as: [solarec-java / solarec.inveters / weather](https://github.com/Renovus-Tech/solarec-java/tree/main/solarec.inverters/src/main/java/tech/renovus/solarec/weather).