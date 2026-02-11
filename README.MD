# CSE 270 – Smoke Test CI/CD Project

Author : Diogo Rangel dos Santos
CSE 270 – Software Testing & DevOps
This project demonstrates a complete CI/CD pipeline implementation for a static website using:

Python

Pytest

Selenium WebDriver

GitHub Actions

Chrome Headless Browser

The project includes automated smoke testing to validate that the web application loads correctly and that core functionality works as expected.

Project Structure
cse270-v16/
│
├── test_smokeside.py        # Selenium smoke test
├── cse270/                  # Website source files
├── .github/
│   └── workflows/
│       └── main.yml         # CI/CD pipeline configuration
└── README.md

Technologies Used

Python 3.12+

Pytest

Selenium

Chrome WebDriver

GitHub Actions

HTTP Server Action

Smoke Test Description

The smoke test (test_smokeside.py) verifies:

Homepage loads successfully

Key UI elements are present

Navigation links work correctly

Directory view switches correctly

Join form submission works

Admin login shows an error message for invalid credentials

The test runs using Chrome in headless mode during CI execution.

Running Tests Locally
1. Install dependencies
pip install -r requirements.txt


Or manually:

pip install pytest selenium

2. Start Local Web Server (Port 5500)

The test expects the site to run on:

http://127.0.0.1:5500


You can use:

VS Code Live Server

Or Python HTTP server:

python -m http.server 5500

3. Run Tests
pytest -v

Viewing Test Results in VS Code

You can see test results in three ways:

Option 1 – Terminal

Run:

pytest -v


Results will appear in the terminal:

✔ PASSED

❌ FAILED

Option 2 – VS Code Testing Tab (Recommended)

Install the Python extension by Microsoft.

Press:

Ctrl + Shift + P


Select:

Python: Configure Tests


Choose:

pytest

Root project folder

You will see:

List of tests

▶ Run button

✔ Green (passed)

❌ Red (failed)

Option 3 – HTML Test Report

If pytest-html is installed:

pip install pytest-html


Run:

pytest --html=report.html


Then open:

report.html


in your browser.

CI/CD Pipeline

The GitHub Actions workflow:

Installs dependencies

Runs linting (flake8)

Starts a local HTTP server on port 5500

Executes pytest

Runs CodeQL analysis

Deploys to GitHub Pages

Important

The workflow expects the server to run on:

port: 5500


If you change the port in your test file, you must also update it in:

.github/workflows/main.yml

Running in Headless Mode (CI)

For GitHub Actions, Chrome runs in headless mode:

options.add_argument("--headless=new")
options.add_argument("--no-sandbox")
options.add_argument("--disable-dev-shm-usage")


Headless mode is required because CI environments do not have a graphical interface.

Expected CI Flow

Push to main

GitHub Actions triggers

Server starts on port 5500

Smoke test runs

If all tests pass → deployment continues

Pages deploys successfully

Educational Purpose

This project demonstrates:

Automated UI testing

Smoke test strategy

Continuous Integration

Continuous Deployment

Selenium best practices

Headless browser testing

GitHub Actions pipeline setup
