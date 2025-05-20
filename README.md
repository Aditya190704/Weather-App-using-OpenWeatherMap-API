# Weather App using OpenWeatherMap API
This is a simple Python script that fetches and displays real-time weather information for any city using the OpenWeatherMap API.

## Features
  1. Get current weather data of any city
  2. Displays temperature, humidity, wind speed, and weather condition
  3. Uses free and public OpenWeatherMap API
  4. Outputs data in a clean and readable format

## Requirements
  1. Python 3.x
  2. requests module

### Install dependencies using:
        pip install requests

## How to Use
### Clone the repository:
    git clone https://github.com/your-username/weather-api-python.git
    cd weather-api-python
    
### Get your free API key from OpenWeatherMap

### Run the script:

import requests

def get_weather(city_name, api_key):
    base_url = "http://api.openweathermap.org/data/2.5/weather"
    params = {
        'q': city_name,
        'appid': api_key,
        'units': 'metric'
    }

    response = requests.get(base_url, params=params)

    if response.status_code == 200:
        data = response.json()
        weather_report = f"""
        🌍 Weather in {data['name']} ({data['sys']['country']}):
        🌡️ Temperature: {data['main']['temp']}°C
        ☁️ Weather: {data['weather'][0]['description'].title()}
        💧 Humidity: {data['main']['humidity']}%
        🌬️ Wind Speed: {data['wind']['speed']} m/s
        """
        print(weather_report)
    else:
        print("❌ Error: City not found or API limit exceeded.")

city = "Pune"
api_key = "your_api_key_here"
get_weather(city, api_key)


## Sample Output
🌍 Weather in Pune (IN):
🌡️ Temperature: 28.5°C
☁️ Weather: Clear Sky
💧 Humidity: 60%
🌬️ Wind Speed: 3.6 m/s
