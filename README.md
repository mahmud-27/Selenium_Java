
# Selenium Test Automation Framework

This project is a Test Automation Framework built using **Selenium**, **Java**, **TestNG**, and other tools following the **Page Object Model (POM)** and **Page Factory** design patterns. It supports **data-driven testing** with external files and uses **Maven** for dependency management.

---

## 📁 Project Structure

| Package/Folder                      | Description                                                                 |
| ----------------------------------- | --------------------------------------------------------------------------- |
| `base`                              | Contains base classes including the base driver setup and reusable methods. |
| `testCase`                          | Contains all the test cases.                                                |
| `utilities`                         | Common utility classes and helper methods used across the framework.        |
| `configFile`                        | Contains application and environment configuration files.                   |
| `logs`                              | Contains logging configurations and log files generated using **log4j**.    |
| `report`                            | Contains reports generated after test execution.                            |
| `testData`                          | Stores test data such as `.csv` or `.xlsx` files for data-driven testing.   |
| `Feature` (in `src/test/resources`) | Contains `.feature` files for BDD tests written in Gherkin syntax.          |

---

## 🔧 Tools & Dependencies

| Tool/Library                           | Purpose                                 |
| -------------------------------------- | --------------------------------------- |
| **Selenium WebDriver**                 | Browser automation                      |
| **TestNG**                             | Test execution and grouping             |
| **ReportNG**                           | Simple HTML reporting plugin for TestNG |
| **log4j**                              | Logging framework                       |
| **Apache POI**                         | Read/write Excel files for test data    |
| **WebDriverManager**                   | Automatic driver management             |
| **Maven**                              | Build and dependency management         |
| **Cucumber Java** / **Cucumber JUnit** | BDD support using Gherkin syntax        |

---

## 🧱 Page Object Model (POM)

* Ensures **separation of concerns** by separating test logic from page structure.
* Enhances **code reusability and maintainability**.
* Implemented using **Selenium PageFactory**:

  ```java
  PageFactory.initElements(new AjaxElementLocatorFactory(driver, 30), this);
  ```

---

## 🔄 Parameterization in Cucumber

Parameterization allows writing reusable step definitions with variable inputs. This is done using **placeholders** in `Scenario Outline` and `Examples`:

```gherkin
Scenario Outline: Login functionality
  Given I open the browser
  When I navigate to the login page
  And I enter "<username>" in the username box
  And I enter "<password>" in the password box
  Then I should see the Home Page

Examples:
  | username | password |
  | user1    | pass1    |
  | user2    | pass2    |
```

---

## 📊 Data-Driven Testing (DDT)

Data-Driven Testing in Cucumber allows the same test scenario to run multiple times with different inputs:

* Using **Scenario Outlines** and **Examples tables** in `.feature` files.
* Or by fetching test data from external sources like:

  * `.csv`
  * `.xlsx` using **Apache POI**
  * `.json`

This enhances test coverage without duplicating scenarios.

---

## ✅ Sample Test Steps

```gherkin
Given Open Browser  
When Navigate to login page  
And Enter user in UserName box  
And Enter pass in the password box  
And Click login button  
Then Verify user navigates to Home Page  
```
