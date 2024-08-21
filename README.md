# {{ cookiecutter.project_name }}

{{ cookiecutter.description }}

This Cookiecutter template is designed to help you quickly start a new data science project. It provides a flexible and adaptable structure suitable for various types of data science projects, including general-purpose projects, computer vision, NLP, time series analysis, and more.

## Table of Contents

- [{{ cookiecutter.project\_name }}](#-cookiecutterproject_name-)
  - [Table of Contents](#table-of-contents)
  - [Features](#features)
  - [Requirements](#requirements)
  - [Installation](#installation)
    - [Install Cookiecutter](#install-cookiecutter)
  - [Usage](#usage)
    - [Generate a New Project](#generate-a-new-project)
    - [Navigate to Your Project](#navigate-to-your-project)
    - [Set Up the Environment and Dependencies](#set-up-the-environment-and-dependencies)
    - [Run Makefile Commands](#run-makefile-commands)
  - [Project Structure](#project-structure)
  - [Customization Options](#customization-options)
  - [Contributing](#contributing)
  - [License](#license)

## Features

- **Flexible Project Structure**: Supports various data science domains (e.g., NLP, computer vision, time series).
- **Modular Code Organization**: Easily extendable and maintainable codebase.
- **Integrated Testing**: Includes unit testing with `pytest`.
- **Automation with Makefile**: Automate tasks like environment setup, testing, and running models.
- **Optional SonarQube Integration**: For code quality and security analysis.

## Requirements

To use this Cookiecutter template, you need the following installed:

- Python >= {{ cookiecutter.python_version }}
- [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/installation.html) >= 2.2.0
- Conda (optional, for environment management)
- pipx (optional, for isolated package installation)

## Installation

### Install Cookiecutter

```bash
pip install cookiecutter
```

Or using `pipx`:

```bash
pipx install cookiecutter
```

## Usage

### Generate a New Project

Run the following command to generate a new project using this template:

```bash
cookiecutter git@github.com:simonherlin/cookiecutter-datascience.git
```

You will be prompted to enter various details like `project_name`, `author_name`, `description`, and more.

### Navigate to Your Project

After the project is generated, navigate to your new project directory:

```bash
cd {{ cookiecutter.project_name }}
```

### Set Up the Environment and Dependencies

Use the `Makefile` to automate the environment setup and dependency installation:

```bash
make install
```

### Run Makefile Commands

Other tasks can also be automated using the `Makefile`:

- Run tests: `make test`
- Lint project: `make lint`
- Use sonarqube: `make sonar`
- Read the documentation for more information

## Project Structure

The generated project structure is designed to be adaptable to various types of data science projects:

```bash
{{ cookiecutter.project_name }}/
├── data/
├── notebooks/
├── docs/
├── src/
├── config/
├── scripts/
├── reports/
├── logs/
├── environment.yml
├── requirements.txt
├── README.md
└── Makefile
```

## Customization Options

During project generation, you can customize various aspects of the project:

- **`project_name`**: The name of your project.
- **`author_name`**: Your name or your team’s name.
- **`description`**: A brief description of the project.
- **`project_type`**: Choose from "General", "Computer Vision", "NLP", "Time Series".
- **`use_sonarqube`**: Optionally integrate with SonarQube for code quality analysis.

## Contributing

Contributions are welcome! If you find a bug or have a feature request, please open an issue or submit a pull request.

## License

This project is licensed under the [{{ cookiecutter.license }}](LICENSE) License.