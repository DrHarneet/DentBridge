# DentBridge - Doctor-Patient Communication Platform

DentBridge is an AI-powered web application that enables doctors to communicate complex dental treatment information to patients in their preferred language. The app provides a seamless multi-language experience with AI-generated explanations and real-time Q&A.

## Features

### 5-Screen Flow:

1. **Screen 1: Language Selection**
   - Doctor selects patient's preferred language
   - Supported languages: Hindi, Marathi, Punjabi, Telugu, Tamil, Bengali

2. **Screen 2: Doctor's Input**
   - Microphone button for voice input ("Hello Doctor, please tell me the case")
   - Text fields for:
     - Chief complaint
     - Diagnosis
     - Treatment plan
     - Cost
     - Number of appointments
     - Medications
     - Follow-up instructions
   - Proceed button to next screen

3. **Screen 3: Patient Explanation**
   - AI-generated explanation in simple, non-medical language
   - Visual tooth diagram
   - Audio playback option
   - "Understood" button to proceed

4. **Screen 4: Patient Q&A**
   - Microphone button for voice questions
   - Text input field for questions
   - Question counter (max 5 questions)
   - AI answers in patient's language
   - Question history display

5. **Screen 5: Thank You**
   - Warm closing message in patient's language
   - Contact information
   - Option to start new session

## Setup Instructions

### Prerequisites
- Python 3.8 or higher
- OpenAI API key
- Modern web browser with microphone access

### Installation

1. **Clone or extract the project**
   ```bash
   cd DentBridge
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   ```

3. **Activate virtual environment**
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

5. **Setup environment variables**
   - Copy `.env.example` to `.env`
   - Add your OpenAI API key:
     ```
     OPENAI_API_KEY=your_api_key_here
     ```

6. **Run the application**
   ```bash
   python app.py
   ```

7. **Access the app**
   - Open your browser and navigate to `http://localhost:5000`

## Project Structure

```
DentBridge/
├── app.py                 # Flask backend
├── requirements.txt       # Python dependencies
├── .env.example          # Environment variables template
├── README.md             # This file
├── templates/
│   └── index.html        # Main HTML template
└── static/
    ├── css/
    │   └── style.css     # Application styles
    └── js/
        └── main.js       # Frontend logic
```

## API Endpoints

### POST `/api/start-session`
Initialize a new session for doctor-patient interaction.

**Response:**
```json
{
  "session_id": "uuid",
  "success": true
}
```

### POST `/api/select-language`
Store selected language for current session.

**Request:**
```json
{
  "session_id": "uuid",
  "language": "hindi"
}
```

### POST `/api/doctor-input`
Save doctor's input about patient's case.

**Request:**
```json
{
  "session_id": "uuid",
  "chief_complaint": "...",
  "diagnosis": "...",
  "treatment": "...",
  "cost": "...",
  "appointments": "...",
  "medications": "...",
  "follow_up": "..."
}
```

### POST `/api/generate-explanation`
Generate AI explanation in patient's language.

**Response:**
```json
{
  "success": true,
  "explanation": "...",
  "language": "Hindi"
}
```

### POST `/api/patient-question`
Submit patient question and get AI response.

**Request:**
```json
{
  "session_id": "uuid",
  "question": "..."
}
```

**Response:**
```json
{
  "success": true,
  "answer": "...",
  "questions_remaining": 4,
  "language": "Hindi"
}
```

### POST `/api/closing-message`
Generate closing message in patient's language.

**Response:**
```json
{
  "success": true,
  "message": "...",
  "language": "Hindi"
}
```

## Speech Recognition

The app uses the Web Speech API for speech-to-text conversion. It automatically sets the language based on patient's selection:
- Hindi: `hi-IN`
- Marathi: `mr-IN`
- Punjabi: `pa-IN`
- Telugu: `te-IN`
- Tamil: `ta-IN`
- Bengali: `bn-IN`

## Future Enhancements

1. **Text-to-Speech Integration**
   - Integrate Google Cloud Text-to-Speech for audio explanations
   - Support for multiple voices

2. **Advanced Medical Diagrams**
   - Interactive tooth visualization
   - Before/after treatment comparisons
   - Step-by-step procedure illustrations

3. **Session Recording**
   - Store session data in database
   - Allow doctors to generate reports
   - Patient history tracking

4. **Multi-Format Support**
   - PDF report generation
   - WhatsApp integration
   - SMS notifications

5. **Analytics Dashboard**
   - Track consultations
   - Language usage statistics
   - Patient satisfaction metrics

## Troubleshooting

### Microphone not working
- Ensure browser has microphone permissions
- Check that you're using HTTPS or localhost
- Try a different browser

### Speech recognition not recognized
- Verify your internet connection
- Check browser compatibility (Chrome recommended)
- Ensure selected language is supported

### API errors
- Verify OpenAI API key is correct
- Check API account has available credits
- Ensure API key is not expired

## Browser Compatibility

- Chrome/Edge: Full support
- Firefox: Good support
- Safari: Partial support (may need permission prompts)

## License

This project is provided as-is for educational and commercial use.

## Support

For issues or questions, contact: support@dentbridge.com
