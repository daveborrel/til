# Earthlens

Google Earth Engine is an API to extract images from satelites along with their associated GPS data.

## Creating a Project on Google Earth Engine

### Registering your project on Google's Website

1. In order to use earth engine, create a cloud project that has earth engine enabled.
2. Google has a console on a web browser that you can access to create a project related to space.
3. Register your project for non commercial use (If you're just doing this for a project)
   - Google has documentation that describes use case on whether or not your
4. Once you register, enable the API.

### Installing the Earth Engine Python Client Library

1. `pip install earthengine-api --upgrade` command used to keep the client library up to date
2. Ensure that you are authenticated.

```python
import ee

# Trigger the authentication flow.
ee.Authenticate()

# Initialize the library.
ee.Initialize(project='my-project')

# This should return a string in the terminal.
print(ee.String('Hello from the Earth Engine servers!').getInfo())
```

### Earth Engine Data Catalog

There are many different types.

## Sources

[Official Earth Engine API](https://github.com/google/earthengine-api)
[Earth Engine Python Client Installation](https://developers.google.com/earth-engine/guides/python_install)
[Google's own code editor](https://code.earthengine.google.com/)
[Visualizing the responses from Google Earth API](https://github.com/gee-community/geemap)
