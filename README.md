# Bayesian-Knowledge-Tracing-for-Lecture-Quiz-Sequences
Modeling Knowledge Progression in MOOCs
# Overview
This project extends classical Bayesian Knowledge Tracing (BKT) by incorporating lecture engagement and time-gap data into the knowledge estimation pipeline — two behavioral signals that traditional quiz-only models ignore.
Using a curated dataset of over 6,000 lecture–quiz records from a Coursera MOOC, we compare a Lecture-Quiz BKT model against a Quiz-Only BKT model to evaluate how lecture completion and the time interval between lectures and quizzes affect knowledge state prediction.

<p>
  <img src="https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white"/>
  <img src="https://img.shields.io/badge/pyBKT-1.4%2B-4CAF50?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/License-MIT-lightgrey?style=for-the-badge"/>
</p>
<p><i>An extended BKT model that integrates lecture engagement and time-gap data to improve knowledge state estimation in online learning environments.</i></p>
<!-- REPLACE with your banner or demo image -->
<!-- <img src="images/banner.png" alt="Project Banner" width="800"/> -->
</div>

# Key Finding: 
The Lecture-Quiz model achieved an AUC of 0.9640 and Log-Loss of 0.0156, outperforming the Quiz-Only model (AUC: 0.9370 | Log-Loss: 0.0272).

## Research Questions
#RQ1What is the effect of lecture completion on initial knowledge states p(Know₀) across different learner profiles?
RQ2How do different time intervals between lecture completion and quiz attempts impact the learning rate p(Learn)?
RQ3Can lecture-quiz sequences improve the predictive accuracy of BKT models compared to quiz-only models?

## Methodology
![BKT Workflow](images/WORKFLOW BKT.jpeg)
RQ1 bar chart — p(Know₀) by quiz topic

Dataset
The dataset (final_dataset.csv) is derived from Coursera activity logs and contains 6,000+ lecture–quiz interaction records.
ColumnDescriptionStudent IDAnonymized unique student identifierLecture IDUnique identifier for each lectureLecture CompletedWhether the lecture was completed (Yes/No)Lecture TimeTimestamp of lecture completionQuiz IDUnique identifier for each quizQuiz Correct (1)/Incorrect (0)Binary quiz outcome (1 = correct, 0 = incorrect)Quiz TimeTimestamp of quiz attemptTime Gap (mins)Minutes elapsed between lecture completion and quiz attempt
