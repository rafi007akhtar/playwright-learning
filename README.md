# Playwright learning

Link to tutorial: https://learn.microsoft.com/en-us/training/modules/build-with-playwright/

## Details of the tutorial

**End goal:** Build an end-to-end test with Playwright.

**Objectives:**

- Use Playwright to test a sample web application.
- Learn:
  - the structure of a Playwright project,
  - how to create new test suite,
  - how to refine your tests,
  - how to run tests,
  - how to view test reports.
- Use VS Code to run, debug and record new tests.

## About Playwright

### What it is

- It's an [open-source](https://github.com/microsoft/playwright) framework by Microsoft for end-to-end testing of modern _web_ apps.
- It was launched in 2020.
- Offical website: https://playwright.dev/

### Benefits of using it

- **Unified API**
  - supports multiple browser engines like Chromium, WebKit and Firefox,
  - supports device emulation for mobile coverage
  - supports headed execution for debugging convenience and headless execution for CI/CD flows
- **Elimination of _flaky_ tests**
  - implements "auto-wait" and "auto-retry" which means no artificial timeouts
  - features "tracing" and "time-travel" options to debug and fix issues when tests fail
- **Test isolation**
  - every test runs independent of other tests, in its own BrowserContext
  - tests run in parallel for optimization
  - one test failure doesn't affect other tests
- **Tooling**
  - with tools like the VS Code extension and CLI tools.

## Playwright Core Concepts

TODO: Expand on this as you code through the tutorial.

### TestConfig

### TestProject

### Test Timeout

### Fixtures

### Navigation

### Locators

### Assertions

### Annotations

### use Options

### Page object Models

## Getting started with Playwright

### Installation / Initialization

The following command will install Playwright (if not already installed) and create a new Playwright project inside the current folder.

```sh
npm init playwright@latest
```

I went with all default options, meaning:

- TypeScript for the language
- "test" as the name of the test directory
- add file for GitHub actions
- install Playwright browsers

### Structure

The project structure is:

- [playwright.config.ts](./playwright.config.ts) file: the test configuration file
- [.github/workflows/playwright.yml](./.github/workflows/playwright.yml) file: GitHub actions for automating tests
- [tests/](./tests/) folder: top level folder containing test files and other test subfolders

