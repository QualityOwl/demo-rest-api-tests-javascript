Performance tests for the [Restful Booker API](https://restful-booker.herokuapp.com) written in JavaScript using [k6](https://k6.io).

## Overview

This project contains load and performance tests that validate the Restful Booker API under concurrent traffic. Tests are organized by endpoint and use a shared load profile with ramp-up and ramp-down stages.

**Endpoints covered:**

| Test Suite | Endpoint                                                                                                    | Operations       |
| ---------- | ----------------------------------------------------------------------------------------------------------- | ---------------- |
| Ping       | `GET /ping`                                                                                               | Health check     |
| Auth       | `POST /auth`                                                                                              | Token generation |
| Booking    | `GET /booking`, `POST /booking`, `GET /booking/{id}`, `PUT /booking/{id}`, `DELETE /booking/{id}` | Full CRUD        |

## Prerequisites

- [k6](https://k6.io/docs/get-started/installation/) installed and available on your `PATH`

## Running the Tests

From the `performance/` directory:

```bash
# Run individual test suites
npm run test:ping
npm run test:auth
npm run test:booking

# Run a quick smoke test (1 VU, 1 iteration)
npm run test:smoke

# Run all suites sequentially
npm run test:all
```

## Configuration

The following environment variables can be set to override defaults:

| Variable         | Default                                  | Description   |
| ---------------- | ---------------------------------------- | ------------- |
| `BASE_URL`     | `https://restful-booker.herokuapp.com` | API base URL  |

Example:

```bash
k6 run -e BASE_URL=https://my-api.example.com tests/booking-performance-tests.js
```

## Performance Thresholds

All test suites enforce the following global thresholds:

| Metric                        | Threshold |
| ----------------------------- | --------- |
| Error rate                    | < 1%      |
| 95th percentile response time | < 3000 ms |
| 99th percentile response time | < 5000 ms |
| Check pass rate               | > 95%     |

Individual suites apply tighter per-endpoint thresholds on top of these defaults.
