---
layout: default
permalink: /documentation/inverters/
---
# Integration with inverters and data cycle
The inverters are a key part of the solution, are the ones that provide the information required, but also are complex, since all of them can define their own API.
In order to solve the problem to communicate with multiple inverters brands, the Solarec code as have an interface `tech.renovus.solarec.inverters.common.InverterService` that defines the methods that any inverter that Solrec connects to must implements. Also, since each inverter has its own parameters and requeriments, a series of metadata values will be available at the client, location and generator (inverter) level.

## Integration with inverters
Each inverter will be defined as a `DataDefinitionVo` and will contain the `package + class` that implements the connection to the inverter, plus a series of parameters that must be set in order to connect.

Every 24 hours, a schedule will iterate through all the generators / invereters and will load the associated DataDefinitionVo. With it, it will call the invereter executable, which will be responsable for:

- Validate that the required data to connect is available
- Establish a connection with the inverter
- Retrieve the required data from the last one retrieve to the period of time available
- Retrieve the weather information from a weather service, in case the inverter does not provide it
- Adjust the values so that they correspond to Solarec definition

## Data cycle
1. Daily data call
2. Data retrieve (invereter service)
3. Data conversion (invereter service)
4. Data store 
5. Alerts calculation
6. Alerts notification
7. Certificate generation

The data that needs to be retrieve are:

- DC Power (`DataTypeVo.TYPE_SOLAR_INVERTER_DC_POWER = 501`)
- AC Power (`DataTypeVo.TYPE_SOLAR_INVERTER_AC_POWER = 502`)
- Ambient Temperature (`DataTypeVo.TYPE_SOLAR_STATION_AMBIENT_TEMPERATURE = 503`): if not available in the inverter, the weather service can be use to retrieve it.
- Module Temperature (`DataTypeVo.TYPE_SOLAR_STATION_MODULE_TEMPERATURE = 504`): if not available in the inverter, the weather service can be use to retrieve it.
- Irradiation (`DataTypeVo.TYPE_SOLAR_STATION_IRRADIATION = 505`): if not available in the inverter, the weather service can be use to retrieve it.
- Total production (`DataTypeVo.TYPE_LOCATION_SOLAR_OUTPUT_CAPACITY = 500`): in KW, can be calculated as the sum of the AC Power of all inverters for that period.

Previous data need to stored within a 15 minutes frequency.

## Sample data
As parte of Solarec opensource code, the InverterService for the following brand are provided as example of code for the data cycle:

- Aiswei
- Fimer
- Fornius
- SAM
- Sofar
- SolarEdge

## Inverter service
When coding the inverter service, the following aspects need to be consider in the code:

- Create all the required methods to retrieve the data
- Create all the required methods retrieve the necessary information for an automated interaction with the API. These might required to call endpoints to retrieve list of devices for example.
- Take in consideration the frequency of the data that is return by the API and the frequency in with the data need to be stored
- Validate the all required configuration is present

## Testing the inverter service
- Since most data is confidential, code it in a way the different parameters required are retrieve as a system property
- First call all the required endpoints manually and finally call the service retrieveData method to test them all together.