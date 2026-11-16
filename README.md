# Understats — Statistical Analysis Decision Tree Portal

## Overview

Understats is a Django-based interactive statistical analysis portal designed to guide users through the selection and execution of statistical methods, with an emphasis on applications in biomedical research.

The portal incorporates an interactive decision tree that helps users navigate statistical questions and identify appropriate analytical methods. Each statistical module processes user-provided datasets or uses built-in sample datasets for demonstration.

## Features

### Interactive Statistical Decision Tree

- Step-by-step navigation through statistical decision-making questions.
- Guidance toward appropriate statistical methods based on data characteristics and analytical objectives.
- Integrated execution of statistical analyses and presentation of results.

### Statistical Analysis Modules

The portal supports:

- **Hypothesis Testing:** One-sample, two-sample and paired-sample statistical tests.
- **Analysis of Variance (ANOVA):** One-way and repeated-measures ANOVA.
- **Categorical Data Analysis:** Analysis of categorical observations and contingency tables.
- **Regression Analysis:** Simple and multiple linear regression, nonlinear regression, and binomial, ordinal and multinomial logistic regression.
- **Survival Analysis:** Statistical comparison of survival outcomes.
- **Parameter Estimation:** Estimation of statistical parameters and confidence intervals.
- **Power and Sample-Size Analysis:** Statistical power calculations and sample-size estimation.

### Data Input and Visualisation

- Upload datasets in `.dat`, `.csv`, or `.txt` formats.
- Use built-in sample datasets when no file is uploaded.
- View statistical results, model diagnostics, and graphical visualisations.
- Access statistical explanations and interpretation guidance.

## Requirements

- Python 3.12 (tested with Python 3.12.4)
- Git
- Python packages listed in `requirements.txt`

## Installation

### 1. Clone the repository

```bash
git clone --branch sid-ann-portal-update https://github.com/albertocorrias/understats.git
cd understats
```

### 2. Create a virtual environment

On Windows PowerShell, with Python 3.12 installed:

```powershell
py -3.12 -m venv .venv
```

Activate the environment:

```powershell
.\.venv\Scripts\Activate.ps1
```

Alternatively, you can run the virtual environment's Python executable directly without activating it.

### 3. Install dependencies

```powershell
python -m pip install -r requirements.txt
```

### 4. Configure the Django secret key

Generate a secret key:

```powershell
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

Set the generated key in your PowerShell session:

```powershell
$env:DJANGO_SECRET_KEY = "YOUR_GENERATED_SECRET_KEY"
```

Replace the placeholder with the generated value.

Do not commit secret keys to GitHub.

The environment variable must be set again when starting a new PowerShell session.

### 5. Initialize the database

```powershell
python manage.py migrate
```

### 6. Restore the decision-tree data

The repository includes a Django fixture containing 27 decision-tree nodes.

Load the fixture:

```powershell
python manage.py loaddata decision_tree_nodes
```

### 7. Start the development server

```powershell
python manage.py runserver
```

Open the portal in your browser:

http://127.0.0.1:8000/questions/

The Django development server is intended for local development and testing, not production deployment.

## Sample Datasets

The `sample_data/` directory contains 25 example datasets covering different statistical analysis methods.

If no dataset is uploaded, the relevant analysis module can load its corresponding sample dataset.

These datasets allow users to explore the statistical methods without preparing their own input files.

## Testing and Reproducibility

The application was tested using a fresh clone of the GitHub repository and a newly created Python 3.12 virtual environment.

The following setup steps were completed successfully:

- Installation of dependencies from `requirements.txt`.
- Django system configuration check.
- Application of database migrations.
- Restoration of all 27 decision-tree nodes.
- Launch of the Django application from the fresh clone.

The automated Django test suite currently contains 34 tests, of which 30 passed and four failed during the latest recorded run.

The four known failures involve two hypothesis-test p-value formatting assertions and two regression tests expecting nonlinear-override interface text. These require review before the automated test suite can be considered fully passing.

Run the test suite with:

```powershell
python manage.py test
```

## Project Structure

```text
understats/
├── analytics/                 # Statistical analysis modules
├── django_decision_tree/      # Django project configuration
├── questions/                 # Decision tree, views and templates
│   ├── fixtures/              # Decision-tree data
│   ├── migrations/            # Database migrations
│   ├── static/                # Application CSS and static assets
│   └── templates/             # HTML templates
├── sample_data/               # Example statistical datasets
├── manage.py                  # Django management script
└── requirements.txt           # Python dependencies
```

## Repository

This development version is available at:

https://github.com/albertocorrias/understats/tree/sid-ann-portal-update

The project is maintained within the Understats GitHub repository. Contributions and original project authorship should be credited according to the repository's existing documentation and licence.