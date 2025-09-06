# Face-Based Student Attendance System

A Django-based web application that uses facial recognition technology to automatically track student attendance. The system supports multiple cameras, real-time face detection, and provides a comprehensive admin interface for managing students and attendance records.

## Features

- **Facial Recognition**: Uses FaceNet (InceptionResnetV1) and MTCNN for accurate face detection and recognition
- **Multi-Camera Support**: Configure and use multiple cameras simultaneously for attendance tracking
- **Student Registration**: Web-based selfie capture system for student enrollment
- **Admin Dashboard**: Comprehensive interface for managing students, attendance, and camera configurations
- **Real-time Processing**: Live face recognition with audio feedback
- **Attendance Export**: Download attendance records in Excel/CSV format
- **Authorization System**: Admin approval required for student activation
- **Responsive UI**: Modern dark-themed interface with Bootstrap styling

## Technology Stack

- **Backend**: Django 5.0.7, Python
- **Computer Vision**: OpenCV, PyTorch, FaceNet-PyTorch
- **Database**: SQLite3 (easily configurable to other databases)
- **Frontend**: HTML5, CSS3, Bootstrap, Font Awesome
- **Audio**: Pygame for success notifications

## Prerequisites

- Python 3.8 or higher
- Webcam or IP camera
- Git (for cloning the repository)

## Installation & Setup

### 1. Clone the Repository

\`\`\`bash
git clone <your-repository-url>
cd Project-Face-attandence-system-version-1.0
\`\`\`

### 2. Create Virtual Environment

\`\`\`bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
\`\`\`

### 3. Install Dependencies

\`\`\`bash
pip install -r requirements.txt
\`\`\`

### 4. Database Setup

\`\`\`bash
# Run migrations
python manage.py makemigrations
python manage.py migrate

# Create superuser (admin account)
python manage.py createsuperuser
\`\`\`

### 5. Create Media Directory

\`\`\`bash
mkdir media
mkdir media/students
\`\`\`

### 6. Run the Development Server

\`\`\`bash
python manage.py runserver
\`\`\`

The application will be available at `http://127.0.0.1:8000/`

## Usage Guide

### Initial Setup

1. **Admin Login**: Navigate to `http://127.0.0.1:8000/login/` and login with your superuser credentials

2. **Configure Camera**: 
   - Go to Camera Configuration section
   - Add camera configurations (use `0` for default webcam or IP camera URL)
   - Set recognition threshold (0.6 recommended)

### Student Registration

1. **Student Self-Registration**:
   - Navigate to `http://127.0.0.1:8000/capture_student/`
   - Fill in student details
   - Capture selfie using webcam
   - Submit registration

2. **Admin Authorization**:
   - Login as admin
   - Go to Students section
   - Review and authorize pending students

### Attendance Tracking

1. **Start Face Recognition**:
   - Click "Start Face Recognition" from the dashboard
   - System will open camera windows for each configured camera
   - Students will be automatically checked in/out when recognized
   - Press 'q' in any camera window to stop

2. **View Attendance**:
   - Navigate to "View Attendance" section
   - Filter by student name or date
   - Export records to Excel/CSV

### Download Attendance Records

1. Go to the attendance list page
2. Use the search and date filters if needed
3. Click "Download Excel" or "Download CSV" button
4. File will be downloaded with attendance data

## Project Structure

\`\`\`
Project-Face-attandence-system-version-1.0/
├── Project101/                 # Django project settings
│   ├── settings.py            # Main configuration
│   ├── urls.py               # URL routing
│   └── wsgi.py               # WSGI configuration
├── app1/                      # Main application
│   ├── models.py             # Database models
│   ├── views.py              # View functions
│   ├── urls.py               # App URL patterns
│   ├── admin.py              # Admin interface
│   └── suc.wav               # Success sound file
├── templates/                 # HTML templates
│   ├── home.html             # Dashboard
│   ├── login.html            # Admin login
│   ├── capture_student.html  # Student registration
│   ├── student_list.html     # Student management
│   └── ...                   # Other templates
├── media/                     # Uploaded files
│   └── students/             # Student photos
├── static/                    # Static files (CSS, JS)
├── manage.py                 # Django management script
├── requirements.txt          # Python dependencies
└── README.md                # This file
\`\`\`

## Database Models

### Student Model
- Name, email, phone number, class
- Profile image
- Authorization status

### Attendance Model
- Student reference
- Date, check-in/check-out times
- Automatic duration calculation

### CameraConfiguration Model
- Camera name and source
- Recognition threshold settings

## API Endpoints

- `/` - Dashboard
- `/capture_student/` - Student registration
- `/capture-and-recognize/` - Face recognition
- `/students/` - Student management
- `/students/attendance/` - Attendance records
- `/camera-config/` - Camera configuration
- `/login/` - Admin authentication

## Configuration

### Camera Settings
- **Local Webcam**: Use camera index (0, 1, 2, etc.)
- **IP Camera**: Use full URL (e.g., `http://192.168.1.100:8080/video`)
- **Threshold**: Recognition confidence (0.0-1.0, recommended: 0.6)

### Audio Settings
- Place your success sound file at `app1/suc.wav`
- Supported formats: WAV, MP3, OGG

## Troubleshooting

### Common Issues

1. **Camera Not Working**:
   - Check camera permissions
   - Verify camera index or IP URL
   - Ensure camera is not used by another application

2. **Face Recognition Accuracy**:
   - Adjust threshold in camera configuration
   - Ensure good lighting conditions
   - Use high-quality student photos

3. **Dependencies Issues**:
   - Ensure Python 3.8+ is installed
   - Try upgrading pip: `pip install --upgrade pip`
   - Install dependencies one by one if batch install fails

4. **Database Issues**:
   - Delete `db.sqlite3` and run migrations again
   - Check file permissions in project directory

### Performance Optimization

- Use GPU acceleration if available (CUDA)
- Optimize camera resolution for better performance
- Consider using IP cameras for better quality

## Security Considerations

- Change the Django secret key in production
- Use environment variables for sensitive settings
- Implement HTTPS in production
- Regular backup of student data and attendance records

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source. Please check the license file for details.

## Support

For issues and questions:
1. Check the troubleshooting section
2. Review Django and OpenCV documentation
3. Create an issue in the repository

## Acknowledgments

- FaceNet-PyTorch for face recognition
- Django framework for web development
- OpenCV for computer vision
- Bootstrap for responsive UI design
