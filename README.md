# London-Bike-Rides-Analysis

## Overview
This analysis explores bicycle usage patterns in London based on seasons and weather conditions. The data is analyzed to understand travel trends and factors affecting the number of cyclists, such as temperature, wind speed, and weather conditions.

## Data Processing
To ensure the data is more readable and analyzable, several transformations were applied:

### 1. Column Name Changes
The original column names were changed to more descriptive names using the following dictionary:
```python
new_cols_dict ={
    'timestamp':'time',
    'cnt':'count',
    't1':'temp_real_C',
    't2':'temp_feels_like_C',
    'hum':'humidity_percent',
    'wind_speed':'wind_speed_kph',
    'weather_code':'weather',
    'is_holiday':'is_holiday',
    'is_weekend':'is_weekend',
    'season':'season'
}

bikes.rename(new_cols_dict, axis=1, inplace=True)
```

### 2. Mapping Season Codes to Season Names
The `season` column, initially represented as numbers (0-3), was converted into meaningful season names:
```python
season_dict = {
    '0.0':'spring',
    '1.0':'summer',
    '2.0':'autumn',
    '3.0':'winter'
}

bikes.season = bikes.season.astype('str')
bikes.season = bikes.season.map(season_dict)
```

### 3. Mapping Weather Codes to Descriptive Weather Conditions
The `weather_code` column, originally numerical, was mapped to more informative weather descriptions:
```python
weather_dict = {
    '1.0':'Clear',
    '2.0':'Scattered clouds',
    '3.0':'Broken clouds',
    '4.0':'Cloudy',
    '7.0':'Rain',
    '10.0':'Rain with thunderstorm',
    '26.0':'Snowfall'
}

bikes.weather = bikes.weather.astype('str')
bikes.weather = bikes.weather.map(weather_dict)
```

## Insights
- Seasonal Trends: Bicycle usage increases during summer and decreases in winter.
- Weather Impact: Rain and snowfall significantly reduce the number of cyclists.
- Temperature & Wind Factors: More cyclists ride in warm temperatures with moderate wind speeds.

## Visualizations
The created dashboard displays:
1. Trends in bicycle usage from January 2015 to March 2017, with a moving average to highlight patterns.
2. The correlation between temperature and wind speed on ride frequency, shown using a heatmap.

## Conclusion
This analysis provides valuable insights for urban transportation planning and policymaking related to cycling. Weather and seasonal factors greatly influence the number of cyclists, which can be used as a basis for improving cycling infrastructure in London.

