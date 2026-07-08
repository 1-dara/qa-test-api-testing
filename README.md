![API Tests](https://github.com/1-dara/qa-test-api-testing/actions/workflows/newman.yml/badge.svg)

# QA Portfolio: ReqRes API Testing

API testing project targeting [ReqRes](https://reqres.in), a mock REST API built for testing practice.

## What this project demonstrates

- Manual API test case design (9 test cases covering GET, POST, PUT, DELETE)
- Test automation using Postman + Newman (CLI test runner)
- CI/CD integration via GitHub Actions (tests run automatically on every push)
- Secure handling of API credentials using GitHub Secrets (no keys committed to source control)

## Tech stack

- **Postman** — request building and test scripting
- **Newman** — command-line runner for Postman collections, used in CI
- **GitHub Actions** — CI/CD pipeline
- **GitHub Secrets** — secure API key storage

## Project structure

- `reqres-collection.json` — Postman collection (exported), contains all requests and test scripts
- `test-plan.md` — Manual test plan and results
- `.github/workflows/newman.yml` — CI pipeline configuration

## Running the tests locally

```bash
npm install -g newman
npx newman run reqres-collection.json --env-var "apiKey=YOUR_API_KEY_HERE"
```

Get a free API key at [app.reqres.in/api-keys](https://app.reqres.in/api-keys).

## Test coverage

|Method|Test Cases              |
|------|------------------------|
|GET   |TC-API-001 to TC-API-004|
|POST  |TC-API-005 to TC-API-007|
|PUT   |TC-API-008              |
|DELETE|TC-API-009              |

See `test-plan.md` for full test case details, including expected/actual results.

## CI/CD

Tests run automatically on every push via GitHub Actions. The API key is stored as a GitHub Secret (`REQRES_API_KEY`) and injected at runtime — never hardcoded in the repository. See the Actions tab for build history.

## Security note

An API key was briefly hardcoded in the exported Postman collection during development. It was identified before being pushed to GitHub, removed, and replaced with a `{{apiKey}}` variable that’s populated at runtime via GitHub Secrets locally and in CI.

-----

## How to add this file and push it to GitHub

Run these commands, one at a time, from inside your `qa-test-api-testing` folder.

### 1. Make sure you’re in the right folder

```bash
cd ~/qa-test-api-testing
```

### 2. Confirm this README.md is sitting in the folder

```bash
ls
```

You should see `README.md` in the list along with `reqres-collection.json`, `test-plan.md`, `.github`, etc.

### 3. Check what Git sees as changed

```bash
git status
```

Paste this output here first, before staging or committing anything.

### 4. Stage everything

```bash
git add .
```

### 5. Commit

```bash
git commit -m "Add README"
```

### 6. Push

```bash
git push
```

### 7. Verify on GitHub

Go to `https://github.com/1-dara/qa-test-api-testing` and confirm the README renders on the main page.
