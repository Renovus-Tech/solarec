---
layout: default
permalink: /documentation/react/
---
# General usage and project structure of React Frontend
The React Frontend is a web application for viewing and analyzing data of solar inverters. It connects to a backend that receives and process data from the inverters and displays data on charts and graphs. Also informs the user about the state of the inverters and shows alerts related to malfunction.

## Screenshots
![Overview](https://github.com/Renovus-Tech/solarec/blob/main/documentation/imgs/screenshot-overview.jpg?raw=true)
![Trends](https://github.com/Renovus-Tech/solarec/blob/main/documentation/imgs/screenshot-trends.jpg?raw=true)
![Performance](https://github.com/Renovus-Tech/solarec/blob/main/documentation/imgs/screenshot-performance.jpg?raw=true)

## Project Structure
```
solarec-react
├── public/              # static files
│   ├── favicon.ico
│   ├── index.html       # html template
│   └── manifest.json
│
├── src/                 # project root
│   ├── assets/          # images, icons, etc.
│   ├── components/      # common components - header, footer, sidebar, etc.
│   ├── layouts/         # layout containers
│   ├── helpers/     
│   ├── scss/            # scss styles
│   ├── locales/         # translations files
│   ├── views/           # application views
│   │   └── pages/        # application pages
│   │      ├── user/      # user pages
│   │      ├── client/    # client pages
│   │      ├── login/     # login and password reset pages
│   │      ├── enery/     # energy pages
│   │      ├── revenue/   # revenue pages
│   │      ├── page404/   
│   │      └── page500/   
│   ├── _nav.js          # sidebar navigation config
│   ├── App.js
│   ├── index.js
│   ├── routes.js        # routes config
│   └── store.js         # template state example 
│
├── .env                 # environment variables
├── licenses.json        # packages licenses information
├── package.json         # npm dependencies and run scripts
└── README.md            # Documentation
```

# Technologies Used


-   **Main stack:**  Nodejs, npm, React, Javascript, Bootstrap, Redux, scss.
-   **UI Kit and template:** 
	-   **CoreUI v4:** - https://coreui.io/react/docs/getting-started/introduction/
	-   **Free React Admin Template:** https://coreui.io/product/free-react-admin-template/
-   **Other packages dependencies:** @kurkle/color, classnames, google-map-react, i18next, js-cookie, prop-types, react-app-polyfill, react-chartjs-2, react-datepicker, react-dom, react-flags-select, react-i18next, react-router-dom, react-scripts, sass, simplebar-react, web-vitals
-   **Development packages dependencies:** @babel/preset-env, "@babel/preset-react, @testing-library/jest-dom, @testing-library/react, eslint-config-prettier, eslint-plugin-prettier, jest, jest-canvas-mock, jest-cli, jest-fetch-mock, license-compatibility-checker, prettier

Other packages dependencies: @kurkle/color, classnames, google-map-react, js-cookie, prop-types, react-app-polyfill, react-chartjs-2, react-datepicker, react-dom, react-flags-select, react-i18next, react-router-dom, react-scripts, sass, simplebar-react, web-vitals
Development packages dependencies: @babel/preset-env, "@babel/preset-react, @testing-library/jest-dom, @testing-library/react, eslint-config-prettier, eslint-plugin-prettier, jest, jest-canvas-mock, jest-cli, jest-fetch-mock, license-compatibility-checker, prettier



# Backend API

## Concepts
- **Client:** The person, group or company that uses the system for a common purpose.
- **User:**  A personal user to log in to a client's account.
- **Location:** The place where an inverter or group of inverters is located. A client has one or more locations.
- **Generator (inverter):** A unit inverter (solar panel).

## Data filters
Attributes used across the app to filter de information needed.

### Period: 
- cy -> Current year
- cm -> Current month
- cw -> Current week
- y -> Yesterday
- 30d -> 30 days
- 12w -> 12 weeks
- 12m -> 12 month
- cy-{{x}} -> Current year minus {{x}}
- x -> Custom range
	- from
	- to

### Group by:
- hour
- day
- week
- month
- year


## User settings
Settings defined for the app user account.

### Language
Language on the application
- **name:** language
- **values:** 
   - en: English
   - es: Spanish
   - fr: French
   - pt: Portugues



## Client settings
Settings defined for the clients installation. Apply to all the accounts on the client.

**Alert:** Data Availability lower than\
**name:** alertDataAvailabilityLowerThan\
**category:** Alerts\
**type:** number\
**max:** 100\
**min:** 0\
**units:** %\
**valueDefault:** 90\

**Alert:** Negative change exceeding\
**name:** alertNegativeChangeExceeding\
**category:** Alerts\
**type:** number\
**min:** 0\
**max:** 100\
**units:** %\
**valueDefault:** 6\

**Alert:** Time-Based Availability lower than\
**name:** alertTimeBasedAvailabilityLowerThan\
**category:** Alerts\
**type:** number\
**min:** 0\
**max:** 100\
**units:** %\
**valueDefault:** 90\

**Certificate:** Certificate Sold Porcentage\
**name:** certSoldPorcentage\
**category:** Certificate\
**type:** number\
**min:** 0\
**max:** 100\
**units:** %\
**valueDefault:** 50\

**Certificate:** Certificate price\
**name:** certPrice\
**category:** Certificate\
**type:** number\
**min:** 0\
**max:** 100\
**units:** %\
**valueDefault:** 20\


## Endpoints

### GET

#### Authentication
Get authenticated user data.\
**Endpoint:** GET https://{{HOST}}:{{PORT}}/ api3/rest/security/authenticate

#### Locations
Get all locations data for logged user.\
**Endpoint:** GET https://{{HOST}}:{{PORT}}/ api3/rest/security/authenticate/location

#### Location
Get location data for selected location.\
**Endpoint:** GET https://{{HOST}}:{{PORT}}/ api3/rest/security/authenticate/location/{locationId}

#### Location and inverters 
Get inverter/s location data and inverter/s data.\
**Endpoint:** GET https://{{HOST}}:{{PORT}}/ api3/rest/admin/locations/current

#### Client settings 
Get client settings.\
**Endpoint:** GET https://{{HOST}}:{{PORT}}/ api3/rest/admin/clients/current

#### Alerts
Get yesterday  alerts.\
**Endpoint:** GET https://{{HOST}}:{{PORT}}/ api3/rest/solar/overview/alerts


### POST

#### Authentication
Authenticate user.\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/api3/rest/security/authenticate\
**Body example:**
```
{
    email: ‘someUser’,
    password: ‘somePassword’,
}
```

#### User settings
Change user settings\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/security/authenticate/current\
**Body example:**
```
{
  settings: 
    [
      {
        name: ‘language’,
        value: ‘es’,
      }
    ]
}
```

#### Client settings
Change client settings\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/security/authenticate/current\
**Body example:**
```
{
  settings: 
    [
      {
        name: ‘alertDataAvailabilityLowerThan’,
        value: 88,
      },
      {
        name: ‘alertNegativeChangeExceeding’,
        value: 5,
      },
      {
        name: ‘alertTimeBasedAvailabilityLowerThan’,
        value: 93,
      },
      {
        name: ‘certSoldPorcentage’,
        value: 46,
      },
      {
        name: ‘certPrice’,
        value: 22,
      }
    ]
}
```

#### Overview
Get general data for Overview page.\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/solar/overview\
**Body example:**
```
{
    location: 1,
    period: ‘y’
}
```

#### Overview CO2
Get CO2 data for Overview page.\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/solar/overview/co2\
**Body example:**
```
{
    location: 1,
    period: ‘y’
}
```

#### Climate
Get the climate data.\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/solar/climate\
**Body example:**
```
{
    location: 1,
    period: ‘cm’
    groupBy: ‘hour’,
    generators: [1,2],
}
```

#### Performance index
Get the inverter/s performance data.\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/solar/performanceIndex\
**Body example:**
```
{
    location: 1,
    period: ‘cm’
    groupBy: ‘day’,
    generators: [1,2],
}
```

#### Revenue
Get data for certificates generated and sold and CO2 avoided.\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/chart/revenue\
**Body example:**
```
{
    location: 1,
    period: ‘cm’
}
```

#### Sales
Sames a revenue but returning also income and price for certificates.\
**Endpoint:** POST https://{{HOST}}:{{PORT}}/ api3/rest/chart/revenue/sales\
**Body example:**
```
{
    location: 1,
    period: ‘cm’
}
```


# Security
Without authentication first user can only access to Login and Password reset pages. If user tries to access any other page without being authenticated the app displays login page. Backend doesn't retrieve any data if user is not correctly authenticated. The authentication security is handled on the backend.



