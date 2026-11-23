Setup Intructions
Install dependencies
npm install
npm ci
npx playwright install chromium

Environment Variables
Create a .env file
Copy-Item .env.example .env

Add training credentials to .env file using these variable names and safe example values:
MERIDIAN_EMAIL=student@example.test
MERIDIAN_PASSWORD=not-a-real-password
MERIDIAN_POLICY_NUMBER=POL-TRAINING-0001

FYI: If your password contains a # character, put double quotes in the .env file. The # may be treated as the beginning of a comment, causing a part of your password to be ignored.

Example:
MERIDIAN_PASSWORD="not-a-real-password"

Run the tests (whichever one is applicable for what you're testing)
npm test (runs all tests, list below runs tests individually)
npm run test:policy
npm run test:quote
npm run test:api

To view Allure report
npm run report:generate (generates Allure report)
npm run report:open (opens an Allure browser page to view report)

GitHub Actions
To Add your credentials secretly to GitHub (Will not be visible to the public)

GitHub Secrets: Settings => Secrets and Variables => Actions

Add these repository secrets:

MERIDIAN_EMAIL
MERIDIAN_PASSWORD
MERIDIAN_POLICY_NUMBER

To run the workflow:

Open the repository on GitHub.
Select Actions.
Choose Day 40 Meridian Capstone.
Select Run workflow.
Choose the main branch and run the workflow.
After the workflow finishes, check the results and download the Allure report artifact.


To keep the project safe, keep these things in mind:

Some things to keep out of GitHub:

Do not upload .env files that contain real usernames, passwords, or other credentials.
Do not upload the node_modules folder.
Do not share any private account information.
Do not upload reports that contain data from private training accounts.

Stick to committing your project code, safe example files, and documentation. If something contains real credentials or personal data, leave it out of the repo.

Notes
The quote and policy tests handle their own login.
The API test does not require a browser or sign-in.
Keep credentials and policy numbers private.