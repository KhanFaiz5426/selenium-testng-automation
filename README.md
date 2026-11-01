# selenium-testng-automation

A simple Selenium browser automation project using Java, TestNG, Maven, and Jenkins for DevSecOps practical.

## Project Description

This project demonstrates basic Selenium WebDriver automation with TestNG framework. It contains a single test that:
1. Opens Google Chrome browser
2. Navigates to the Selenium demo website (https://www.selenium.dev/selenium/web/web-form.html)
3. Fills in a text field with "DevSecOps Practical"
4. Clicks the Submit button
5. Verifies the success message "Received!" appears

## Technologies Used

- **Java 17** - Programming language
- **Maven** - Build and dependency management
- **Selenium WebDriver 4.21.0** - Browser automation
- **TestNG 7.9.0** - Testing framework
- **Maven Surefire Plugin 3.2.5** - Test execution
- **Jenkins** - CI/CD pipeline
- **Google Chrome** - Target browser
- **Selenium Manager** - Automatic ChromeDriver management

## Project Structure

```
selenium-testng-automation/
│
├── src/
│   └── test/
│       └── java/
│           └── com/
│               └── selenium/
│                   └── SeleniumTest.java
│
├── pom.xml
├── testng.xml
├── Jenkinsfile
├── .gitignore
└── README.md
```

## Prerequisites

- Java 17 or higher installed and configured in PATH
- Maven 3.8+ installed and configured in PATH
- Google Chrome browser installed
- Git (for version control)
- Jenkins (for CI/CD pipeline)

## How to Run Locally

### 1. Clone the repository
```bash
git clone <your-repository-url>
cd selenium-testng-automation
```

### 2. Run tests with Maven (headed mode - default)
```bash
mvn clean test
```

### 3. Run tests in headless mode
```bash
mvn clean test -Dheadless=true
```

## How to Execute Tests Using Maven

| Command | Description |
|---------|-------------|
| `mvn clean test` | Runs tests in headed mode (opens Chrome window) |
| `mvn clean test -Dheadless=true` | Runs tests in headless mode (no UI) |
| `mvn clean compile` | Compiles the project only |
| `mvn clean verify` | Runs full build lifecycle including tests |

Test reports are generated in `target/surefire-reports/` as JUnit XML files.

## How to Integrate with Jenkins

### Option 1: Jenkins Pipeline (Recommended)

1. Create a new **Pipeline** job in Jenkins
2. Select **Pipeline script from SCM**
3. Set SCM to **Git** and enter your repository URL
4. Set **Script Path** to `Jenkinsfile`
5. Save and build

The Jenkinsfile will:
- Checkout the code
- Run `mvn clean test` in headless mode
- Publish JUnit test reports automatically

### Option 2: Jenkins Freestyle Project

1. Create a new **Freestyle project**
2. Under **Source Code Management**, select **Git** and add repository URL
3. Under **Build**, add **Invoke top-level Maven targets**
   - Goals: `clean test`
   - Properties: `headless=true`
4. Under **Post-build Actions**, add **Publish JUnit test result report**
   - Test report XMLs: `target/surefire-reports/*.xml`
5. Save and build

## Git Commands to Push to GitHub

```bash
# Initialize Git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Selenium TestNG automation project"

# Add GitHub remote (replace with your repository URL)
git remote add origin https://github.com/<your-username>/selenium-testng-automation.git

# Push to main branch
git branch -M main
git push -u origin main
```

## License

This project is for educational purposes only.