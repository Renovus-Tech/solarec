# Renovus Solarec


Pending: add information regarding UNICEF Venture Found

# The repositories
**Renovus Solarec Open Source** solution is divided in various repositories that are technology dependent and that have specific goals. The repositories are:
- **solarec-java**: contains information related to the Java technology of the proyect. The Java code is divided into a series of sub-repositories, in order to garantee a complete independence, portability and extensibility.
	- **solarec-java-interfaces**: Contains all the interface definitions of the proyects. Sub repositories will required the information of these repository in order to implement and internaction with other parts of the code.
	- **solarec-java-db**: contains all the required code to access the database and information stored there.
	- **solarec-java-inverters**: contains the code to connect to different inverter manufacturers.
	- **solarec-java-implementations**: contains the main inmplementatins of the interface required for the execution of the solution. All non-specific implementations are here.
	- **solarec-java-schedule**: contains all the code that will run on background and therefore no GUI is required.
	- **solarec-java-core**: contains all main API Rest code that will allow the interaction with different GUI.
-   **solarec-python**: contains information related to the Python technology of the proyect. The Python code is divided into a series of sub-repositories, in order to garantee a complete independence, portability and extensibility.
	-   **solarec-python-core**: main code and API Rest endpoints to allow the interaction with other GUI.
	-   **solarec-python-calculations**: code with the different calculations that are executed with the corresponding data.
	-   **solarec-python-ml**: code related to the machine learning.
- **solarec-react**: contains information related to the React technology of the proyect. The React code is divided into a series of sub-repositories, in order to garantee a complete independence, portability and extensibility.
	-   **solarec-react-core**: main GUI for the final user.
	-   **solarec-react-elements**: React components used to generate the main GUI.

In order to collaborate in one o more of the Renovus Solarec repositories, please request access in each one of the repositorioes.
