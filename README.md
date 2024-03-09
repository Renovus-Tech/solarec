# Renovus Solarec
[![IMAGE ALT TEXT](http://img.youtube.com/vi/YRrv0dtq210/0.jpg)](http://www.youtube.com/watch?v=YRrv0dtq210 "Renovus (Uruguay) - AI for Carbon Offsets and Sustainable Energy")

Selected by [UNICEF Venture Fund’s First Cohort for Climate Action](https://www.unicef.org/innovation/venturefund/climate-action-cohort)

Other links of interest:
- [Venture Fund](https://www.unicefventurefund.org/story/unicef-venture-funds-inaugural-climate-action-cohort-kicks-stockholm)
- [Renovus | Linkedin](https://www.linkedin.com/company/renovus-energy-tech/)

# What you can read
- [code_of_conduct.md](CODE_OF_CONDUCT.md)
- [security_policies.md](SECURITY_POLICIES.md)
- [contribution.md](CONTRIBUTION.md)
- [new_feature_request_template.md](NEW_FEATURE_REQUEST_TEMPLATE.md)
- [issue_template.md](ISSUE_TEMPLATE.md)
- [pull_request_template.md](PULL_REQUEST_TEMPLATE.md)

# The repositories
**Renovus Solarec Open Source** solution is divided in various repositories that are technology dependent and that have specific goals. The repositories are:
- **[solarec-java](https://github.com/Renovus-Tech/solarec-java)**: contains information related to the Java technology of the project. The Java code is divided into a series of modules, in order to garantee a complete independence, portability and extensibility. Check out our [code_style_java.md](CODE_STYLE_JAVA.md).
	- **solarec.core**: contains all main API Rest code that will allow the interaction with different GUI.
	- **solarec.db**: contains all the required code to access the database and information stored there.
	- **solarec.implementations**: contains the main inmplementatiOns of the interface required for the execution of the solution. All non-specific implementations are here.
	- **solarec.interfaces**: Contains all the interface definitions of the projects. Sub repositories will required the information of these repository in order to implement and interact with other parts of the code.
	- **solarec.inverters**: contains the code to connect to different inverter manufacturers.
	- **solarec.schedule**: contains all the code that will run on background and therefore no GUI is required.
	- **solarec.vo**: contains all the required to represent the information in different VO.
- **[solarec-python](https://github.com/Renovus-Tech/solarec-python)**: contains information related to the Python technology of the project, used for different calculations and IA analyse of data. Check out our [code_style_python.md](CODE_STYLE_PYTHON.md).
- **[solarec-react](https://github.com/Renovus-Tech/solarec-react)**: contains information related to the React technology of the project, used for the user interface in web browsers. Check out our [code_style_reac.md](CODE_STYLE_REACT.md).
 - **[solarec-db](https://github.com/Renovus-Tech/solarec-db)**: contains information regarding the database structure of the project. It contains a series of files that allow the creation of an empty valid database. Check out our [code_style_SQL.md](CODE_STYLE_SQL.md).

In order to collaborate in one o more of the Renovus Solarec repositories, please request access in each one of the repositories.
