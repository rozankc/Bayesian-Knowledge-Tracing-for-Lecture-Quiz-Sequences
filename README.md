# Bayesian-Knowledge-Tracing-for-Lecture-Quiz-Sequences
Modeling Knowledge Progression in MOOCs

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

# Project Overview
Massive Open Online Courses (MOOCs) have transformed scalable education, yet accurately tracking student knowledge remains a challenge. Traditional Bayesian Knowledge Tracing (BKT) models rely solely on quiz results — ignoring whether students engaged with lecture content at all.
This project addresses that gap by building a Lecture-Quiz BKT model that incorporates:

✅ Whether a student completed the lecture before attempting the quiz
✅ The time gap (in minutes) between lecture completion and quiz submission

We compare this against a baseline Quiz-Only BKT model using a dataset of 6,000+ lecture–quiz records from a Coursera MOOC.

# Key Result: 
The Lecture-Quiz model achieved an AUC of 0.9640 and Log-Loss of 0.0156, outperforming the Quiz-Only model (AUC: 0.9370 | Log-Loss: 0.0272).

# Research Questions
📌RQ1 What is the effect of lecture completion on initial knowledge states p(Know₀) across different learner profiles?
📌RQ2 How do different time intervals between lecture completion and quiz attempts impact the learning rate p(Learn)?
📌RQ3 Can lecture-quiz sequences improve the predictive accuracy of BKT models compared to quiz-only models?

#  Workflow
![BKT Workflow](images/WORKFLOW_BKT.jpeg)
  <em>Figure 1 — End-to-end pipeline: from raw Coursera data to BKT knowledge state predictions</em>
</p>
The pipeline follows five stages:
Raw Coursera Data  ──►  Feature Engineering  ──►  Structured Dataset
                                                          │
                                              pyBKT Model Training
                                                          │
                                       Knowledge State Predictions & Evaluation
