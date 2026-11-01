Aim: To automate a web form using Selenium and TestNG, and execute the test through Jenkins using Maven.
Step 1: Check software
Open CMD:
java -version
mvn -version
git --version


Make sure Java, Maven and Git are working. Also install Google Chrome.
Step 2: Clone the project
cd /d D:\Desktop
git clone https://github.com/KhanFaiz5426/selenium-testng-automation.git
cd selenium-testng-automation
code .


Step 3: Run the project locally
In CMD, inside the project folder:
mvn clean test -Dheadless=true


Check that the output shows:
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
BUILD SUCCESS


Step 4: Push code to GitHub
If the project is already pushed, skip this step.
git add .
git commit -m "Selenium automation project"
git push origin main


Step 5: Open Jenkins
Open:
http://localhost:8080


Go to Manage Jenkins → Tools.

Check that Maven is configured with the name:
Maven3


Reuse the Maven installation from the previous practical.
Step 6: Create Jenkins job
1. Click New Item.
2. Enter Selenium-TestNG-Automation.
3. Select Freestyle project.
4. Click OK.
Step 7: Configure GitHub
Under Source Code Management:
- Select Git.
- Repository URL:
https://github.com/KhanFaiz5426/selenium-testng-automation.git


- Credentials: None (public repository).
- Branch:
*/main


Step 8: Configure Maven
Under Build Steps:
1. Click Add build step.
2. Select Invoke top-level Maven targets.
3. Maven Version: Maven3.
4. Goals:
clean test -Dheadless=true


Step 9: Configure test report
Under Post-build Actions:
1. Select Publish JUnit test result report.
2. Report pattern:
target/surefire-reports/TEST-*.xml


3. Save the job.

Use this pattern if the JUnit-compatible Surefire report exists. TestNG's native testng-results.xml is not necessarily compatible with Jenkins' JUnit publisher.
Step 10: Execute the job
1. Open your Jenkins job.
2. Click Build Now.
3. Wait for execution.
4. Open Console Output.
Expected result:
BUILD SUCCESS
Finished: SUCCESS


Step 11: Verify the test
Open the Jenkins job and click Latest Test Result.

Expected result:
1 Test Passed
- Total: 1
- Passed: 1
- Failed: 0
- Skipped: 0
Step 12: Final screenshots
Take screenshots of:
1. GitHub repository.
2. Jenkins job configuration.
3. Jenkins successful Console Output.
4. Latest Test Result.
Result: Successfully automated a web form using Selenium and TestNG, managed the project using Maven, and executed the automated test through Jenkins.