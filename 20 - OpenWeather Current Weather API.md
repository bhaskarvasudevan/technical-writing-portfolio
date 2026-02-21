# API Overview
The Current Weather API retrieves the real-time weather data for a geographical location using its latitude and longitude.
* The API is an HTTP GET endpoint.
* The response format is JSON by default.
* The API returns meteorological data such as temperature, humidity, atmospheric pressure, wind speed, and weather conditions.

# Endpoint
The API endpoint is: **GET https://api.openweathermap.org/data/2.5/weather** 

# Authentication
This API requires an appid query parameter set to a valid API key.
You can find your unique API key on your account page under the API keys tab. 

# Request Parameters
The API has the following request parameters:

| Parameter | Type   | Required | Default  | Allowed Values                | Description                                                |
| --------- | ------ | -------- | -------- | ----------------------------- | ---------------------------------------------------------- |
| lat       | float  | Yes      | —        | Valid latitude (-90 to 90)    | Geographic latitude coordinate of the requested location.  |
| lon       | float  | Yes      | —        | Valid longitude (-180 to 180) | Geographic longitude coordinate of the requested location. |
| appid     | string | Yes      | —        | Valid API key                 | Unique API key used for authentication.                    |
| units     | string | No       | standard | standard, metric, imperial    | Unit system used for temperature and wind speed values.    |
| mode      | string | No       | json     | xml, html                     | Response format. JSON is returned by default.              |
| lang      | string | No       | en       | ISO language codes            | Language used for weather description fields.              |

   
# Example Request



# Example Response

# Error Codes

# Rate Limits
