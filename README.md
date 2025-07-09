# 🌦️ Weather Dashboard using WeatherAPI and Power BI

This project is an interactive **Weather Analytics Dashboard** built using **Power BI**, integrating real-time weather data through the **WeatherAPI.com** service. It displays live weather conditions, forecast data, and environmental metrics for multiple cities in a clean and engaging format.

---

## 📌 Project Overview

The dashboard fetches real-time and forecast weather data using a **REST API** from [https://www.weatherapi.com](https://www.weatherapi.com), dynamically visualizing key meteorological and environmental indicators such as:

- 🌡️ Temperature (Current & 7-Day Forecast)
- ☀️ Sunrise & Sunset Times
- 🌧️ Precipitation & Chance of Rain
- 🌫️ Visibility, Humidity, Pressure, Wind Speed
- 🌍 Air Quality Index (AQI) with PM10, PM2.5, SO2, CO, NO2, and O3 levels
- 📍 City selection for **dynamic weather comparison** (e.g., Manali, Ahmedabad, Ajmer, Hyderabad)
- 🕒 Real-Time Timestamp: “Last Updated” using `NOW()` in DAX

---

## 🔗 Data Source

- **API Provider**: [WeatherAPI.com](https://www.weatherapi.com)
- **Endpoints Used**:
  - `/v1/current.json`
  - `/v1/forecast.json`
- **Authentication**: API Key (passed as query parameter)
- **Method**: `Web.Contents()` in Power Query M

---

## ⚙️ Features & Tools Used

| Tool/Feature           | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| 🔗 API Integration      | Real-time weather pulled directly using `Web.Contents()`                    |
| 🧠 DAX Measures          | `NOW()`, conditional formatting, and dynamic titles                         |
| 📈 Visualizations       | Line charts, cards, gauges, bar charts, and custom icons                    |
| 🧩 Parameters & Filters | City selection using bookmarks and slicers                                  |
| 🎨 UI/UX                | Dark theme with soft highlights for intuitive experience                    |
| 🔁 Auto Refresh         | Scheduled refresh enabled via Power BI Service                              |

---

## 💡 Key DAX Formulas

```dax
-- Last Updated Time
LastUpdated = NOW()

-- Weather Category (Dynamic Label)
WeatherConditionLabel = 
SWITCH(TRUE(),
    'Weather'[Condition] = "Patchy light rain", "🌧️ Light Rain",
    'Weather'[Condition] = "Sunny", "☀️ Sunny",
    'Weather'[Condition] = "Cloudy", "☁️ Cloudy",
    "🌤️ Varying"
)

-- AQI Status
AQI_Status = 
SWITCH(TRUE(),
    'AQI'[PM10] <= 50, "Good",
    'AQI'[PM10] <= 100, "Moderate",
    'AQI'[PM10] <= 200, "Unhealthy",
    "Hazardous"
)
```

---

## 📊 Dashboard Preview

![Weather Dashboard Screenshot](./assets/weather-dashboard-preview.png)

---

## 🔄 How Refresh Works

- Data is refreshed on **Power BI Service** using **Scheduled Refresh**
- Uses `DateTime.LocalNow()` in Power Query to force new API calls on each load
- Anonymous authentication is set in **Data Source Credentials** for API access
- Refresh history and status is monitored under dataset settings in Power BI Service

---

## ✅ Benefits of This Project

- Real-world use of **REST APIs** in Power BI
- Hands-on experience with **DAX**, **Power Query**, and **custom visualizations**
- Showcases ability in **data storytelling**, **real-time analytics**, and **cloud refresh automation**
- Demonstrates UI/UX design using dark theme with clean KPIs

---

## 📁 Folder Structure

```bash
📦WeatherDashboard
 ┣ 📄 WeatherDashboard.pbix
 ┣ 📄 README.md
 ┣ 📁 assets/
 ┃ ┗ 📸 weather-dashboard-preview.png
 ┗ 📁 documentation/
   ┗ 📄 WeatherAPI_QueryStructure.docx
```

---

## 📬 Contact

For any queries or collaboration requests, feel free to reach out via [ahadalyani9@gmail.com/8879178223].

---

> ⭐ *Don’t forget to give a star if you find this project useful!*
