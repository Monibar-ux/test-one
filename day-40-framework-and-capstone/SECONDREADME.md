# Day 40 Setup Notes

## Install dependencies

Run these commands from the Day 40 project folder:

```powershell
npm ci
npx playwright install chromium
```

## Configure environment variables

Create a local `.env` file from the example:

```powershell
Copy-Item .env.example .env
```

Add your approved training-account values to `.env` using these variable names. The values below are fictional examples:

```env
MERIDIAN_EMAIL=student@example.test
MERIDIAN_PASSWORD=not-a-real-password
MERIDIAN_POLICY_NUMBER=POL-TRAINING-0001
```

If a password contains `#`, put it in double quotes in `.env`, because `#` may otherwise begin a comment:

```env
MERIDIAN_PASSWORD="not-a-real-password"
```

Keep the real `.env` private; it is ignored by Git.

## Run tests

Run the full suite or an individual scenario:

```powershell
npm test
npm run test:policy
npm run test:quote
npm run test:api
```

## View the Allure report

Generate and open the report:

```powershell
npm run report:generate
npm run report:open
```

## Run GitHub Actions

Add these as separate repository secrets under **Settings → Secrets and variables → Actions**:

- `MERIDIAN_EMAIL`
- `MERIDIAN_PASSWORD`
- `MERIDIAN_POLICY_NUMBER`

Use the approved training-account credentials and a policy owned by that account. Do not put their real values in this file or commit them.

To run the workflow:

1. Open the repository on GitHub and select **Actions**.
2. Choose **Day 40 Meridian Capstone**.
3. Select **Run workflow** on the `main` branch.
4. After the run, review the results and download the Allure report artifact.

## Keep private data out of commits

- Do not commit `.env` files containing real credentials.
- Do not commit `node_modules`.
- Do not share private account information.
- Do not commit reports containing private training-account data.

The quote and policy tests sign in independently. The public API test does not require a browser or sign-in.
