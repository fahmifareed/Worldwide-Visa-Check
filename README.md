
![Banner](/banner.png)
![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-Framework-green?logo=flask&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-4.5.3.56-green) ![Tesseract](https://img.shields.io/badge/Tesseract-OCR-red) ![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-1.4.22-lightgrey)
![Heroku](https://img.shields.io/badge/Heroku-Deployed-blueviolet?logo=heroku&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-blue?logo=github-actions&logoColor=white)
![License](https://img.shields.io/github/license/<your-username>/worldwide-visa-check)

# Worldwide Visa Check
A Python-based global solution for scanning passports and verifying visa validity using Optical Character Recognition (OCR) and various API/data sources.

## Key Features:
- **Passport Image Upload or Scanning**: Allows users to upload or scan passport images.
- **OCR for Passport Data Extraction**: Uses Tesseract OCR to extract passport details such as passport number, nationality, and date of birth.
- **Visa Validity Check**: Validates visa information against predefined rules (or through external API integration if available).
- **User Authentication**: Secure user registration and login system using Flask-Login.
- **Database Management**: Stores passport and visa details using SQLite.
- **Security**: Data encryption for sensitive information and HTTPS support for secure communication.

## Table of Contents
1. [Technologies Used](#technologies-used)
2. [Project Architecture](#project-architecture)
3. [Installation](#installation)
4. [Usage](#usage)
5. [API Endpoints](#api-endpoints)
6. [Security Considerations](#security-considerations)
7. [Deployment](#deployment)
8. [ToDo](#todo)
9. [Contribution](#contribution)
10. [License](#license)

## Technologies Used:
- **Python 3.9**: Core programming language.
- **Flask**: Web framework used for creating the web application.
- **OpenCV**: For image processing and passport scanning.
- **Tesseract-OCR**: Optical Character Recognition library for extracting text from passport images.
- **SQLAlchemy**: ORM for database management (SQLite).
- **Flask-Login**: For user authentication and session management.
- **Flask-WTF**: For secure forms and CSRF protection.

## Project Architecture:

### Architecture Diagram:
![Architecture](./worldwide_visa_check_architecture.png)

### Architecture Description:
```
+----------------------------------------------+
|               User Interface (UI)            |
|  - HTML/CSS/JavaScript                       |
|  - Passport Image Upload Form                |
+----------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|              Web Application (Flask)             |
|  - Routes:                                       |
|    - `/upload`: Handles passport image upload    |
|    - `/register`: User registration              |
|    - `/login`: User login                        |
|  - Authentication: Flask-Login                   |
|  - Handles form submissions and processes data   |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|        OCR & Image Processing                    |
|  - Tesseract: Extracts text from passport images  |
|  - OpenCV: Preprocesses images (grayscale, etc.)  |
|  - Focuses on the MRZ for passport data           |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|               Visa Validation Logic              |
|  - Validates visa expiration date                |
|  - Checks issuing country and visa number        |
|  - Predefined rules or external API integration  |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|             Database (SQLite/SQLAlchemy)         |
|  - User Table: Stores user credentials           |
|  - Passport Table: Stores passport details       |
|  - Visa Table: Stores visa details               |
|  - Logs all scans for auditing                   |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|               Security Layer                     |
|  - User Authentication via Flask-Login           |
|  - Data encryption using cryptography library    |
|  - HTTPS for secure communication                |
|  - CSRF protection via Flask-WTF                 |
+--------------------------------------------------+
                       |
                       v
+--------------------------------------------------+
|               Deployment (Cloud)                 |
|  - Dockerized for portability                    |
|  - Deployable on Heroku or AWS                   |
|  - Autoscaling and monitoring for production     |
+--------------------------------------------------+
```

### Workflow:
1. **User Interaction**: Users interact with the web interface to upload passport images.
2. **File Upload**: The Flask backend processes the uploaded images.
3. **OCR & Processing**: The image is preprocessed, and Tesseract extracts passport details.
4. **Visa Validation**: Visa information is validated using predefined rules or external APIs.
5. **Database Storage**: All passport and visa details are stored securely in SQLite.
6. **Security**: Data encryption and authentication ensure secure handling of sensitive data.
7. **Deployment**: The app is packaged in Docker and deployed to cloud platforms like Heroku or AWS.

## Installation:

### Prerequisites:
- Python 3.9+
- Tesseract-OCR installed on your machine (for OCR functionality)
  - Install Tesseract: [Installation Guide](https://github.com/tesseract-ocr/tesseract)
  
### Steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/fahmifareed/worldwide-visa-check.git
   cd worldwide-visa-check
   ```

2. Set up a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Initialize the database:
   ```bash
   python
   >>> from app import create_app, db
   >>> app = create_app()
   >>> with app.app_context():
   >>>     db.create_all()
   ```

5. Run the application:
   ```bash
   flask run
   ```

6. Open a browser and visit: `http://127.0.0.1:5000`

## Usage:

### Registration:
- Visit `/register` to create a new user account.
- Provide a username, email, and password to register.

### Login:
- After registering, visit `/login` to log in with your credentials.

### Passport Upload:
- Once logged in, navigate to the homepage.
- Upload an image of a passport to initiate OCR processing.
- The system will extract passport details (name, passport number, nationality) and validate visa details if available.

## API Endpoints:

### 1. `POST /upload`:
Uploads a passport image and returns extracted details.
- **Request**: Form data with the passport image file.
- **Response**: Extracted passport and visa details.

### 2. `POST /register`:
Registers a new user.
- **Request**: JSON data with `username`, `email`, and `password`.
- **Response**: Success or failure message.

### 3. `POST /login`:
Logs in an existing user.
- **Request**: JSON data with `username` and `password`.
- **Response**: Success or failure message.

### 4. `GET /logout`:
Logs out the current user.
- **Request**: No data required.
- **Response**: Redirects to login page.

## Security Considerations:

- **Encryption**: Passport and visa details are encrypted before being stored in the database using the `cryptography` library.
- **HTTPS**: Use HTTPS for secure data transmission in production environments.
- **Authentication**: User authentication is handled with Flask-Login. Passwords are hashed and stored securely.
- **CSRF Protection**: Flask-WTF provides built-in CSRF protection for all forms.

## Deployment:

### Heroku:
1. Install the Heroku CLI and log in.
   ```bash
   heroku login
   ```

2. Create a new Heroku app:
   ```bash
   heroku create worldwide-visa-check
   ```

3. Push the code to Heroku:
   ```bash
   git push heroku main
   ```

4. Set up environment variables for Flask:
   ```bash
   heroku config:set FLASK_APP=run.py
   ```

5. Open the deployed app:
   ```bash
   heroku open
   ```

### AWS (Elastic Beanstalk):
Alternatively, you can deploy the application to AWS using Elastic Beanstalk for scalability.

## ToDo:

- [ ] **Improve UI/UX**
- [ ] Enhance the UI for better user experience (mobile and desktop).
  
- [ ] **Extend Visa Validation Logic**
- [ ] Integrate real-time visa validation APIs (if available).
  
- [ ] **Cloud Storage Integration**
- [ ] Use AWS S3 or other cloud storage to store uploaded images.


## Contribution:

1. Fork the repository.
2. Create a new feature branch:
   ```bash
   git checkout -b feature/your-feature
   ```

3. Commit your changes:
   ```bash
   git commit -m "Add your feature"
   ```

4. Push the branch to GitHub:
   ```bash
   git push origin feature/your-feature
   ```

5. Create a Pull Request on the main repository.

## License:
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
```

Let me know if you'd like further changes!
