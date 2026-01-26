# Playwright learning

Link to tutorial: https://learn.microsoft.com/en-us/training/modules/build-with-playwright/

## Details of the tutorial

**End goal:** ~~Build~~ Understand an end-to-end test with Playwright.

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

The tutorial provides a brief overview of these concepts, but doesn't really provide any coding exercises that make use of these concepts.

Some of them are: TestConfig, TestProject, Fixures, Navigation, Locators, Assertions, and more. I'll just add a link to the tutorial's page, which then has links to all these core concepts in the docs.

[Link to Core Concepts in the tutorial](https://learn.microsoft.com/en-us/training/modules/build-with-playwright/2-introduction-to-playwright).

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

### Running the tests

To run the tests, enter:

```sh
npx playwright test
```

To view the report:

```sh
npx playwright show-report
```

To test only on one browser, like Chrome, use the `--project` flag:

```sh
npx playwright test --project chromium
```

#### Side note

I added the following alias in my bash to shorten the command:

```sh
alias pw='npx playwright'
```

This has allowed me to run the same commands but in short:

```sh
pw test # instead of `npx playwright test`
pw show-report # intead of `npx playwright show-report`
```

## Test Hierarchy

- A **test-case** is a `test()` function. Each project instantiates its own `test()` object based on project configuration.
  - A **test action** is every statement in a test-case that can be tracked in the reporter, trace-viewer or in UI mode tools.
- A **test suite** is a group of test-cases.
  - This grouping can be done _explicitly_, by placing the test-cases under the `test.describe()` method.
  - This grouping can be done _implicitly_, by putting the similar test-case files under one directory, and Playwright will automatically place those test files in the same group.
- Test suite hierachy:
  - every test run has a **root suite**
  - the root suite contains all the **project suites**
  - each project suite contains all the test files for that project, called the **file suite**
  - each file contains either individual test-cases, or explicitly grouped test-cases with `test.describe`
  - example (AI-generated):
  ```
  Test Run/
  ├── Root Suite
  │   ├── User Interface Testing (Project Suite)
  │   │   ├── login.spec.ts (File Suite)
  │   │   ├── checkout.spec.ts (File Suite)
  │   │   └── product.spec.ts (File Suite)
  │   └── API Testing (Project Suite)
  │       ├── user.spec.ts (File Suite)
  │       └── order.spec.ts (File Suite)
  ```

---

Skipping notes from the rest of the tutorial, and they are more about the superficial concepts of using Playwright, and doesn't really have any coding exercises where we can practise writing these tests ourselves.

---
