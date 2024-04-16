# Getting started with Calculations API development

- [Project overview](https://renovus-tech.github.io/solarec/documentation/python/)
- [Environment setup](https://github.com/Renovus-Tech/solarec-python/blob/main/README.md)

## Adding a new endpoint

- Add a new file for the new endpoint under ```/endpoints```
- Add a new DTO defining the schema for the request and response of the new endpoint.
   - Check existing endpoints to make sure it's consistent with the current standard. 
- Add the endpoint route definition.
   - Check existing endpoints to make sure it's consistent with the current standard.
- New business logic / calculations should be implemented under ```/core```.
- Data access is implemented under ```/db```, e.g. if you need a to access a new piece of data, you can add a class/function there.
- Add the orchestration logic in the added endpoint file.
- Include the endpoint's routing under ```main.py```.

## Manual testing

- Once everything is setup, you can locally run the API using ```uvicorn```.
- You can easily access the API's auto-generated OpenAPI documentation from the browser at ```[API_HOST]:[API_PORT]/docs```.

## Unit testing

- Check ``/tests``` for examples on how to add a test for the new endpoint.
   - Consider using ```mock_alchemy``` to mock the database.