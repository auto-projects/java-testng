🚀 Playwright + TestNG Automation Framework (UI + API)

This project is a Java-based automation framework built using:

Playwright (UI + API testing)

TestNG (test runner, parallel execution, retry)

Maven (build + dependency management)

Allure (reporting)

 - 1. Test runners for parallel execution & dependencies
   - testng.xml - responsible for the parallel execution; parallel="methods" → TestNG runs tests in parallel and thread-count="5" → Up to 5 tests run at the same time
   - This means: TestNG runs tests in parallel; Parallel mode is methods;Uses 5 threads
   - depended on tests - handled in test -api-LoginApiTest - @Test(dependsOnMethods = "loginApiSimulation")

- 2. Retry mechanism to improve stability/reliability
   - test -> utils -> RetryAnalyzer - retry mechanism; retries failed tests up to two times

- 3. CI/CD integration, execution schedules, environment selection, and reporting:
   - CI/CD integration: The GitHub Actions workflow runs on push to main, on pull requests, and can be triggered manually (workflow_dispatch).
   - Environment selection: we pass -Denv=ci to Maven, which can select the CI environment.
   - Reporting: Upload both TestNG reports and Allure results