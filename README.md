# Weather Application

## Transforming a CLI Weather App into a Full API-Driven Weather App

## 1️⃣ **Preparation: Setting Up the Project**

Before starting the transformation, we ensured that our project was well-structured and ready for development.

### **✅ Steps Taken:**

- Initialized a **Node.js backend** using Express.
- Installed necessary dependencies:
  ```sh
  npm install express cors dotenv axios
  ```
- Set up a `.env` file to store API keys securely.
- Created an **Express server (`server.js`)** to handle API requests.
- Installed **nodemon** for easier development:
  ```sh
  npm install -g nodemon
  ```

## 2️⃣ **Building the Backend API**

### **✅ Steps Taken:**

- Configured `server.js` with routes to fetch weather data.
- Used the **OpenWeather API** (or a similar service) to retrieve weather information.
- Created a route:
  ```js
  app.get("/weather/:city", async (req, res) => {
    const { city } = req.params;
    try {
      const response = await axios.get(
        `API_URL?q=${city}&appid=${API_KEY}&units=metric`
      );
      res.json({
        city: response.data.name,
        temp: response.data.main.temp,
        description: response.data.weather[0].description,
      });
    } catch (error) {
      res.status(400).json({ error: "City not found" });
    }
  });
  ```
- Enabled **CORS** for frontend communication.
- Tested the API using **Postman/Thunder Client** before moving to frontend integration.

## 3️⃣ **Creating the React Frontend**

### **✅ Steps Taken:**

- Initialized a React project:
  ```sh
  npx create-react-app weather-app
  ```
- Installed dependencies:
  ```sh
  npm install react-icons
  ```
- Created `WeatherComponent.jsx` for UI and state handling.
- Built `WeatherFetcher.jsx` to fetch data dynamically based on user input.

## 4️⃣ **Handling User Input & Fetching Data Dynamically**

### **✅ Steps Taken:**

- Used `useState` to manage the user’s city input.
- Created an input field to capture user input.
- Modified `WeatherFetcher.jsx` to dynamically fetch weather data when the user clicks a button.
- Updated error handling for a smoother user experience.

## 5️⃣ **Fixing UI Responsiveness Issues**

### **✅ Steps Taken:**

- Adjusted **CSS in `index.css`** to prevent layout issues:
  ```css
  body {
    display: flex;
    place-items: center;
    place-content: center;
    min-width: 320px;
    max-width: 100vw;
    min-height: 100vh;
    overflow-x: hidden;
    padding: 10px;
  }
  ```
- Added a `.app-container` to control content width:
  ```css
  .app-container {
    width: 100%;
    max-width: 450px;
    padding: 20px;
  }
  ```
- Ensured **the app remains centered** and **scales well on mobile screens.**

## 🎉 **Final Outcome & Success**

- **✅ A fully functional API-powered weather app** with dynamic input.
- **✅ A responsive and modern UI.**
- **✅ Improved error handling and state management.**
- **✅ Backend and frontend communicate seamlessly.**

---

This transition from CLI to API-driven frontend was a great exercise in **full-stack development, API handling, UI design, and responsiveness!** 🚀🔥
