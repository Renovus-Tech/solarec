---
layout: default
permalink: /documentation/grid/
---
# Integration with data grid information and data cycle
The information for the energy grid is a key part of the solution, it is use to calculate important information regarding the CO2. Since the information from the grid can vary from service to service the solution support the use of a grid data service.

## Integration with data service
Currently one service for data grid is supported and must implement the interface ```tech.renovus.solarec.grid.DataGridService``` and implement the ```retrieveGridData``` method. The method will be call for each country that is used for any of the countries of the clients.

Every 23 hours, a schedule will iterate through the different country clients and call the corresponding service.

Currently 2 services are available:
- ```tech.renovus.solarec.grid.ember.EmberDataGridService```
- ```tech.renovus.solarec.grid.electricMaps.ElectricMapsService```