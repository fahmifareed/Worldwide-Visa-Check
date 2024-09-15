[![Worldwide Visa Check](https://github.com/fahmifareed/Worldwide-Visa-Check/blob/main/banner.png)](https://github.com/fahmifareed/Worldwide-Visa-Check)
# Worldwide Visa Check

![Heroku](https://img.shields.io/badge/Heroku-Deployed-blueviolet?logo=heroku&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-Framework-green?logo=flask&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-blue?logo=github-actions&logoColor=white)
![License](https://img.shields.io/github/license/<your-username>/worldwide-visa-check)

### A Global Solution for Scanning Passports and Validating Visa Legality

---

## Project Overview

The **Worldwide Visa Check** application is designed to allow users to scan passports and validate visas using Optical Character Recognition (OCR) technology. The application extracts key passport information, validates visas based on rules or external APIs, and stores the scanned data for auditing purposes. Built with security, efficiency, and scalability in mind, the project is deployed using continuous integration and continuous deployment (CI/CD) practices, ensuring smooth updates and automated deployment.

---

## Key Features

- **User Authentication**
  - Secure registration and login.
  - Password hashing and session management.
  - Protect routes to allow only authorized users to upload passport images.

- **Passport Image Upload & OCR**
  - Upload passport images in `.png`, `.jpg`, or `.jpeg` formats.
  - Extract data such as passport number, name, issuing country, date of birth, and expiration date using Tesseract OCR.
  - Preprocess images using OpenCV to improve OCR accuracy.

- **Visa Validation**
  - Extract visa-related information such as visa number, issue date, and expiration date.
  - Validate the visa based on predefined rules (e.g., expiration check) or external APIs for country-specific visa validation.

- **Data Security**
  - Encrypt sensitive data such as passport and visa details before storing them in the database.
  - CSRF protection for forms and secure handling of file uploads.
  - User authentication and access control using Flask-Login and Flask-WTF.

- **Database Integration**
  - Use SQLite or any relational database (MySQL/PostgreSQL) to store users, passports, and visas.
  - Establish relationships between users and their scanned passport/visa data.
  - Store validation logs for auditing and future use.

---

## Technologies Used

- **Backend**: 
  - Python (Flask Framework)
  - Flask-Login & Flask-WTF for security and authentication.
  - OpenCV for image processing.
  - Tesseract for OCR.

- **Frontend**:
  - HTML/CSS for the user interface.
  - Flask Jinja2 Templates for dynamic content.

- **Database**:
  - SQLite (or MySQL/PostgreSQL) using SQLAlchemy ORM.

- **CI/CD**:
  - GitHub Actions for automated testing and deployment.
  - Deployment on **Heroku** or **AWS Elastic Beanstalk**.

---

## Project Setup

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/worldwide-visa-check.git
cd worldwide-visa-check
```

### 2. Set Up the Python Virtual Environment

```bash
python -m venv venv
source venv/bin/activate   # For Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Up Environment Variables

Create a `.env` file for your environment variables:

```bash
SECRET_KEY=your_secret_key
DATABASE_URL=sqlite:///visa_check.db  # or your preferred database URL
```

### 5. Initialize the Database

```bash
flask db init
flask db migrate
flask db upgrade
```

### 6. Run the Application Locally

```bash
flask run
```

---

## Running Tests

You can run unit and integration tests (if configured) to verify that the application works as expected:

```bash
pytest
```

---

## CI/CD Deployment

### Heroku Deployment

1. Log in to Heroku:
   ```bash
   heroku login
   ```

2. Create a Heroku app:
   ```bash
   heroku create worldwide-visa-check
   ```

3. Add your remote Heroku repository:
   ```bash
   git remote add heroku https://git.heroku.com/worldwide-visa-check.git
   ```

4. Push to Heroku:
   ```bash
   git push heroku main
   ```

### AWS Deployment

1. Initialize the Elastic Beanstalk environment:
   ```bash
   eb init -p python-3.7 worldwide-visa-check --region us-east-1
   ```

2. Create the environment:
   ```bash
   eb create worldwide-visa-check-env
   ```

3. Deploy:
   ```bash
   eb deploy
   ```

---

## Future Enhancements

- **Visa API Integration**: Extend the visa validation by integrating with government or third-party APIs to perform real-time visa checks.
- **Cloud Storage**: Use AWS S3 or similar services to store passport images.
- **Internationalization**: Add support for multiple languages for global users.
- **Mobile Compatibility**: Improve the UI for mobile users and consider developing a mobile application.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Contributors

- **Fahmi Farid** (Lead Developer)
- **Other Contributors**
