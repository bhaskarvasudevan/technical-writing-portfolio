# API Overview
The Current Weather API retrieves the real-time weather data for a geographical location using its latitude and longitude.
* The API is a http GET endpoint.
* The response format is JSON by default.
* The API returns meteorological data like temperature, humidity, wind, etc.

# Base URL
The base URL for the API is:
GET https://api.openweathermap.org/data/2.5/weather

# Authentication
Authentication for this API is via an appid query parameter set to your unique API key.
You can find your unique API key on your account page under the API keys tab. 

# Request Parameters
The API has the following request parameters:

## lat
Latitude
   - **Name**: lat
   - **Type**: string
   - **Required**: Yes
   - **Description**: Latitude

## long 
   - **Name**: lon
   - **Type**: string
   - **Required**: Yes
   - **Description**: Longitude

## appid 
   - **Name**: appid
   - **Type**: string
   - **Required**: Yes
   - **Description**: API key. You can find your unique API key on your account page under the **API key** tab.

## mode 
   - **Name**: mode
   - **Type**: string
   - **Required**: No
   - **Description**: Response format. If used, possible values are: **xml** and **html**. If this parameter is not used, **JSON** is the default format.

## units
   - **Name**: units
   - **Type**: string
   - **Required**: No
   - **Description**: Units of measurement. Possible values are: **standard**, **metric** and **imperial**. If this parameter is not used, **standard** is the default unit.

## lang 
   - **Name**: lang 
   - **Type**: string
   - **Required**: No
   - **Description**: Output language. Language in which the response is displayed. If this parameter is not used, then **US English (en-US)** is the default language. 
  
   
# Example Request



# Example Response

# Error Codes

# Rate Limits
