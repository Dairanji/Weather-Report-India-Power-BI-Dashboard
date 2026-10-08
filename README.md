# Weather Report India – Power BI Dashboard

An interactive Power BI dashboard showing live conditions, a 7-day forecast and air quality for **28 Indian cities** (state and UT capitals), built from the WeatherAPI.com forecast API.

![Weather Report India](images/weather-dashboard-preview.png)

## Problem
- Weather for different Indian cities sits on separate pages, so comparing cities or checking air quality and rain chances together takes several lookups.
- Raw API data comes as nested JSON, one response per city, and is not report-ready.

## Solution
One dashboard page where picking a city shows everything about it:

| Section | What it shows |
|---------|---------------|
| City card | Current temperature, condition and date, with a city switcher |
| Weekday cards | Average temperature for each of the next 7 days |
| Weather Forecast | 7-day temperature trend |
| Sunrise & Sunset | Times for the selected city |
| Chance Of Rain | Daily rain probability |
| Humidity, Visibility, Wind, Pressure, UV, Precipitation | Current readings |
| Air Quality | PM10 donut with status text, plus PM2.5, SO2, O3, CO and NO2 |

## Data
| Item | Details |
|------|---------|
| Source | WeatherAPI.com `forecast.json` (free plan) |
| Coverage | 28 cities, one query each |
| Forecast | 7 days, 27 Sep – 3 Oct 2026, with air quality |
| Snapshot | Saved on 27 Sep 2026, 12:45; refreshes live with your own API key |

## Dashboard for Each City
Full-page PDF of the dashboard for every city (open from the `city_reports` folder):

| | | | |
|---|---|---|---|
| [Agartala](city_reports/weather_report_india_agartala.pdf) | [Aizawl](city_reports/weather_report_india_aizawal.pdf) | [Amaravati](city_reports/weather_report_india_amaravati.pdf) | [Bengaluru](city_reports/weather_report_india_bengaluru.pdf) |
| [Bhopal](city_reports/weather_report_india_bhopal.pdf) | [Bhubaneswar](city_reports/weather_report_india_bhubaneswar.pdf) | [Chandigarh](city_reports/weather_report_india_chandigarh.pdf) | [Chennai](city_reports/weather_report_india_chennai.pdf) |
| [Dehradun](city_reports/weather_report_india_dehradun.pdf) | [Delhi](city_reports/weather_report_india_delhi.pdf) | [Dispur](city_reports/weather_report_india_dispur.pdf) | [Gandhinagar](city_reports/weather_report_india_gandhinagar.pdf) |
| [Gangtok](city_reports/weather_report_india_gangtok.pdf) | [Hyderabad](city_reports/weather_report_india_hyderabad.pdf) | [Imphal](city_reports/weather_report_india_imphal.pdf) | [Itanagar](city_reports/weather_report_india_itanagar.pdf) |
| [Jaipur](city_reports/weather_report_india_jaipur.pdf) | [Kohima](city_reports/weather_report_india_kohima.pdf) | [Kolkata](city_reports/weather_report_india_kolkata.pdf) | [Lucknow](city_reports/weather_report_india_lucknow.pdf) |
| [Mumbai](city_reports/weather_report_india_mumbai.pdf) | [Panaji](city_reports/weather_report_india_panaji.pdf) | [Patna](city_reports/weather_report_india_patna.pdf) | [Raipur](city_reports/weather_report_india_raipur.pdf) |
| [Ranchi](city_reports/weather_report_india_ranchi.pdf) | [Shillong](city_reports/weather_report_india_shillong.pdf) | [Shimla](city_reports/weather_report_india_shimla.pdf) | [Thiruvananthapuram](city_reports/weather_report_india_thiruvananthapuram.pdf) |

## How It Was Built
- **Power Query:** 28 per-city API queries (one `Web.Contents` call each), combined into `WeatherReport_MasterTable`, then split into `Current`, `Forcast_Day` and `Forcast_Hour` tables. Nested JSON records are expanded into columns.
- **DAX:** measures for unit-formatted values (°C, Kph, Km), rain "remaining" bars, pollutant colour rules, and air quality status and advice text.
- **Visuals:** cards, line chart, 100% stacked bar chart, donut chart, tile slicers for the city switcher, and custom shapes and icons.

**Tools:** Power BI Desktop, Power Query (M), DAX, WeatherAPI

## API Key
The API key used to build this report is **revoked**, so the `.pbix` opens with the saved 27 Sep 2026 data. To get live data, add your own free key from [weatherapi.com](https://www.weatherapi.com):
1. In Power BI Desktop, open **Home → Transform data**, pick a city query and select its **Source** step.
2. Replace the text after `key=` in the URL with your key. Repeat for each city query, then **Close & Apply**.

## Notes
- The 28 cities are 26 state capitals plus Chandigarh and Delhi. Haryana and Punjab are covered by Chandigarh.
- The air quality donut and status text use the **PM10** reading with simplified bands. It is an indicator, not the official Indian AQI.

## Files
```
├── README.md
├── weather_report_india_portfolio_project.pbix   # Full report (open in Power BI Desktop)
├── images/
│   └── weather-dashboard-preview.png
└── city_reports/                                  # 28 dashboard PDFs, one per city
```

## Author
**Shayantan Mitra** – Data Reporting & Operations Analyst
[LinkedIn](https://www.linkedin.com/in/shayantanmitra96) · [GitHub](https://github.com/Dairanji)
