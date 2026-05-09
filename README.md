# 🌤️ Flutter Weather App

A professional, real-time weather forecasting application built with Flutter. This project serves as a comprehensive demonstration of core Flutter concepts, including asynchronous programming, API integration, and dynamic UI rendering.

---

## 🚀 Overview

The **Flutter Weather App** provides users with up-to-the-minute weather data using the OpenWeather API. It features a clean, Material 3 dark-themed interface that displays current weather conditions, an hourly forecast, and detailed metrics like humidity, wind speed, and pressure.

This project was built with a focus on **educational best practices**, showcasing how to handle real-world data fetching and state management in a Flutter environment.

## ✨ Features

-   **Real-time Data:** Fetches live weather information from the OpenWeather API.
-   **Hourly Forecast:** Displays a scrollable list of weather predictions for the coming hours.
-   **Detailed Metrics:** Provides specific data points: Humidity, Wind Speed, and Atmospheric Pressure.
-   **Material 3 Design:** A modern, dark-themed UI with glassmorphism effects (blur).
-   **Responsive Layout:** Uses reusable widgets and flexible layouts to ensure consistency across devices.
-   **Refresh Functionality:** Instantly update weather data with a single tap.

## 🛠️ Tech Stack

-   **Language:** [Dart](https://dart.dev/)
-   **Framework:** [Flutter](https://flutter.dev/)
-   **API:** [OpenWeather API](https://openweathermap.org/api)
-   **Packages:**
    -   `http`: For making asynchronous network requests.

---

## 📁 Project Structure

The project follows a modular structure to promote reusability and maintainability:

```text
lib/
├── main.dart             # Application entry point & Theme configuration
├── weather_screen.dart    # Primary UI and API logic
├── forecast_card.dart     # Reusable widget for hourly forecast items
├── additional_info.dart   # Reusable widget for weather metrics
└── secrets.dart          # Sensitive data (API Keys) - [Ignored by Git]
```

---

## 🧠 Core Concepts & Learnings

### ⏳ Asynchronous Programming
In Flutter, network requests are "expensive" operations that take time. To prevent the UI from freezing while waiting for a response, we use `async` and `await`.
-   `async` marks a function as asynchronous.
-   `await` pauses the execution of the function until the `Future` (the API response) completes.

### 🏗️ FutureBuilder & UI Lifecycle
The `FutureBuilder` widget is a powerful tool for handling asynchronous data. It allows the UI to react to different states of a data fetch:
-   **Waiting:** Shows a loading spinner (`CircularProgressIndicator`).
-   **Success:** Renders the weather data once `snapshot.hasData` is true.
-   **Error:** Displays an error message if the request fails.

This ensures a smooth user experience where the app remains interactive even during data retrieval.

### 🌐 API Integration & Security
The app communicates with OpenWeather via **HTTP GET requests**. 
-   **Security:** To protect my personal API key, I stored it in a separate `secrets.dart` file which is excluded from version control using `.gitignore`. This is a critical industry standard for protecting sensitive credentials.

### 📊 JSON Parsing
Data from the web arrives as a long string (JSON). We use `jsonDecode(res.body)` to convert this string into a `Map<String, dynamic>`, making it easy to access nested fields like `data['list'][0]['main']['temp']`.

### 📱 Dynamic UI with ListView.builder
Instead of rendering all forecast items at once, we use `ListView.builder`. This is an **optimization technique** that only builds the items currently visible on the screen (lazy loading), which significantly improves performance for larger datasets.

### 🔄 State Updates (Refresh Logic)
The refresh button uses `setState(() {})`. Even though no local variables are explicitly changed, calling `setState` triggers a rebuild of the `WeatherScreen`, which re-executes the `FutureBuilder` and fetches fresh data from the API.

---

## 🚀 Setup & Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/weather_app.git
    cd weather_app
    ```

2.  **Install dependencies:**
    ```bash
    flutter pub get
    ```

3.  **Setup API Key:**
    -   Create a file named `lib/secrets.dart`.
    -   Add your OpenWeather API key:
    ```dart
    const openWeatherAPIKey = 'YOUR_API_KEY_HERE';
    ```

4.  **Run the application:**
    ```bash
    flutter run
    ```

---

## 🔮 Future Roadmap

-   [ ] **City Search:** Allow users to search for weather by city name.
-   [ ] **Unit Conversion:** Toggle between Celsius and Fahrenheit.
-   [ ] **Enhanced Visuals:** Add dynamic icons based on weather conditions (Rain, Sun, Snow).
-   [ ] **State Management:** Implement Provider or Riverpod for more robust state handling.
-   [ ] **Local Storage:** Save the last searched city using `shared_preferences`.
-   [ ] **Daily Forecast:** Expand from hourly to a 7-day forecast.

---

## 🎓 What I Learned
Through this project, I strengthened my understanding of:
-   The **Widget Tree** and how `BuildContext` works.
-   Handling **REST APIs** and managing network errors gracefully.
-   The difference between **Stateless** and **Stateful** widgets.
-   Standard **Git/GitHub workflows** for project documentation and security.

---

## 👤 Author

**Fawaz**
-   GitHub: [fwz-blk](https://github.com/fwz-blk)


---
*Developed as part of my Flutter development journey. 🚀*
