# Selenium Automation Framework

This project is a **dynamic data-driven Selenium automation framework** built using **Java, Selenium WebDriver, TestNG, and YAML configuration files**.

The framework allows tests to be executed dynamically by defining test cases and test data in **YAML files**, without modifying the Java test code.

It follows a **modular architecture** that separates test definitions, test data, page actions, and framework utilities.

<img width="774" height="517" alt="Screenshot 2026-03-10 at 11 45 13 PM" src="https://github.com/user-attachments/assets/ab665a8e-4491-4248-9a67-cf908aa3907b" />

---

# Framework Components

### Runner

The `Runner` reads the test definitions from `tests.yaml` and creates TestNG tests dynamically.

### DynamicTest

`DynamicTest` executes the steps defined in YAML using Java reflection.

### DriverFactory

Responsible for initializing and closing the Selenium WebDriver.

### BrowserFunctions

Contains reusable Selenium methods such as:

* click
* enter text
* wait for elements
* screenshot capture

### Page Objects

Page classes contain UI element locators and actions.

### Reporting

The framework integrates **Extent Reports** for execution reporting and screenshots.

### Utilities

Utility classes are used for:

* reading configuration files
* reading YAML test files
* managing test data

---

# Framework Features

* Dynamic test execution
* YAML based test definition
* Data-driven testing
* Parallel execution support
* Screenshot capture
* Extent reporting
* CI/CD ready execution
* Modular framework design

---

# Test Structure

Tests are defined in `tests.yaml`.

Example:

```yaml
TC001:
  name: "Login valid"
  tags: ["smoke","sanity"]
  testData: "login_valid"

  steps:
    - class: "otherTest.LoginTest"
      method: "testLogin"
```

Each test contains:

| Field    | Description        |
| -------- | ------------------ |
| name     | Test description   |
| tags     | Test grouping      |
| testData | Dataset name       |
| steps    | Methods to execute |

---

# Test Data

Test data is maintained in `testData.yaml`.

Example:

```yaml
login_valid:
  - iteration: "1"
    email: "automationuser"
    password: "Learning@830$3mK2"
```

The framework automatically runs all iterations.

---

# Configuration

Execution settings are managed in `config.properties`.

Example:

```properties
testsFile=tests.yaml
testDataFile=testData.yaml
parallel=true
threads=5
suiteName=AutomationSuite
appUrl=https://sample.cpm

runTests=
runTags=
```

---

# Running Tests

### Run all tests

```properties
runTests=
runTags=
```

---

### Run a specific test

```properties
runTests=TC001
```

---

### Run multiple tests

```properties
runTests=TC001,TC002
```

---

### Run tests by tag

```properties
runTags=smoke
```

---
# Prerequisites

Ensure the following tools are installed.

### Java

```
java -version
```

### Maven

```
mvn -version
```

### Git

```
git --version
```

---

# Clone the Repository

```
git clone https://github.com/automationtesterag/WebAutomation.git
```

Navigate into the project:

```
cd WebAutomation
```

---

# Install Dependencies

Download project dependencies using Maven.

```
mvn clean install
```

---

# Execute the Framework (CLI)

The framework runs through the **TestRunner class**.

Run using:

```
mvn clean test-compile exec:java -Dexec.mainClass="otherTest.TestRunner" -Dexec.classpathScope=test
```

This command will:

1. Clean previous builds
2. Compile test classes
3. Execute `TestRunner`
4. Run tests defined in `tests.yaml`

---

# Reports

Reports are generated after execution.

### TestNG Reports

```
test-output/
```

### Extent Reports

```
ExtentReports/
```

Reports include:

* execution status
* logs
* screenshots
* test metrics

---

# Dependencies

Main libraries used in this framework:

* Selenium WebDriver
* TestNG
* Apache POI
* SnakeYAML
* Extent Reports

---

# CI/CD Ready

The framework is designed to run easily in CI/CD pipelines such as:

* GitHub Actions
* GitLab CI
* Jenkins

Execution can be triggered using the same Maven command.
