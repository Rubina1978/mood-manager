<i class="fa-solid fa-link"></i><a href="https://mood-manager.onrender.com/">LIVE SITE</a>

<p align="center">
  <img src="./static/images/mood_manager_banner.png" width="90%"  alt="Project banner" />
</p>

<h1 align="center">Mood Manager</h1>

<p align="center">
  An interactive predictive web application exploring how lifestyle factors influence mood and stress levels.
</p>


<p align="center">
    <a href="./jupyter_notebooks/01_clean_the_data.ipynb">Data Clean</a>
    &nbsp;&nbsp;-&nbsp;&nbsp;
    <a href="./jupyter_notebooks/02_predicting_mood_score.ipynb">Mood Score Model</a>
    &nbsp;&nbsp;-&nbsp;&nbsp;
	<a href="./jupyter_notebooks/03_predicting_stress_level.ipynb">Stress Level Model</a>
    &nbsp;&nbsp;-&nbsp;&nbsp;
    <a href="https://mood-manager.onrender.com/">Live Demo</a>
</p>

<br />
<br />

<details>
<summary align="center">Table of contents (Click to show)</summary>

<br/>

- [Overview](#overview)
- [Dataset](#dataset)
- [Problem](#problem)
- [Solution](#solution)
- [Input Variables](#input-variables)
- [Scoring Logic](#scoring-logic)
- [Features](#features)
- [How it Works](#how-it-works)
- [UI Design & Responsiveness](#ui-design-and-responsiveness)
- [Responsiveness](#responsiveness)
- [Technical Architecture](#technical-architecture)
- [Project Structure](#project-structure)
- [Installation (locally)](#installation-locally)
- [Deployment](#deployment)
- [Ethical Considerations](#ethical-considerations)
- [Future Improvements](#future-improvements)
- [Testing](#testing)
- [Contributors](#contributors)
- [Acknowledgements](#acknowledgements)

---

</details>

<br/>
<br/>

## Overview

**Mood Manager** is a predictive web application that analyzes user-selected lifestyle variables and generates:

- **Predicted Mood score (1–10)**
- **Predicted Stress score (1–10)**

Users adjust on-screen slider controls to simulate behavioural scenarios. Each variable begins at a neutral midpoint and can be increased or decreased to reflect different habits or conditions.

After clicking **Predict**, the system evaluates the selected values and returns quantified results. The application functions as a behavioural simulator, allowing users to explore how changes in lifestyle factors may influence emotional wellbeing.

## Dataset

The predictive model was trained using a dataset sourced from [Kaggle](https://www.kaggle.com).

- **Number of records:** 2,000
- **Variables include:** sleep hours, screen time, exercise minutes, pending tasks, interruptions, fatigue level, social hours, coffee consumption, diet quality, and weather conditions.

This dataset provided the basis for weighting the input variables in the scoring logic to generate Mood and Stress predictions.

## Problem

Lifestyle habits such as sleep, workload, fatigue, and social interaction significantly influence emotional wellbeing. However, these relationships are often difficult to interpret without structured feedback.

A simple and interactive system is needed to help visualize how behavioural factors may correlate with mood and stress levels.

## Solution

The application provides a structured interface where users can experiment with lifestyle variables and immediately observe predicted outcomes.

Rather than tracking or storing personal data, the system is designed for exploration — enabling users to simulate different scenarios and reflect on potential behavioural impacts.

## Input Variables

The predictive model evaluates the following factors:

- Sleep hours
- Screen time
- Exercise minutes
- Daily pending tasks
- Interruptions
- Fatigue level
- Social hours
- Coffee cups
- Diet quality
- Weather

A predictive model using linear regression was created that used these features as inputs and predicted a mood score and stress level.

## Scoring Logic

> Note: The scoring system is based on the Kaggle dataset’s variable distributions. Some extreme combinations (e.g., zero sleep) may not produce intuitively expected results due to dataset limitations.

The scoring system is rule-based and designed to model plausible behavioural relationships.

Each input variable contributes positively or negatively to Mood and Stress scores based on predefined weightings. Balanced inputs (midpoint values) represent a neutral state, while higher or lower extremes influence predictions proportionally.

Mood and Stress are calculated independently, allowing certain factors to impact stress more heavily than mood.

The final outputs are normalized to a 1–10 scale to provide clear, interpretable results.

The logic is modular, allowing future integration of machine learning models or adaptive weighting mechanisms.

## Features

- Linear Regression models to predict stress level and mood score
- Interactive slider-based input system
- Real-time mood and stress prediction
- Immediate results display
- Colour-coded feedback system
- Clean, responsive user interface
- Helpful information on how to improve mood or lower stress
- Modular architecture for future expansion

## How It Works

1. User adjusts slider controls representing lifestyle variables
2. Inputs are validated and processed server-side
3. Weighted scoring logic calculates Mood and Stress values
4. Results are displayed instantly with visual feedback

## UI Design and Responsiveness

The interface follows a mobile-first design approach using the Bootstrap grid system.

A structured colour system supports clarity and interpretation:

- **Blue** serves as the primary interface colour, providing a calm and neutral interaction environment.
- **Green** highlights positive outcomes (higher mood, lower stress).
- **Red** indicates elevated stress levels, drawing attention to higher-risk states.

This colour hierarchy reinforces meaning without overwhelming the user.

The layout adapts seamlessly across mobile, tablet, and desktop devices. 🚧 TODO - test

Colour-coded results:

- **Green:** High mood / low stress
- **Red:** Low mood / high stress
- **Yellow/Orange:** Intermediate states

## Responsiveness

![Demo image of responsive devices](./static/images/all-devices-black.png)

The application is designed mobile-first using the Bootstrap grid system.
Layouts adapt seamlessly across:

- **Desktop** – full-width charts and controls
- **Tablet** – stacked elements with preserved spacing
- **Mobile** – single-column layout for easy touch interaction

The input sliders, buttons, and results panels resize dynamically.
No functionality is lost on smaller screens, ensuring the simulation is usable across devices.

## Technical Architecture

### Backend

- Django
- Python

### Frontend

- HTML5
- CSS3
- Bootstrap 5
- JavaScript

### Database

- SQLite (development)
- PostgreSQL (production-ready)

## Project Structure

```text
├── README.md
├── __pycache__
│   └── env.cpython-312.pyc
├── charts
│   ├── correlation_matrix_heatmap.png
│   ├── distribution_of_categorical_columns_count_plots.png
│   ├── distribution_of_numerical_columns_histogram.png
│   ├── distribution_of_numerical_columns_violin_box_plots.png
│   ├── predicting_mood_score_linear_regression_residuals.png
│   ├── predicting_mood_score_linear_regression_scatter.png
│   ├── predicting_stress_level_linear_regression_residuals.png
│   └── predicting_stress_level_linear_regression_scatter.png
├── data_files
│   ├── mental_health_dataset_cleaned.parquet
│   └── mental_health_dataset_raw.csv
├── db.sqlite3
├── env.py
├── home
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-312.pyc
│   │   ├── admin.cpython-312.pyc
│   │   ├── apps.cpython-312.pyc
│   │   ├── forms.cpython-312.pyc
│   │   ├── models.cpython-312.pyc
│   │   ├── suggestions.cpython-312.pyc
│   │   ├── urls.cpython-312.pyc
│   │   └── views.cpython-312.pyc
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py
│   ├── migrations
│   │   ├── __init__.py
│   │   └── __pycache__
│   ├── models.py
│   ├── suggestions.py
│   ├── templates
│   │   ├── contact.html
│   │   ├── faq.html
│   │   ├── home
│   │   ├── improve_mood.html
│   │   ├── predict.html
│   │   └── reduce_stress.html
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── jupyter_notebooks
│   ├── 01_clean_the_data.ipynb
│   ├── 02_predicting_mood_score.ipynb
│   └── 03_predicting_stress_level.ipynb
├── manage.py
├── ml_models
│   ├── __pycache__
│   │   └── predict.cpython-312.pyc
│   ├── predict.py
│   ├── predicting_mood_score_linear_regression_model.pkl
│   └── predicting_stress_level_linear_regression_model.pkl
├── mood_manager
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-312.pyc
│   │   ├── settings.cpython-312.pyc
│   │   ├── urls.cpython-312.pyc
│   │   └── wsgi.cpython-312.pyc
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── requirements.txt
├── static
│   ├── css
│   │   └── main.css
│   ├── favicons
│   │   ├── apple-touch-icon.png
│   │   ├── favicon-96x96.png
│   │   ├── favicon.ico
│   │   ├── favicon.svg
│   │   ├── site.webmanifest
│   │   ├── web-app-manifest-192x192.png
│   │   └── web-app-manifest-512x512.png
│   ├── images
│   │   ├── correlation_matrix_heatmap.png
│   │   ├── distribution_of_categorical_columns_count_plots.png
│   │   ├── distribution_of_numerical_columns_histogram.png
│   │   ├── distribution_of_numerical_columns_violin_box_plots.png
│   │   ├── mood_manager_banner.png
│   │   ├── predicting_mood_score_linear_regression_scatter.png
│   │   └── predicting_stress_level_linear_regression_scatter.png
│   └── videos
│       └── sunset.mp4
├── structure.txt
└── templates
    └── base.html
```

## Installation (locally)

Clone the repository:

```bash
git clone https://github.com/yourusername/mood-manager.git
cd mood-manager
```

Add the right env variables in an env.py file:

```python
import os

os.environ["SECRET_KEY"] = "<YOUR-SECRET-KEY>"
```

Create a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate   # macOS/Linux
# .venv\Scripts\activate    # Windows
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run migrations and start the development server:

```bash
python manage.py migrate
python manage.py runserver
```

## Deployment

Deployed via Render

Environment variables required:

- SECRET_KEY
- DEBUG
- DATABASE_URL (if using PostgreSQL)

## Ethical Considerations

This application provides predictive indicators and does not offer medical or psychological diagnoses.

User inputs are not stored, and the tool is designed for exploratory purposes only.

Future production implementations should include secure authentication, encrypted data handling, and a clear privacy policy.

## Future Improvements

- A bigger bank of tips for the user
- Historical tracking and visual dashboards
- Personalised behavioural recommendations
- User authentication and profile management
- API endpoint for external integrations

## Testing

> Testing performed manually by all team members across multiple devices and browsers.

Testing focused on ensuring that user inputs are processed correctly, outputs are meaningful and all parts of the website function, and are relevant to the site.

- **Input validation:** Ensured slider values remain within expected ranges and handle edge cases (e.g., 0 or maximum values).
- **Output checks:** Verified Mood and Stress predictions respond consistently to varying inputs.
- **Functional testing:** Confirmed that Predict button triggers calculation and results update correctly.
- **Cross-browser / device checks:** Ensured layout and responsiveness work on desktop, tablet, and mobile screens.
- **Future testing plans:** Unit and integration tests can be added to automate validation as the project evolves.

## Contributors

- Alistair Driscoll - [https://www.linkedin.com/in/alistair-driscoll/](https://www.linkedin.com/in/alistair-driscoll/)
- Anthony Radose - [https://www.linkedin.com/in/anthony-radose-35a969236/](https://www.linkedin.com/in/anthony-radose-35a969236/)
- Pete Smith - [https://www.linkedin.com/in/petedanielsmith/](https://www.linkedin.com/in/petedanielsmith/)
- Hana Rubesova - [https://www.linkedin.com/in/hana-rubesova-6338b9104/](https://www.linkedin.com/in/hana-rubesova-6338b9104/)
- Barby Kelly - [https://www.linkedin.com/in/barby-kelly-130a362a3/](https://www.linkedin.com/in/barby-kelly-130a362a3/)

## Acknowledgements

- **Dataset source:** [Kaggle – Lifestyle Factors Dataset](https://www.kaggle.com) (2,000 records used to train the model)
- **AI assistance:** ChatGPT, for helping with README drafting, structure, and content refinement
- **Technical references:**
  - [Django Documentation](https://docs.djangoproject.com/)
  - [Bootstrap Documentation](https://getbootstrap.com/docs/)
  - [Python Official Documentation](https://www.python.org/)

This section recognises resources, inspiration, and tools that contributed to the development of this project.

- Django Documentation
- Bootstrap Documentation
- Python Official Documentation
- Hackathon Organisers

