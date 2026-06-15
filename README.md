# demo-rest-api-tests-javascript

JavaScript-based test suites for the [Restful Booker API](https://restful-booker.herokuapp.com). This repository is organized by test layer, with each layer living in its own top-level folder alongside its own dependencies, configuration, and documentation.

## Test Layers

| Folder | Type | Tool |
|---|---|---|
| `performance/` | Performance & load testing | [k6](https://k6.io) |

The `performance/` folder contains its own `README.md` with setup instructions, how to run the tests, and configuration details.

## API Under Test

All test layers target the [Restful Booker API](https://restful-booker.herokuapp.com), a publicly hosted demo API that exposes endpoints for health checks, authentication, and hotel booking management.
