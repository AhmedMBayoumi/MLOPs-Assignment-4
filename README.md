# Assignment 4: Machine Learning CI Pipeline

## Project Overview

This repository contains the implementation and debugging of a Machine Learning Continuous Integration (CI) pipeline for the DSAI 406: Machine Learning Engineering for Production course at the School of Computational Sciences and Artificial Intelligence, Zewail City of Science and Technology. The goal of this project was to identify and resolve configuration issues within a GitHub Actions workflow to ensure automated validation and testing of ML models.

## Identified Issues and Solutions

The original `ml-pipeline.yml` file contained three primary technical bugs that prevented successful execution:

### 1. Missing Repository Checkout

- **Bug**: The workflow did not include a step to fetch the repository content, causing subsequent steps to fail because they could not locate the source code or `requirements.txt`.
- **Solution**: Integrated the `actions/checkout@v3` action at the beginning of the workflow steps to pull the code into the runner environment.

### 2. YAML Indentation Errors

- **Bug**: The `uses`, `with`, and `run` keys were incorrectly indented and did not align properly with their corresponding `name` keys, violating YAML syntax rules for GitHub Actions.
- **Solution**: Standardized the indentation across the entire file to ensure all step attributes are correctly aligned with the step definitions.

### 3. Undefined Linter Execution

- **Bug**: The "Linter Check" step was declared in the file but lacked any actual commands or specifications for execution.
- **Solution**: Added the `flake8` package to the environment and updated the `run` key to execute `pip install flake8` followed by the `flake8` command to perform static code analysis.

## Pipeline Performance and Validation

The corrected pipeline was validated through multiple runs on GitHub Actions.

- **Workflow Execution**: Successful runs were recorded for both `push` and `pull_request` events, with each run taking approximately 2 minutes to complete.
- **Branch Strategy**: Final validation was conducted on a test branch to comply with requirements regarding branch-specific execution.
- **Security Integration**: The pipeline includes GitGuardian security checks to ensure no secrets are exposed in the codebase.
