# Supplement Data Integration and Cleaning – 1001-Experiments Project

This project focuses on preparing and integrating multiple data sources for **1001-Experiments**, a company that creates personalized supplements based on users’ health metrics and habits. The goal was to clean, standardize, and merge four months of data from different sources into a single unified dataset that gives a comprehensive view of each user's supplement usage and health performance.

## 🛠️ What I Did

I developed a Python function `merge_all_data()` that:
- Loads and cleans data from the following CSV files:
  - `user_health_data.csv`
  - `supplement_usage.csv`
  - `experiments.csv`
  - `user_profiles.csv`
- Merges them into a single DataFrame using user identifiers and dates.
- Handles inconsistencies in units (e.g., converts supplement dosage from mg to grams).
- Fills in required default values where appropriate (e.g., `'No intake'` when no supplement was taken).
- Standardizes age groups and deals with missing demographic or health information as specified.

## 🧾 Output Dataset

The final DataFrame returned by the function includes the following columns:

| Column Name           | Description |
|-----------------------|-------------|
| `user_id`             | Unique identifier for each user (no missing values). |
| `date`                | Date of health data or supplement intake (date format, no missing values). |
| `email`               | Contact email of the user (no missing values). |
| `user_age_group`      | Age group (e.g., '18-25', '26-35', etc. or 'Unknown'). |
| `experiment_name`     | Name of the experiment linked to the supplement (can be missing). |
| `supplement_name`     | Name of the supplement taken, or `'No intake'`. |
| `dosage_grams`        | Supplement dosage in grams (converted from mg where needed). |
| `is_placebo`          | Boolean indicating if supplement was placebo (nullable). |
| `average_heart_rate`  | Average heart rate (nullable). |
| `average_glucose`     | Average glucose level (nullable). |
| `sleep_hours`         | Total sleep hours from previous night (nullable). |
| `activity_level`      | Activity level score (0–100, nullable). |

## 📈 Purpose

This cleaned and merged dataset is crucial for enabling:
- Accurate analysis of user behavior and supplement effectiveness.
- Easier downstream modeling and reporting by data scientists.
- Improved recommendation and personalization systems for 1001-Experiments.

## ▶️ Usage

Once all four CSVs are in your working directory, simply run:
```python
merged_df = merge_all_data('user_health_data.csv', 'supplement_usage.csv', 'experiments.csv', 'user_profiles.csv')
