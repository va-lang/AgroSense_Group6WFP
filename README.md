# MaizeSecure

MaizeSecure is an AI powered web application that helps Ghanaian maize farmers detect Fall Armyworm infestations from a simple photo or video of a maize leaf. It gives an instant severity result, plain language treatment advice in English or Twi, and a dashboard for tracking outbreaks across Ghana's regions.

This project was built by Group 6 as part of the WFP program.

## What This App Does

1. A farmer or extension officer signs in to the app.
2. They upload a photo, take a photo with a camera, or upload a short video of a maize leaf.
3. An AI model (YOLOv8) scans the image and checks for signs of Fall Armyworm damage.
4. The app shows a result: Healthy, Early to Moderate, or Severe, along with a confidence score.
5. The app gives treatment recommendations based on the result, available in both English and Twi (with audio playback).
6. The farmer can download a report of the scan, and view past scans in a history page.
7. Extension officers see a regional dashboard with outbreak trends, a map of Ghana, and district level reports.

## Who This App Is For

- **Farmers**: scan crops, view results and advice, track scan history.
- **Extension Officers**: view a regional dashboard with outbreak trends and monitoring data across Ghana's 16 regions.

## Key Features

- Image, camera, and video based scanning
- AI severity classification: Healthy, Early to Moderate, Severe
- Treatment recommendations in English and Twi, with voice playback
- Downloadable scan reports
- Scan history with filtering by severity and date
- Regional outbreak dashboard with charts and a map of Ghana
- Built to work in the field, with a workflow designed for areas with limited internet

## Project Structure

```
MaizoraAI_Group6WFP/
├── agrosense.py                        # Main Streamlit app: pages, navigation, and UI logic
├── app_components.py                   # Reusable UI pieces (cards, alerts, badges, theme)
├── app_data.py                         # Static data used in the app (recommendations, regional data, text)
├── model_service.py                    # Runs the AI model on images and videos to get predictions
├── storage_service.py                  # Saves and retrieves scan history from the database
├── maizesecure_scans.db                # SQLite database that stores scan history
├── requirements.txt                    # Python packages needed to run the app
├── packages.txt                        # System level packages needed (for deployment)
├── fall_armyworm_production/           # Model files and related resources
├── fall_armyworm_production_version_3/ # A newer version of the model files
├── voicescript/                        # Audio files for English and Twi voice guidance
├── .streamlit/                         # Streamlit configuration files
└── .devcontainer/                      # Development container configuration
```

## How the App Is Built

- **Frontend and app logic**: [Streamlit](https://streamlit.io/), a Python framework for building web apps
- **AI model**: [YOLOv8](https://github.com/ultralytics/ultralytics) (via the `ultralytics` package), trained to detect Fall Armyworm damage on maize leaves
- **Image and video processing**: OpenCV
- **Data storage**: SQLite (a lightweight file based database)
- **Language support**: English and Twi, including recorded audio guidance

## Requirements

- Python 3.9 or newer
- pip (Python package manager)

## Setup Instructions

1. Clone the repository:
   ```
   git clone https://github.com/va-lang/MaizoraAI_Group6WFP.git
   cd MaizoraAI_Group6WFP
   ```

2. Create a virtual environment (recommended):
   ```
   python -m venv venv
   source venv/bin/activate
   ```
   On Windows, use `venv\Scripts\activate` instead.

3. Install the required Python packages:
   ```
   pip install -r requirements.txt
   ```

4. If you are deploying to a Linux server or a platform like Streamlit Community Cloud, also make sure the packages listed in `packages.txt` are installed on the system, since some of them are needed for video and image processing to work correctly.

## Running the App

From the project folder, run:

```
streamlit run agrosense.py
```

This will start a local web server. Streamlit will show a local URL in the terminal, usually something like `http://localhost:8501`. Open that link in your browser to use the app.

## Using the App

1. On the sign in page, choose whether you are signing in as a Farmer or as an Extension Officer.
2. Enter the requested details and sign in.
3. As a Farmer:
   - Go to "Scan Crop" and choose Image, Camera, or Video as your input.
   - Upload or capture a clear photo of a maize leaf, or a short video, and press "Analyze Crop."
   - View your result on the Results page, switch between English and Twi, listen to the voice guidance, and download a report if needed.
   - Visit "History" to see and filter past scans.
4. As an Extension Officer:
   - View the regional dashboard, which shows outbreak trends, a map of Ghana, and district level reports.

## Notes on the AI Model

- The model was trained to recognize three categories: Healthy, Early to Moderate, and Severe Fall Armyworm damage.
- Two versions of the trained model are included in the repository (`fall_armyworm_production` and `fall_armyworm_production_version_3`), with the newer version reflecting further training improvements.
- The recommendations shown in the app are intentionally kept general and are not a substitute for guidance from a trained agricultural extension officer.

## Disclaimer

MaizeSecure is a student project built for learning and demonstration purposes. The predictions and recommendations it provides should not be treated as a final or complete agronomic diagnosis. For serious or unclear infestations, farmers should consult a local agricultural extension officer.

## Contributors

Built by Group 6 as part of a Data Science and AI training program, focused on applying AI to agricultural challenges in Ghana.
