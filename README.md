# SnapClass - AI-Powered Attendance Management System 

## 📋 Project Overview

**SnapClass** is an intelligent attendance management system that leverages artificial intelligence to automate and streamline the attendance tracking process. The system uses facial recognition and voice recognition technologies to automatically mark attendance for students in an educational institution.

The project consists of two main components:
- **Main Application**: A Streamlit-based web portal for teachers and students
- **Landing Page**: A Flask-based informational website

---

## 🎯 Key Features

### For Teachers
- **Create & Manage Subjects**: Create subjects with unique codes and sections
- **Face-Based Attendance**: Use facial recognition to mark attendance automatically
- **Voice-Based Attendance**: Alternative attendance method using speaker identification
- **Photo Management**: Upload and manage student photos for face recognition training
- **Attendance Reports**: View detailed attendance statistics and history
- **Subject Sharing**: Share subjects with other teachers or generate join codes for students
- **Auto-Enrollment**: Support for automatic student enrollment via join codes

### For Students
- **Self-Enrollment**: Enroll in subjects using join codes
- **Auto Attendance**: Get marked present through face or voice recognition
- **Attendance Tracking**: View personal attendance statistics across all subjects
- **Multi-Biometric Support**: Use face or voice for attendance marking
- **Subject Management**: View and unenroll from subjects

### General Features
- **Secure Authentication**: User registration and login with password hashing (bcrypt)
- **Database Integration**: Supabase backend for reliable data storage
- **Multi-Modal Recognition**: Both facial and voice-based identification
- **User-Friendly Interface**: Streamlit-based responsive UI with custom styling
- **Real-Time Processing**: Instant attendance marking and updates

---

## 📁 Project Structure

```
Project/
├── Readme.md                                    # Main documentation
│
├── ai-attendance-project-app-main/              # Main Streamlit Application
│   ├── app.py                                   # Entry point of the application
│   ├── requirements.txt                         # Python dependencies
│   ├── README.md
│   │
│   └── src/
│       ├── components/                          # Reusable UI components
│       │   ├── dialog_add_photo.py             # Photo upload dialog
│       │   ├── dialog_attendance_results.py    # Attendance results display
│       │   ├── dialog_auto_enroll.py           # Auto-enrollment dialog
│       │   ├── dialog_create_subject.py        # Subject creation dialog
│       │   ├── dialog_enroll.py                # Student enrollment dialog
│       │   ├── dialog_share_subject.py         # Subject sharing dialog
│       │   ├── dialog_voice_attendance.py      # Voice attendance dialog
│       │   ├── footer.py                       # Footer component
│       │   ├── header.py                       # Header component
│       │   └── subject_card.py                 # Subject card display
│       │
│       ├── database/                            # Database operations
│       │   ├── config.py                       # Supabase client configuration
│       │   └── db.py                           # Database queries and operations
│       │
│       ├── pipelines/                           # AI/ML pipelines
│       │   ├── face_pipeline.py                # Face recognition implementation
│       │   └── voice_pipeline.py               # Voice recognition implementation
│       │
│       ├── screens/                             # Main application screens
│       │   ├── home_screen.py                  # Home page (login selection)
│       │   ├── teacher_screen.py               # Teacher portal
│       │   └── student_screen.py               # Student portal
│       │
│       └── ui/                                  # UI styling and layouts
│           └── base_layout.py                  # Base layout and styling
│
└── ai-attendance-project-landing-main/          # Flask Landing Page
    ├── app.py                                   # Flask application entry
    ├── requirements.txt                         # Python dependencies
    ├── README.md
    ├── vercel.json                              # Vercel deployment config
    │
    └── static/                                  # Static assets
        ├── css/
        │   └── style.css                        # Landing page styling
        ├── fonts/                               # Custom fonts
        ├── img/
        │   └── demo/                            # Demo images
        └── js/
            └── script.js                        # Client-side scripts
    
    └── templates/                               # HTML templates
        └── index.html                           # Landing page HTML
```

---

## 🛠 Technology Stack

### Backend & Framework
- **Streamlit**: Web application framework for the main application
- **Flask**: Lightweight framework for the landing page
- **Python 3.x**: Core programming language

### AI/ML Libraries
- **face_recognition**: Face detection and recognition
- **dlib**: Face detection and landmark detection
- **scikit-learn (SVM)**: Machine learning classifier for face recognition
- **resemblyzer**: Voice embedding generation
- **librosa**: Audio processing and analysis

### Database
- **Supabase**: PostgreSQL-based backend-as-a-service for data storage
- **bcrypt**: Password hashing and security

### Data Processing
- **NumPy**: Numerical computations
- **Pandas**: Data manipulation and analysis
- **Pillow**: Image processing

### Deployment
- **Gunicorn**: WSGI HTTP Server for production
- **Vercel**: Serverless deployment platform (configured)

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Supabase account with database setup
- Git

### Step 1: Clone the Repository
```bash
cd c:\Users\MUSKAN\OneDrive\Desktop\Project
```

### Step 2: Set Up Main Application (Streamlit)

```bash
cd ai-attendance-project-app-main

# Create virtual environment (optional but recommended)
python -m venv venv
venv\Scripts\activate  # On Windows
# or
source venv/bin/activate  # On macOS/Linux

# Install dependencies
pip install -r requirements.txt
```

### Step 3: Configure Supabase Credentials

Create a `.streamlit/secrets.toml` file in the `ai-attendance-project-app-main` directory:

```toml
SUPABASE_URL = "your_supabase_url"
SUPABASE_KEY = "your_supabase_key"
```

### Step 4: Run the Main Application
```bash
streamlit run app.py
```

The application will be available at `http://localhost:8501`

### Step 5: Set Up Landing Page (Flask) [Optional]

```bash
cd ../ai-attendance-project-landing-main

# Install dependencies
pip install -r requirements.txt

# Run the Flask application
python app.py
```

The landing page will be available at `http://localhost:5002`

---

## 📖 Usage Guide

### Teacher Workflow

1. **Registration/Login**: Teachers can register with a username, password, and name
2. **Create Subject**: Click "Create Subject" to add new subjects with:
   - Subject Code
   - Subject Name
   - Section Number
3. **Upload Photos**: Upload student photos for face recognition training
4. **Mark Attendance**:
   - Use face recognition: Capture or upload images
   - Use voice recognition: Record student voices
5. **View Reports**: Check attendance statistics and history
6. **Share Subject**: Generate join codes for student enrollment

### Student Workflow

1. **Registration/Login**: Students can register with name and optional biometric data
2. **Enroll in Subject**: Use join code provided by teacher or search for subject
3. **Mark Attendance**:
   - Face Recognition: Allow camera access for face detection
   - Voice Recognition: Record your voice for speaker identification
4. **View Attendance**: Check personal attendance records across all enrolled subjects
5. **Manage Enrollment**: Unenroll from subjects as needed

### Landing Page
- View project information and features
- Learn about the technology stack
- Direct access to the main application

---

## 🧠 AI/ML Architecture

### Face Recognition Pipeline
- **Detection**: Uses dlib's frontal face detector to locate faces in images
- **Encoding**: Generates 128-dimensional face embeddings using dlib's face recognition model
- **Classification**: SVM classifier trained on student face embeddings for identification
- **Matching**: Compares new faces against trained classifier for identification

### Voice Recognition Pipeline
- **Audio Processing**: Librosa preprocesses audio to 16kHz sampling rate
- **Embedding**: Resemblyzer generates speaker embeddings from audio utterances
- **Identification**: Compares voice embeddings with stored student samples using distance metrics
- **Threshold**: Configurable threshold (default 0.65) for identification accuracy

---

## 🗄 Database Schema Overview

### Key Tables

**teachers**
- `id`: Unique identifier
- `username`: Login username
- `password`: Hashed password
- `name`: Teacher name

**students**
- `id`: Unique identifier
- `name`: Student name
- `face_embedding`: Stored face encoding vectors
- `voice_embedding`: Stored voice encoding vectors

**subjects**
- `id`: Unique identifier
- `subject_code`: Subject code
- `name`: Subject name
- `section`: Section number
- `teacher_id`: Reference to teacher
- `join_code`: Code for student enrollment

**attendance_logs**
- `id`: Unique identifier
- `student_id`: Reference to student
- `subject_id`: Reference to subject
- `timestamp`: Attendance timestamp
- `method`: Recognition method (face/voice)

**student_subject_enrollment**
- `student_id`: Reference to student
- `subject_id`: Reference to subject
- `enrollment_date`: Date of enrollment

---

## 🔒 Security Considerations

- **Password Security**: All teacher passwords are hashed using bcrypt
- **API Keys**: Supabase credentials stored securely in Streamlit secrets
- **Data Privacy**: Student biometric data stored securely in database
- **Authentication**: Role-based access control for teachers and students

---

## 🐛 Troubleshooting

### Common Issues

**"Face recognition library not found"**
- Ensure `dlib-bin` is installed: `pip install dlib-bin`
- On Windows, you may need Visual Studio Build Tools

**"Supabase connection error"**
- Verify `SUPABASE_URL` and `SUPABASE_KEY` in secrets.toml
- Check internet connection and Supabase service status

**"Camera/Microphone not working"**
- Grant browser permissions for camera and microphone
- Check device permissions in system settings

**"No faces detected"**
- Ensure adequate lighting
- Position face directly at camera
- Try multiple photos for training

---

## 📝 Development Notes

### Adding New Features
1. Create components in `src/components/` for UI elements
2. Add database operations in `src/database/db.py`
3. Implement pipelines in `src/pipelines/` for new ML features
4. Add screens in `src/screens/` for new user interfaces

### Code Organization
- Keep components modular and reusable
- Use Streamlit caching (`@st.cache_resource`) for ML models
- Follow existing naming conventions
- Document complex AI logic with comments

---

## 📄 License

This project is provided as-is for educational purposes.

---

## 👥 Authors & Contributors

SnapClass Development Team

---

## 📞 Support & Contact

For issues, questions, or contributions, please refer to the project documentation or contact the development team.

---

**Last Updated**: May 5, 2026  
**Version**: 1.0