# Restful API Testing Framework

API testing framework built with Playwright for testing the [Restful Booker API](https://restful-booker.herokuapp.com).

## Project Structure

```
api-testing/
├── api/                    # API client classes
│   ├── authApi.ts         # Authentication API
│   └── bookingApi.ts      # Booking CRUD operations
├── config/                 # Configuration files
│   ├── endpoints.ts       # API endpoints
│   └── constants.ts       # Status codes & constants
├── models/                 # Data models and interfaces
│   └── booking.model.ts   # Booking & Auth models
├── helpers/                # Helper utilities
│   └── testData.ts        # Test data factory
├── tests/                  # Test files
│   ├── auth.spec.ts       # Authentication tests
│   └── booking.spec.ts    # Booking CRUD tests
├── playwright.config.ts    # Playwright configuration
├── tsconfig.json          # TypeScript configuration
└── package.json           # Project dependencies
```

## Installation

1. Install dependencies:
```bash
npm install
```

2. Install Playwright:
```bash
npx playwright install
```

## Running Tests

Run all tests:
```bash
npm test
```

Run specific test file:
```bash
npx playwright test tests/auth.spec.ts
npx playwright test tests/booking.spec.ts
```

Run tests in UI mode:
```bash
npm run test:ui
```

View test report:
```bash
npm run test:report
```

## Allure Reporting

This project includes Allure reporting for beautiful, detailed test reports.

### Generate and View Allure Report

After running tests, generate and open the Allure report:
```bash
# Run tests and open Allure report
npm run test:allure
```

Or run commands separately:
```bash
# Generate report from results
npm run allure:generate

# Open the report in browser
npm run allure:open

# Or serve the report (alternative)
npm run allure:serve
```

### Allure Report Features
- ✅ Test execution history
- 📊 Detailed test statistics
- 🔍 Request/response details
- ⏱️ Test duration tracking
- 📈 Trends and graphs
- 🏷️ Categorization and tagging

## GitHub Actions CI/CD

This project includes a GitHub Actions workflow that automatically:
- 🚀 Runs tests on every push and pull request
- 📊 Generates Allure reports
- 📦 Uploads test artifacts
- 🌐 Deploys Allure reports to GitHub Pages (on main branch)

### Viewing CI Results

After pushing to GitHub:
1. Go to the **Actions** tab in your repository
2. Click on the latest workflow run
3. Download artifacts:
   - `allure-report` - Complete Allure HTML report
   - `playwright-report` - Standard Playwright report
   - `allure-results` - Raw test results

### Enable GitHub Pages (Optional)

To view Allure reports directly on GitHub Pages:
1. Go to **Settings** → **Pages**
2. Source: Deploy from a branch
3. Branch: `gh-pages` / `root`
4. Save

Your Allure report will be available at: `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`


## Test Coverage

### Auth API Tests (3 tests)
- Create auth token with valid credentials
- Fail with invalid credentials (negative)
- Fail with missing username (negative)

### Booking API Tests (11 tests)
- Check API health (ping)
- Get all bookings
- Create new booking
- Get booking by ID
- Update booking completely (PUT)
- Partially update booking (PATCH)
- Delete booking
- Return 404 for non-existent booking (negative)
- Return 403 for updating without authentication (negative)
- Return 403 for deleting without authentication (negative)


## API Documentation

This framework tests the Restful Booker API: [https://restful-booker.herokuapp.com/apidoc/index.html](https://restful-booker.herokuapp.com/apidoc/index.html)

**Base URL:** `https://restful-booker.herokuapp.com`

### Main Endpoints:
- `POST /auth` - Create authentication token
- `GET /booking` - Get all bookings
- `POST /booking` - Create a new booking
- `GET /booking/:id` - Get booking by ID
- `PUT /booking/:id` - Update booking
- `PATCH /booking/:id` - Partial update booking
- `DELETE /booking/:id` - Delete booking
- `GET /ping` - Health check

