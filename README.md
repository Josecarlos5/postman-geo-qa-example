# Postman + Newman API QA Example

This repository is a starter template for testing REST APIs using Postman and Newman, including CI/CD integration with GitHub Actions.

## Structure
- `collections/` — Postman collections with test cases
- `envs/` — Environment variables for staging
- `data/` — CSV files for data-driven tests
- `.github/workflows/` — GitHub Actions workflow to run Newman tests
- `reports/` — HTML reports generated after tests

## Local Run
npm install -g newman newman-reporter-htmlextra

newman run collections/geo-qa.postman_collection.json \
  -e envs/staging.postman_environment.json \
  -d data/login_cases.csv \
  -r cli,htmlextra \
  --reporter-htmlextra-export reports/report.html

## CI/CD
Every push to main will:

Install Newman
Run the API tests
Upload an HTML report as a GitHub Actions artifact
