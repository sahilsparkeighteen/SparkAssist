
### SparkAssist - LinkedIn Automation Setup Steps

#### 1. Download and Extract Chrome for Testing
- Download the latest stable version of Chrome for testing according to your system from [here](https://googlechromelabs.github.io/chrome-for-testing/#stable).
- Extract the downloaded zip file.

#### 2. Download and Extract the Code
- Download the code zip file and extract it. [Click here to download](https://drive.google.com/file/d/1Lm2cEyJ1w-99UaWq5c4-_3JND1MVy5vH/view?usp=drive_link).

#### 3. Create a Python Virtual Environment
- Navigate to the backend directory:
  ```bash
  cd {{code_extract_location}}/backend
  ```
- Create a virtual environment named `venv`:
  - For Mac/Ubuntu:
    ```bash
    python3 -m venv venv
    ```

#### 4. Install Dependencies
- Activate the virtual environment:
  ```bash
  source venv/bin/activate
  ```
- Install the required dependencies:
  ```bash
  pip3 install -r requirements.txt
  ```
- Uninstall and reinstall `channels` to ensure compatibility:
  ```bash
  pip3 uninstall channels
  pip3 install channels
  ```

#### 5. Create `.env` Files
- Create a `.env` file in the backend directory with the following content:
  ```plaintext
  SHEET_ID="1V6YUYtWd6HnxvvJg1n4hfnTxnpMDOdNgirL8qf9lk9w"
  SEARCH_COMPANIES_TB="Search Companies"
  COMPANIES_TB="Companies"
  TARGET_PROFILES_TB="Target Profiles"
  EXECUTABLE_PATH="/path/to/your/chromedriver"
  CELERY_BROKER_URL="redis://127.0.0.1:6379/0"
  CELERY_RESULT_BACKEND="redis://127.0.0.1:6379"
  CELERY_TIMEZONE="Asia/Kolkata"
  CELERYD_LOG_LEVEL="DEBUG"
  ```
  - Make sure to update the `EXECUTABLE_PATH` with the correct path to your ChromeDriver executable.

- Create a `.env` file in the frontend directory with the following content:
  ```plaintext
  REACT_APP_API_URL=http://127.0.0.1:8000/
  REACT_APP_SOCKET_URL=ws://127.0.0.1:8000/ws/logs/log_frontend/
  ```

#### 6. Modify `service.py` in Selenium Package
- Open the `service.py` file located in the virtual environment:
  ```bash
  venv/lib/python-x/site-packages/selenium/webdriver/common/service.py
  ```
- Search for the method `def stop` around line 135.
- Replace the `def stop` method with the following code:
  ```python
  def stop(self) -> None:
      return
  ```

#### 7. Make Bash Files Executable
- Navigate to the code directory:
  ```bash
  cd {{code_extract_location}}
  ```
- Make the bash files executable:
  ```bash
  chmod +x backend.sh
  chmod +x frontend.sh
  ```

#### 8. Run the Bash Files
- Navigate to the code directory:
  ```bash
  cd {{code_extract_location}}
  ```
- Run the backend and frontend bash scripts:
  ```bash
  ./backend.sh
  ./frontend.sh
  ```

#### 9. Access the Application
- Open a web browser and go to `http://localhost:3000`.
- Use the following credentials to log in:
  - **Username**: `automation@sparkeighteen.com`
  - **Password**: `Automation@123`

#### 10. Generate Gmail Access Token
- Before generating the Gmail access token, ensure your email is added to the Google Developer Console by the developer.
- Go to the following URL to generate a Gmail access token, which allows the application to read emails sent by LinkedIn and update the connection request status in the SparkAssist database:
  ```plaintext
  http://localhost:8000/api/generate-gmail-access-token/
  ```

#### 11. Contact Information
- If you face any issues, please contact:
  - **Developer Name**: Sahil Kumar
  - **Email**: [sahil.kumar@sparkeighteen.com](mailto:sahil.kumar@sparkeighteen.com)
  - **LinkedIn**: [Sahil Kumar](https://www.linkedin.com/in/sahil-kanger-28176819a/)

These steps should guide you through setting up SparkAssist for LinkedIn automation. Ensure that all dependencies are correctly installed and that paths are accurately specified. If you encounter any issues, verify your configurations and paths in the `.env` files.
