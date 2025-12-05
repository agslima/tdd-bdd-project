# Product Catalog Microservice - TDD & BDD Implementation

[![Python 3.9](https://img.shields.io/badge/Python-3.9-blue.svg)](https://python.org)
[![Methodology](https://img.shields.io/badge/Methodology-TDD%20%2F%20BDD-orange.svg)]()
[![Coverage](https://img.shields.io/badge/Coverage-95%25-brightgreen.svg)]()
[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen.svg)]()
[![License](https://img.shields.io/badge/License-Apache%202.0-lightgrey.svg)](https://opensource.org/licenses/Apache-2.0)
## Project Overview

This project implements a backend RESTful API for an **E-commerce Product Catalog**, built strictly following **Test Driven Development (TDD)** and **Behavior Driven Development (BDD)** methodologies.

The goal was not just to build an API, but to ensure high software quality and reliability by writing tests *before* the actual code implementation. It demonstrates the use of **Gherkin syntax** for acceptance testing and standard **Unit Testing** for business logic.

## Tech Stack & Methodologies

* **Language:** Python 3.9
* **Framework:** Flask
* **Database:** SQLAlchemy (ORM)
* **BDD Framework:** Behave (Gherkin syntax)
* **TDD Framework:** Nose / Pytest
* **Tooling:** Selenium (for automated UI/Integration testing)

## Key Engineering Practices

### 1. Test Driven Development (TDD)

Following the **Red-Green-Refactor** cycle:
* **Unit Tests:** Created comprehensive tests in `tests/test_models.py` to validate database models before migration.
* **Controller Tests:** Implemented `tests/test_routes.py` to verify HTTP endpoints (GET, POST, PUT, DELETE) using mocks.
* **High Coverage:** Ensured that critical business logic is fully covered by automated tests.

### 2. Behavior Driven Development (BDD)

Used to bridge the gap between technical implementation and business requirements:
* **Feature Files:** Defined business rules in `features/products.feature` using natural language (English).
* **Step Definitions:** Implemented steps in `features/steps/load_steps.py` to translate Gherkin scenarios into executable Python code.
* **Acceptance Criteria:** Validated scenarios like "Creating a Product", "Updating Inventory", and "Searching by Category".

## Project Structure

This repository is organized to separate business behavior (features) from technical implementation (service):

```text
├── features/               <- BDD Acceptance Tests (Behave)
│   ├── steps/              <- Python step definitions
│   │   ├── load_steps.py   <- Data loading steps
│   │   └── web_steps.py    <- Web interaction steps
│   ├── environment.py      <- Test environment setup
│   └── products.feature    <- Gherkin scenarios (The "Specs")
├── service/                <- Application Source Code
│   ├── models.py           <- Database Models
│   └── routes.py           <- API Controllers
├── tests/                  <- TDD Unit Tests
│   ├── test_models.py      <- Model logic tests
│   └── test_routes.py      <- Endpoint tests
└── config.py               <- App configuration
```

## 🚀 How to Run

Prerequisites
 * Python 3.9+
 * Virtual Environment

Setup Environment

### Install dependencies

```bash
bash bin/setup.sh
```

### Activate virtual environment (if needed)

```bash
source venv/bin/activate
```

Running the Tests
1. Run TDD Unit Tests (Nose)
To execute the unit tests and check code quality:

```bash
nosetests
```

2. Run BDD Scenarios (Behave)
To execute the acceptance tests defined in the feature files:

```bash
behave
```

<p align="left">
<img src="images/behave-success.png" alt="Behave execution success screenshot" width="700"/>
<em>Figure 1: Successful execution of BDD scenarios, validating business rules against the implementation.</em>
</p>

## 🥒 Example Scenario (Gherkin)

​The core of this project's documentation lies in the .feature files. Here is an example of a scenario implemented:

```gherkin
  Feature: The product service store
  As a Catalog Administrator
  I need a RESTful catalog service
  So that I can keep track of all my products

  Scenario: Create a Product
    Given the following products exist
      | name        | category | price |
      | Fedora      | Hats     | 12.95 |
    When I visit the "Home Page"
    And I press the "Create" button
    Then I should see the message "Success"
```

## ⚖️ License

This project is licensed under the Apache 2.0 License.
Based on the curriculum for the IBM DevOps and Software Engineering Professional Certificate.
