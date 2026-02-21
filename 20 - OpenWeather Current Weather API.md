## API Overview
The Current Weather API retrieves real-time weather data for a specified geographical location using its latitude and longitude.
* The API is an HTTP GET endpoint.
* The response format is JSON by default.
* The API returns meteorological data such as temperature, humidity, atmospheric pressure, wind speed, and weather conditions.

## Endpoint
```
GET https://api.openweathermap.org/data/2.5/weather
```
Base URL: `https://api.openweathermap.org`
Resource Path: `/data/2.5/weather`

## Authentication
This API requires an **appid** query parameter set to a valid API key.
You can find your unique API key on your account page under the **API keys** tab. 
The **appid** must be passed as a query parameter in every request.
**Security Note**: Do not expose your API key in publicly accessible client-side applications.

## Request Parameters
The API has the following request parameters:

| Parameter | In    | Type   | Required | Default             | Allowed Values                   | Description                                                                                                      |
| --------- | ----- | ------ | -------- | ------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| lat       | query | number | Yes      | —                   | Range: -90 to 90                 | Geographic latitude coordinate of the requested location.                                                       |
| lon       | query | number | Yes      | —                   | Range: -180 to 180               | Geographic longitude coordinate of the requested location.                                                      |
| appid     | query | string | Yes      | —                   | Valid API key                    | Unique API key used for authentication.                                                                         |
| units     | query | string | No       | `standard`          | `standard`, `metric`, `imperial` | Unit system used for temperature and wind speed values. Defaults to **standard** if not specified.              |
| mode      | query | string | No       | `json`              | `json`, `xml`, `html`            | Response format. Defaults to **JSON** if not specified.                                                         |
| lang      | query | string | No       | `en`                | ISO language codes               | Language used for weather description fields. Defaults to English (**en**) if not specified.                    |

The table below shows details about the three types of units:

| Unit     | Temperature | Wind Speed |
| -------- | ----------- | ---------- |
| standard | Kelvin      | m/s        |
| metric   | Celsius     | m/s        |
| imperial | Fahrenheit  | mph        |

   
## Example Request
Here is an example request with minimal required parameters: 
```
curl "https://api.openweathermap.org/data/2.5/weather?lat=12.97&lon=77.59&appid=<API_KEY>"
```

Here is an example request with optional parameters:
```
curl "https://api.openweathermap.org/data/2.5/weather?lat=12.97&lon=77.59&units=metric&lang=fr&appid=<API_KEY>"
```

## Example Response
Here is an example response that uses default (`standard`) units. 
All responses are returned in JSON unless `mode` is changed. 
```
{
  "coord": { "lon": 77.59, "lat": 12.97 },
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "main": {
    "temp": 300.15,
    "humidity": 65,
    "pressure": 1013
  },
  "wind": {
    "speed": 3.6
  }
}
```

See the table below to interpret the fields in the response:  

| Field                 | Type   | Description                                           |
| --------------------- | ------ | ----------------------------------------------------- |
| coord.lat             | number | Latitude of the location                              |
| coord.lon             | number | Longitude of the location                             |
| weather[].main        | string | Group of weather parameters (e.g., Rain, Snow, Clear) |
| weather[].description | string | Weather condition description                         |
| main.temp             | number | Temperature (unit depends on `units` parameter)       |
| main.pressure         | number | Atmospheric pressure (hPa)                            |
| main.humidity         | number | Humidity percentage                                   |
| wind.speed            | number | Wind speed (unit depends on `units` parameter)        |


## Error Codes
Below are the error codes you may see from this API. Error responses are returned in `JSON` format. 
| HTTP Code | Meaning               |
| --------- | --------------------- |
| 400       | Invalid parameters    |
| 401       | Invalid API key       |
| 404       | Location not found    |
| 429       | Rate limit exceeded   |
| 500       | Internal server error |

Here is an example error response: 
```
{
  "cod": 401,
  "message": "Invalid API key"
}
```

## Rate Limits
Rate limits vary by subscription plan. Refer to your account dashboard for request quotas and throttling limits.
