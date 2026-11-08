# PredictiveMaintain – AI-Based Predictive Maintenance System

An intelligent predictive maintenance application that uses Machine Learning and real-time sensor data to predict potential equipment failures before they occur.

The system analyzes industrial sensor parameters such as voltage, current, temperature, power, vibration, and humidity using a trained **Random Forest Classifier**. It provides manual predictions, automated predictions, and IoT-based sensor monitoring through an interactive web dashboard.

## 🚀 Features

- **Machine Learning Prediction:** Uses a trained Random Forest model to predict equipment failure.
- **Real-Time Sensor Monitoring:** Processes sensor readings to monitor equipment conditions.
- **Manual Prediction:** Allows users to enter sensor values and receive predictions.
- **Automatic Prediction:** Generates simulated sensor readings and continuously evaluates equipment conditions.
- **IoT Integration:** Accepts sensor data through REST API endpoints.
- **Weather API Integration:** Retrieves live temperature and humidity data using OpenWeatherMap.
- **Vibration Calculation:** Estimates vibration based on current readings with simulated noise.
- **Interactive Dashboard:** Displays system health, prediction results, and prediction probabilities.
- **Data Visualization:** Provides graphical monitoring and prediction trends.
- **Cloud Deployment:** Supports deployment using Render.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend development |
| FastAPI | REST API development |
| Scikit-learn | Machine Learning |
| Random Forest | Predictive model |
| Pandas | Sensor data processing |
| NumPy | Numerical computations |
| Joblib | Model loading |
| HTML, CSS, JavaScript | Frontend dashboard |
| Chart.js | Data visualization |
| OpenWeatherMap API | Weather information |
| Render | Cloud deployment |

## 📂 Project Structure

```text
PredictiveMaintain/
│
├── main.py                    # FastAPI backend
├── app.py                     # Additional application module
├── index.html                 # Web dashboard
├── random_forest_model.pkl    # Trained ML model
├── sensor.jpeg                # Sensor visualization
├── requirements.txt           # Python dependencies
├── render.yaml                # Render deployment configuration
└── README.md                  # Project documentation
```

## ⚙️ Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/PredictiveMaintain.git
```

### 2. Navigate to the Project Directory

```bash
cd PredictiveMaintain
```

### 3. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / macOS:**
```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure OpenWeatherMap API

The application uses OpenWeatherMap to retrieve live temperature and humidity.

Create an API key at:

https://openweathermap.org/api

Configure the API key securely using an environment variable rather than hardcoding it in the source code.

### 6. Run the Application

```bash
uvicorn main:app --reload
```

### 7. Access the Application

Open your browser and visit:

```text
http://127.0.0.1:8000
```

FastAPI interactive API documentation:

```text
http://127.0.0.1:8000/docs
```

## 🤖 Machine Learning Model

The application uses a pre-trained Random Forest Classifier stored in:

`random_forest_model.pkl`

The model uses the following input features:

| Feature | Description |
|---|---|
| Voltage | Electrical voltage |
| Current | Electrical current |
| Temperature | Equipment temperature |
| Power | Electrical power |
| Vibration | Machine vibration level |
| Humidity | Environmental humidity |

The model generates:

- **Prediction:** Predicted class (0 or 1).
- **Probability:** Estimated probability associated with the positive class.

The prediction threshold is 0.5 when probability estimates are available.

*Note: The exact interpretation of classes 0 and 1 depends on the labels used when training the model.*

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Serves the dashboard |
| POST | `/predict/manual` | Predicts using manually entered sensor data |
| GET | `/predict/auto` | Generates simulated sensor data and predicts automatically |
| GET | `/predict/iotLive` | Retrieves the latest IoT prediction |
| POST | `/predict_iot` | Receives IoT sensor readings and processes them |

### Manual Prediction Example

**Request:**

`POST /predict/manual`

```json
{
  "voltage": 230,
  "current": 0.29,
  "temperature": 35,
  "power": 66.7,
  "vibration": 0.72,
  "humidity": 38
}
```

**Example Response:**

```json
{
  "prediction": "0",
  "probability": 0.12
}
```

*The response values above are illustrative.*

## 📊 Application Workflow

1. Collect sensor readings from manual inputs or IoT devices.
2. Process sensor parameters and calculate derived values such as power.
3. Retrieve environmental information when the weather API is available.
4. Prepare the sensor data in the required feature format.
5. Pass the processed data to the trained Random Forest model.
6. Generate the prediction and probability.
7. Display the results on the interactive dashboard.

## ☁️ Deployment

This project includes a `render.yaml` configuration for deployment on Render.

Basic deployment steps:

1. Push the project to a GitHub repository.
2. Log in to [Render](https://render.com/).
3. Create a new Web Service.
4. Connect your GitHub repository.
5. Configure the start command:

```bash
uvicorn main:app --host 0.0.0.0 --port 10000
```

6. Deploy the application.

Ensure that all required dependencies and model files are available during deployment.

## 🔮 Future Enhancements

- Integration with physical IoT sensors.
- Real-time monitoring using MQTT.
- Historical sensor data storage.
- Advanced failure prediction models.
- Maintenance alerts through email or notifications.
- Equipment health analytics and reporting.
- Improved prediction accuracy through continuous model training.

## 👨‍💻 Author

**Your Name**

GitHub: [Your GitHub Profile](https://github.com/YOUR_USERNAME)

## 📜 License

This project is intended for educational and research purposes. Add an appropriate open-source license if you intend to distribute or reuse the project publicly.
