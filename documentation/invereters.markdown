---
layout: default
permalink: /documentation/inverters/
---
# Integration with inverters and data cycle
The inverters are a key part of the solution, are the ones that provide the information required, but also are complex, since all of them can define their own API.
In order to solve the problem to communicate with multiple inverters brands, the Solarec code as have an interface ```tech.renovus.solarec.inverters.common.InverterService``` that defines the methods that any inverter that Solrec connects to must implements. Also, since each inverter has its own parameters and requeriments, a series of metadata values will be available at the client, location and generator (inverter) level.

## Integration with inverters
Each inverter will be defined as a ```DataDefinitionVo``` and will contain the ```package + class``` that implements the connection to the inverter, plus a series of parameters that must be set in order to connect.

Every 24 hours, a schedule will iterate through all the generators / invereters and will load the associated DataDefinitionVo. With it, it will call the invereter executable, which will be responsable for:

- Validate that the required data to connect is available
- Establish a connection with the inverter
- Retrieve the required data from the last one retrieve to the period of time available
- Retrieve the weather information from a weather service, in case the inverter does not provide it
- Adjust the values so that they correspond to Solarec definition

## Data cycle
1. Daily data call
1. Data retrieve (invereter service)
1. Data conversion (invereter service)
1. Data store 
1. Alerts calculation
1. Alerts notification
1. Certificate generation

## Sample data
As parte of Solarec opensource code, the InverterService for the following brand are provided as example of code for the data cycle:

- Fimer
- Fornius
- SAM
