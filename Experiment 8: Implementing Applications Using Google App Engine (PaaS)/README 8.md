# Experiment 8: Implementing Applications Using Google App Engine (PaaS)

## Aim

To understand the concept of Platform as a Service (PaaS) and develop, deploy, monitor, and manage a simple web application using Google App Engine.

## Technologies and Tools Used

- **Cloud Platform:** Google Cloud Platform (GCP)
- **PaaS Service:** Google App Engine
- **Programming Language:** Python
- **Web Framework:** Flask
- **Runtime:** Python 3.12
- **Command-Line Tool:** Google Cloud CLI
- **Package Manager:** pip
- **Development Environment:** Ubuntu / Linux / Windows
- **Web Browser:** Google Chrome

## Experiment Overview

Platform as a Service (PaaS) is a cloud computing service model that provides a platform for developing, running, and deploying applications without requiring users to manage the underlying infrastructure.

The cloud provider manages:
- Servers
- Storage
- Networking
- Operating System
- Runtime Environment
- Application Infrastructure

**Google App Engine** is a PaaS service provided by Google Cloud that allows developers to build and deploy applications on Google's infrastructure.

### Features of Google App Engine

- Application deployment
- Managed runtime environments
- Automatic scaling
- Application version management
- Application logging
- Cloud-based hosting

### Other Examples of PaaS

- Microsoft Azure App Service
- Heroku
- AWS Elastic Beanstalk

---

## Task 1: PaaS and Google App Engine Setup

### Step 1.1: Create or Access a Google Cloud Project

1. Open a web browser.
2. Visit the [Google Cloud Console](https://console.cloud.google.com/).
3. Sign in using an authorised Google account.
4. Create a new Google Cloud project or select an existing project.
5. Note the Project ID.

Example:

```text
cloud-lab8-project
```

**Purpose:** Creates or selects a Google Cloud project where the App Engine application will be hosted.

### Step 1.2: Open Google App Engine

1. Open the Google Cloud Console.
2. Search for **App Engine**.
3. Open the App Engine service.
4. Explore the App Engine dashboard.
5. Identify the application and service-related options.

**Purpose:** Familiarises students with the Google App Engine dashboard and its available features.

### Step 1.3: Select the App Engine Region

1. Select **Create Application** if App Engine has not been initialised.
2. Choose an available region.
3. Review the selected region carefully.
4. Complete the App Engine initialisation process.

**Important:** The App Engine region generally cannot be changed after the application is created. Select the region instructed by your faculty or appropriate for your laboratory account.

**Expected Result:** A Google Cloud project is configured and the App Engine environment is initialised.

## Task 2: Develop a Simple Web Application

In this task, a simple web application is developed using Python and the Flask framework.

### Step 2.1: Create the Application Directory

Open the terminal and execute:

```bash
mkdir cloud-lab8
cd cloud-lab8
```

**Purpose:** Creates the application directory and navigates into it.

### Step 2.2: Create the Application File

Create a file named `main.py`:

```bash
nano main.py
```

Add the following Python code:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return """
    <h1>Cloud Computing Lab 8</h1>
    <p>Application successfully implemented using Google App Engine.</p>
    <p>This application demonstrates Platform as a Service (PaaS).</p>
    """

if __name__ == "__main__":
    app.run(host="127.0.0.1", port=8080)
```

Save the file:

- `Ctrl + O` → Press Enter
- `Ctrl + X` → Exit Nano

**Explanation:**

- `Flask` imports the Flask web framework.
- `app = Flask(__name__)` creates the Flask application.
- `@app.route("/")` defines the application's home page.
- `home()` returns the HTML content displayed in the browser.
- `app.run()` starts the application locally on port 8080.

### Step 2.3: Create the Requirements File

Create a file named `requirements.txt`:

```bash
nano requirements.txt
```

Add:

```text
Flask
```

Save and exit Nano.

**Purpose:** Specifies Flask as the Python package required by the application.

### Step 2.4: Install Flask

Install Flask using pip:

```bash
pip install Flask
```

**Purpose:** Installs the Flask framework required to execute the web application.

### Step 2.5: Test the Application Locally

Run the application:

```bash
python main.py
```

The terminal should indicate that the application is running on port 8080.

Open a web browser and visit:

```text
http://127.0.0.1:8080
```

**Expected Result:** The browser should display:

- Cloud Computing Lab 8
- Application successfully implemented using Google App Engine.
- This application demonstrates Platform as a Service (PaaS).

**Purpose:** Verifies that the application works correctly before deploying it to Google Cloud.

## Task 3: Configure and Deploy the Application Using Google App Engine

### Step 3.1: Install Google Cloud CLI

Install the Google Cloud CLI if it is not already available on the system.

Verify the installation:

```bash
gcloud --version
```

**Purpose:** Google Cloud CLI allows users to interact with Google Cloud services through terminal commands.

### Step 3.2: Authenticate with Google Cloud

Execute:

```bash
gcloud auth login
```

1. A browser window may open.
2. Sign in using the authorised Google account.
3. Allow the required permissions.
4. Return to the terminal after authentication.

**Purpose:** Authenticates the user with Google Cloud.

### Step 3.3: Select the Google Cloud Project

List available projects:

```bash
gcloud projects list
```

Identify the project created for this experiment.

Set the project:

```bash
gcloud config set project PROJECT_ID
```

Replace `PROJECT_ID` with your actual Google Cloud Project ID.

Verify the configuration:

```bash
gcloud config get-value project
```

**Purpose:** Selects the Google Cloud project where the application will be deployed.

### Step 3.4: Create the App Engine Configuration File

Create a file named `app.yaml`:

```bash
nano app.yaml
```

Add the following configuration:

```yaml
runtime: python312
```

Save and exit Nano.

**Purpose:** Specifies the Python runtime environment that Google App Engine should use to execute the application.

### Step 3.5: Deploy the Application

Make sure you are inside the `cloud-lab8` directory.

Execute:

```bash
gcloud app deploy
```

1. Review the deployment configuration.
2. Confirm the deployment when prompted.
3. Wait for the deployment process to complete.

**Purpose:** Uploads the application and deploys it to Google App Engine.

### Step 3.6: Open the Deployed Application

After successful deployment, execute:

```bash
gcloud app browse
```

Alternatively, open the application URL displayed after deployment.

**Expected Result:** The application should be accessible through its Google App Engine URL.

**Purpose:** Verifies that the application has been successfully deployed and is accessible online.

## Task 4: Application Monitoring and Management

### Task 4A: Explore Application Versions

Google App Engine supports version management, allowing multiple versions of an application to be deployed.

#### Step 4A.1: List Application Versions

Execute:

```bash
gcloud app versions list
```

Observe the following details:

- Version ID
- Service
- Traffic allocation
- Status

**Purpose:** Displays the deployed application versions.

#### Step 4A.2: Understand Application Versions

An application can have multiple deployed versions.

Example:

```text
Version 1 → Initial application
Version 2 → Updated application
```

Different versions can be deployed and managed independently.

**Expected Result:** Students understand how Google App Engine manages different application versions.

### Task 4B: Monitor Application Logs

Google App Engine provides logging facilities to monitor application activity.

#### Step 4B.1: View Application Logs

Execute:

```bash
gcloud app logs tail
```

Observe the application logs generated while accessing the deployed application.

Alternatively:

1. Open Google Cloud Console.
2. Navigate to App Engine.
3. Open the application's monitoring or logging options.
4. Explore the available application logs.

**Purpose:** Displays application logs
