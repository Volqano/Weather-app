# Weather App

The app displays the weather for a selected city. Upon the first launch, the app checks the user's location and shows the weather for the city they are currently in.

- **Current weather**: Weather icon, temperature, weather description, precipitation, wind speed, cloud cover.
- **Hourly forecast**: For each hour, the temperature and an icon showing the corresponding weather are displayed.
- **7-day forecast**: For each day, the minimum and maximum temperatures, as well as an icon representing the predominant weather of the day, are shown.

A search bar allows users to enter a city name. After clicking the magnifying glass icon, the app will display the weather for the searched city. The app also allows switching between light and dark modes.

## Class descriptions

**Weather** - Main weather class
- `int weatherCode`: Weather condition, e.g., sunny, rainy, etc.
- `double temperature`
- `bool? day`: Day - true | Night - false

**CurrentWeather** - Inherits fields from Weather, holds data for the current weather
- `int precipitation`: Chance of precipitation
- `double windSpeed`
- `int cloudCover`

**HourlyWeather** - Inherits fields from Weather, holds data for the hourly weather
- `int hour`

**DailyWeather** - Inherits fields from Weather, holds data for the daily weather
- `String dayOfWeek`
- `double minTemperature`
- `double maxTemperature`

**ThemeProvider** - Manages light and dark mode
- `ThemeData _themeData`: Stores the current theme
- `void toggleTheme()`: Switches to the opposite theme

**WeatherApi** - Handles updating data from the weather API we are using
- `String url`: API address
- `String urlRest`: Stores the remaining part of the API address after the key
- `Future<Map<String, dynamic>> fetchData(String city) async`: Fetches data from the API and checks if the request was successful
- `Future<CurrentWeather> getCurrentWeather(String city) async`: Processes fetched data and creates a `CurrentWeather` instance with this data
- `Future<List<HourlyWeather>> getHourlyWeather(String city) async`: Processes fetched data and creates `HourlyWeather` instances for each hour
- `Future<List<DailyWeather>> getDailyWeather(String city) async`: Processes fetched data and creates `DailyWeather` instances for each day
