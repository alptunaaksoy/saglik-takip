# Sağlık Takip

A Flutter health-tracking app with a lightweight FastAPI service that provides Turkish-language, AI-assisted health information using recent pulse and blood-pressure readings.

## Technology

- **Mobile app:** Flutter and Dart
- **Authentication:** Firebase Authentication
- **Backend:** FastAPI, Python, and the OpenAI API
- **Local assistant context:** a small RAG knowledge file (`backend/rag_data.txt`)

## Features

- User sign-in and registration
- Pulse and blood-pressure tracking
- AI health information based on a question and recent readings
- Basic risk-oriented guidance with prompts to seek professional or emergency care for serious symptoms

The assistant is informational and does not provide a diagnosis or replace a healthcare professional.

## Run locally

### Prerequisites

- Flutter SDK and an Android emulator or device
- Python 3.10 or newer
- A Firebase project with Authentication enabled
- An OpenAI API key for the backend assistant

### Start the backend

```powershell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
```

Add your key to `backend/.env` as `OPENAI_API_KEY`, then start the API from the `backend` directory:

```powershell
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

The Android emulator URL is currently `http://10.0.2.2:8000/chat`. For a physical device, update the app's backend URL in `lib/main.dart` to the reachable address of your development machine.

### Configure and run the app

1. Create a Firebase project and enable Authentication. Download `google-services.json` for Android to `android/app/`, and use FlutterFire CLI (`dart pub global activate flutterfire_cli`, then `flutterfire configure`) to generate `lib/firebase_options.dart`. These project-specific client configuration files are ignored by Git; generate your own locally.
2. From the project root, run:

   ```powershell
   flutter pub get
   flutter run
   ```

## Security and health data

Never commit `.env` or real API keys. Copy `backend/.env.example` to a local `.env` and provide your own key. Do not use real patient information in public demos or sample data. Review Firebase Authentication and security settings before connecting a public app.

