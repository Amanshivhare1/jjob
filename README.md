# Tidal Dashboard - Job Monitoring System

A real-time job monitoring dashboard that reads data from Excel files. Built with Python Flask.

## Features

- 📊 Real-time job monitoring from Excel files
- 🔐 JWT-based authentication
- 📈 Job metrics and analytics
- 🔍 Search and filtering capabilities
- 📤 CSV export functionality
- ⚠️ Alert system for critical jobs
- 🔄 Auto-refresh when Excel file changes
- 📱 Responsive design
- 🌍 Cross-platform support (Windows, macOS, Linux)

## System Requirements

### Prerequisites
- Python 3.8 or higher
- Windows 10/11, macOS 10.14+, or Linux

### Hardware Requirements
- Minimum 2GB RAM
- 100MB free disk space
- Stable internet connection (for package installation)

## Quick Start

### Option 1: Universal Python Script (Recommended)
**Works on Windows, macOS, and Linux**

1. Download and extract the project files
2. Open terminal/command prompt in the project directory
3. Run the universal setup script:
   ```bash
   python start.py
   ```
4. The script will automatically:
   - Check Python installation
   - Install all dependencies
   - Create sample Excel file
   - Start the server
5. Open your browser and go to `http://localhost:3002`

### Option 2: Manual Setup
1. Open terminal/command prompt in the project directory
2. Create virtual environment:
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate
   
   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```
3. Install requirements:
   ```bash
   pip install -r requirements.txt
   ```
4. Start the application:
   ```bash
   python app.py
   ```

## Installation Steps

### 1. Install Python
- Download Python 3.8 or higher from [python.org](https://www.python.org/downloads/)
- During installation, make sure to check "Add Python to PATH"
- Verify installation: `python --version`

### 2. Download Project
- Download and extract the project files to a folder
- Open Command Prompt in the project directory

### 3. Run Setup
```bash
python setup.py
```

This will:
- Check Python version
- Create necessary directories
- Install required packages
- Create configuration files
- Generate sample Excel file

### 4. Start Application
```bash
python app.py
```

### 5. Access Dashboard
- Open your browser
- Go to `http://localhost:3002`
- Login with default credentials:
  - **Admin**: username=`admin`, password=`Admin@123`
  - **Viewer**: username=`viewer`, password=`Viewer@123`

## Excel File Format

The application reads job data from `sample_data/input.xlsx` with the following columns:

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| jobName | Text | Name of the job | `Daily_ETL` |
| startTime | DateTime | Job start time | `2024-03-20T00:00:00` |
| endTime | DateTime | Job end time | `2024-03-20T01:00:00` |
| dependency | Text | Dependent job name | `Daily_ETL` |
| description | Text | Job description | `Daily data extraction` |
| priority | Text | Job priority | `high`, `normal`, `low` |

### Supported Date Formats
- `YYYY-MM-DDTHH:mm:ss` (ISO format)
- `YYYY-MM-DD HH:mm:ss`
- `YYYY-MM-DD`
- `MM/DD/YYYY HH:mm:ss`
- `MM/DD/YYYY`

## Configuration

### Environment Variables
Create a `.env` file in the project root:

```env
# Flask Configuration
FLASK_APP=app.py
FLASK_ENV=development
SECRET_KEY=your-secret-key-change-this-in-production
JWT_SECRET_KEY=your-jwt-secret-key-change-this-in-production

# Data Source Configuration
DATA_SOURCE=excel
```

### Excel File Location
- Default: `sample_data/input.xlsx`
- The application automatically monitors this file for changes
- Updates are reflected in real-time

## API Endpoints

### Authentication
- `POST /api/auth/login` - User login

### Jobs
- `GET /api/jobs` - Get jobs with filtering and pagination
- `GET /api/jobs/metrics` - Get job metrics
- `POST /api/jobs/refresh` - Force refresh data
- `GET /api/jobs/export` - Export jobs as CSV

### System
- `GET /api/alerts` - Get system alerts
- `GET /api/config` - Get configuration
- `GET /api/health` - Health check

## Troubleshooting

### Common Issues

#### Python Issues
1. **Python not found**:
   - **Windows**: Make sure Python is installed and added to PATH
   - **macOS**: Install with `brew install python3` or download from python.org
   - **Linux**: Install with `sudo apt install python3` (Ubuntu/Debian) or `sudo yum install python3` (CentOS/RHEL)

2. **Permission errors (macOS/Linux)**:
   ```bash
   chmod +x start.sh
   ```

#### Port Issues
1. **Port 3002 in use**:
   ```bash
   # Find process using port 3002
   # Windows
   netstat -ano | findstr :3002
   # macOS/Linux
   lsof -i :3002
   
   # Kill the process (replace PID with the number from above)
   # Windows
   taskkill /PID <PID> /F
   # macOS/Linux
   kill -9 <PID>
   ```

#### Package Installation Issues
1. **SSL errors**:
   ```bash
   pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org -r requirements.txt
   ```

2. **Virtual environment issues**:
   ```bash
   # Windows
   python -m pip install --upgrade pip
   python -m venv venv
   venv\Scripts\activate
   
   # macOS/Linux
   python3 -m pip install --upgrade pip
   python3 -m venv venv
   source venv/bin/activate
   ```

#### Excel File Issues
1. **Excel file not found**:
   - Ensure `sample_data/input.xlsx` exists
   - Check file permissions
   - Verify file format matches template

#### Platform-Specific Issues
1. **Windows**: Run scripts as administrator
2. **macOS**: Allow terminal access in Security & Privacy settings
3. **Linux**: Install system dependencies if needed:
   ```bash
   # Ubuntu/Debian
   sudo apt install python3-dev build-essential
   ```

### Logs
- Check console output for detailed error messages
- Application logs are displayed in the terminal

## Security Considerations

1. Change default passwords immediately
2. Use strong secret keys in production
3. Set up proper firewall rules
4. Use HTTPS in production
5. Regularly update dependencies

## Development

### Project Structure
```
jobmon/
├── app.py                 # Main Flask application
├── start.py               # Universal Python startup script
├── requirements.txt       # Python dependencies
├── README.md             # This file
├── templates/
│   └── index.html        # Dashboard HTML template
├── sample_data/
│   └── input.xlsx        # Excel data file
└── logs/                 # Application logs
```

### Adding Features
1. Modify `app.py` to add new API routes
2. Update `templates/index.html` for frontend changes
3. Update Excel file format if needed
4. Add new API endpoints
5. Enhance dashboard functionality

## Support

For issues and feature requests:
1. Check the troubleshooting section
2. Verify Excel file format
3. Check console logs for errors
4. Ensure all dependencies are installed

## License

[Your License Here] 