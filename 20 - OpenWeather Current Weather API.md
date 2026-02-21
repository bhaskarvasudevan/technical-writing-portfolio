## API Overview
The Current Weather API retrieves the real-time weather data for a geographical location using its latitude and longitude.
* The API is an HTTP GET endpoint.
* The response format is JSON by default.
* The API returns meteorological data such as temperature, humidity, atmospheric pressure, wind speed, and weather conditions.

## Endpoint
The API endpoint is: **GET https://api.openweathermap.org/data/2.5/weather** 

## Authentication
This API requires an **appid** query parameter set to a valid API key.
You can find your unique API key on your account page under the **API keys** tab. 

## Request Parameters
The API has the following request parameters:

| Parameter | In    | Type   | Required | Default             | Allowed Values                   | Description                                                                                                      |
| --------- | ----- | ------ | -------- | ------------------- | -------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| lat       | query | float  | Yes      | —                   | Valid latitude (-90 to 90)       | Geographic latitude coordinate of the requested location.                                                        |
| lon       | query | float  | Yes      | —                   | Valid longitude (-180 to 180)    | Geographic longitude coordinate of the requested location.                                                       |
| appid     | query | string | Yes      | —                   | Valid API key                    | Unique API key used for authentication.                                                                          |
| units     | query | string | No       | `standard`          | `standard`, `metric`, `imperial` | Unit system used for temperature and wind speed values. Defaults to **standard** if not specified.               |
| mode      | query | string | No       | JSON (implicit)     | `xml`, `html`                    | Response format. Defaults to **JSON** if not specified.                                                          |
| lang      | query | string | No       | `en`                | ISO language codes               | Language used for weather description fields. Defaults to English (**en**) if not specified.                     |

   
## Example Request



## Example Response

## Error Codes

## Rate Limits
