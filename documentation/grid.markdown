---
layout: default
permalink: /documentation/grid/
---
# Integration with data grid information and data cycle
The information for the energy grid is a key part of the solution, it is use to calculate important information regarding the CO2. Since the information from the grid can vary from service to service the solution support the use of a grid data service.

## Integration with data service
Currently one service for data grid is supported and must implement the interface `tech.renovus.solarec.grid.DataGridService` and implement the `retrieveGridData` method. The method will be call for each country that is used for any of the countries of the clients.

Every 23 hours, a schedule will iterate through the different country clients and call the corresponding service.

Currently 4 services are available:
- `tech.renovus.solarec.grid.disabled.DisabledDataGridService` (solarec.service.grid.provider = disabled)
- `tech.renovus.solarec.grid.ember.EmberDataGridService` (solarec.service.grid.provider = ember)
- `tech.renovus.solarec.grid.electricMaps.ElectricMapsService` (solarec.service.grid.provider = electricmaps)
- `tech.renovus.solarec.certificate.irec.br.IrecBrCertificateService` (solarec.service.grid.provider = irecbr)

In order to determinate the service to be use, you need to the set the `solarec.service.grid.provider` property in the `application.properties` files.

The data that needs to be retrieve is:
- Emissions Intensity CO2 per KWH (`DataTypeVo.TYPE_COUNTRY_EMISSIONS_INTENSITY_GCO2_PER_KWH = 901`)

##Data usage

| Description                                      | Code   | overview | power_curve | performance | climate | anomaly_detection | alerts | inverter | Data Grid | Weather | Certificate |
|--------------------------------------------------|--------|----------|-------------|-------------|---------|-------------------|--------|----------|-----------|---------|-------------|
| TYPE_COUNTRY_EMISSIONS_INTENSITY_GCO2_PER_KWH    | 901    |          |             |             |         |                   |        |          |           |         | added       |

