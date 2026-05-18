# Bayesian Knowledge Tracing for Lecture-Quiz Sequences
## Modeling Knowledge Progression in MOOCs

> **Course:** INFO 5731 — Computational Methods for Information Systems
> **Institution:** University of North Texas

---

## 📋 Table of Contents

- [Abstract](#-abstract)
- [Keywords](#-keywords)
- [1. Introduction](#1-introduction)
- [2. Related Work](#2-related-work)
- [3. Methodology](#3-methodology)
- [4. Results](#4-results)
- [5. Discussion](#5-discussion)
- [6. Limitations & Future Work](#6-limitations--future-work)
- [Acknowledgments](#-acknowledgments)
- [References](#-references)

---

## 📄 Abstract

Massive Open Online Courses (MOOCs) have become a key platform for scalable education, but understanding and monitoring student progress remains a challenge. Bayesian Knowledge Tracing (BKT) is widely accepted for modeling the evolution of student knowledge over time; yet most approaches rely solely on quiz results, ignoring the time students spend on lecture engagement.

This study addresses this gap by integrating **lecture completion** and **time-gap data** into BKT models. A traditional quiz-only BKT model is compared against a lecture-quiz sequence model to better understand learning behaviors in MOOCs.

**Key findings:**
- Learners who completed lectures before attempting quizzes had significantly **higher initial knowledge states**
- Learners who spent more time between lectures and quizzes demonstrated **higher learning rates**
- The lecture-quiz model **outperformed** the quiz-only model in predictive accuracy

These findings highlight the importance of including lecture engagement data in learning models, supporting adaptive learning pathways and more effective online course design.

---

## 🔑 Keywords

`Bayesian Knowledge Tracing` `MOOCs` `Lecture-Quiz Sequences` `Knowledge State Estimation` `Learning Rate` `Predictive Accuracy` `Adaptive Learning`

---

## 1. Introduction

Massive Open Online Courses (MOOCs) are making revolutionary changes in the learning field — presenting flexible and scalable opportunities for education. However, accurately assessing students' knowledge progress in such settings remains a challenge. Traditional BKT models estimate a student's knowledge state using only quiz performance, disregarding important parameters such as lecture engagement and the timing difference between instructional content and assessment.

New studies have sought to strengthen knowledge tracing models with behavioral and metacognitive data. Hidayah and Am (2023) investigated adaptive quiz scheduling within Moodle-based learning management systems, arguing that BKT can inform assessments for effective student engagement and retention. Similarly, Shen et al. (2021) introduced the LP Knowledge Tracing Model, exploring how temporal learning behaviors can improve student modeling in MOOCs.

This study addresses crucial gaps by incorporating **lecture-quiz pairings** to improve the accuracy of knowledge state prediction using timestamps and time intervals between lectures and quizzes.

### Research Questions

| # | Research Question |
|---|-------------------|
| **RQ1** | What is the effect of lecture completion on initial knowledge states `p(Know₀)` across different learner profiles? |
| **RQ2** | How do different time intervals between lecture completion and quiz attempts impact the learning rate `p(Learn)`? |
| **RQ3** | Can the inclusion of lecture-quiz sequences improve the predictive accuracy of BKT models compared to quiz-only models? |

### Contributions

- **Improved BKT Models** — Demonstrates that lecture-quiz integration in BKT outperforms quiz-only models
- **Actionable MOOC Design Insights** — Proposes data-driven guidelines for optimal lecture-quiz intervals
- **Adaptive Learning Frameworks** — Methodologies for lecture and quiz sequencing to maximize learner performance
- **Personalized Learning Pathways** — Concrete means for adaptive interventions (reminders, replays, follow-ups)
- **Scalability** — Framework applicable beyond MOOCs to K–12, corporate training, and blended learning

---

## 2. Related Work

BKT is extensively used to predict student knowledge states based on lecture times and quiz performance. Conventional BKT models assume binary knowledge states and model learning based on quiz performance alone, excluding significant variables like lecture attendance and individual learning trails (Badrinath et al., 2021). Overreliance on quizzes constrains predictability, while static assumptions fail to capture variability in student activity (Carlon & Cross, 2022).

In response, researchers have enriched models with learner behavior and metacognition data. RABKT (Carlon & Cross, 2022) improved predictions using student self-assessed confidence. LBKT (Xu et al., 2023) incorporated behavioral variables such as quiz attempts, guessing, and reaction time for more sophisticated knowledge state representation.

### 2.1 Applications of BKT in MOOCs and Adaptive Learning

Badrinath et al. (2021) showed that students who watched lectures before quizzes had significantly higher initial knowledge probabilities. Hybrid approaches combining BKT and deep learning have also improved predictive performance — Zhang et al. (2024) introduced BCKVMN, combining BKT with LSTM-based memory networks for dynamic student knowledge modeling.

In adaptive systems, BKT models have enabled personalized learning activities. Hidayah and Am (2023) demonstrated the benefits of BKT-based adaptive quiz scheduling in Moodle for increasing student engagement and retention. Pardos and Heffernan (2021) presented a systematic 25-year review of BKT, emphasizing the need to enhance models to handle increasing data complexity.

### 2.2 Data Sparsity in Knowledge Tracing using Generative AI

Generative AI has emerged as a solution to the data sparsity problem in knowledge tracing. Kose and Wei-Kocsis (2025) developed a diffusion model that produces artificial learning records, enabling models to generalize better by training on more stable and diverse datasets. Ma et al. (2025) used Layer-wise Relevance Propagation to highlight relevant inputs, while Pandey and Srivastava (2020) introduced relation-aware self-attention (RKT) to improve contextual interpretability in student modeling.

### 2.3 Instructional Material Sequencing in BKT

Ben David et al. (2016) presented a sequencing approach to instructional content using BKT, incorporating partial credit scores, multiple attempts, and item difficulty. Spaulding and Breazeal (2015) integrated affective states into BKT using a robot tutor, showing that confusion and interest states enhance BKT predictability. Liu et al. (2021) proposed Fuzzy BKT (FBKT) and Type-2 FBKT, deploying fuzzy logic to manage uncertainty in student cognition assessment.

### 2.4 Maintaining Equity and Fairness in Knowledge Tracing

Rogers and Feng (2024) noted that students with multiple quiz attempts tend to be favored by current models, leading to performance prediction bias. They proposed fairness-aware approaches that rescale predictions to offer more comparable results across student groups. Shen et al. (2024) constructed open-source repositories (EduData and EduKTM) to make KT methods more flexible and scalable across education domains.

---

## 3. Methodology

### 3.1 BKT Modeling Workflow

<!-- Add your workflow diagram here -->
<p align="center">
  <img src="images/workflow.png" alt="BKT Modeling Workflow" width="750"/>
  <br/>
  <em>Figure 1 — Workflow for BKT Modeling</em>
</p>

The architectural pipeline consists of five stages:

| Stage | Description |
|-------|-------------|
| **1. Data Input** | Raw Coursera logs: student IDs, lecture metadata, timestamps, quiz grades |
| **2. Feature Engineering** | Derives lecture completion status, time gap, and binary quiz outcome |
| **3. Dataset Creation** | Reshapes data into pyBKT format: `student_id`, `skill_name`, `correct`, `time_gap` |
| **4. BKT Model Layer** | Fits `p(Know₀)`, `p(Learn)`, `p(Guess)`, `p(Slip)` using pyBKT |
| **5. Output** | Predicted knowledge states across quiz attempts |

### 3.2 Data Collection

This project uses data from Coursera activity logs including lecture metadata, student IDs, timestamps, and quiz grades. The dataset enables tracking of individual learning paths and evaluating instructional effectiveness across diverse student populations.

Key source files used:

| File | Description |
|------|-------------|
| `users.csv` | Unique student identifiers |
| `lecture_contents.csv` | Structure and mapping of lectures within the course |
| `course_lessons.csv` | Sequence of lectures and corresponding quizzes |
| `course_item_grades.csv` | Quiz identifiers and assessments |
| `course_progress.csv` | Timestamps of student activity and quiz performance |

### 3.3 Data Cleaning and Preprocessing

The following steps were applied to prepare the dataset:

1. Identified all datasets needed for BKT: student IDs, module lists, lesson sequences, item timestamps, and grade records
2. Filtered items to retain only **lecture-related quizzes**
3. Matched each quiz to its corresponding lecture per student
4. Created a **time gap** column (lecture timestamp → quiz timestamp)
5. Treated **negative time gaps** (quiz taken before lecture) as lecture not completed
6. Removed time gaps **> 90 days** as noise
7. Converted quiz grades to **binary outcomes**: Correct (1) / Incorrect (0)

**Correctness formula:**

```
ratio = course_quiz_grade / course_quiz_max_grade

Correct  (1) → ratio ≥ 0.9
Incorrect (0) → otherwise
```

**Preprocessing rules applied:**

| Rule | Detail |
|------|--------|
| Quiz correctness threshold | Score ≥ 90% of max → `1` (Correct), otherwise → `0` (Incorrect) |
| Negative time gaps | Treated as lecture not completed |
| Large time gaps | Gaps > 90 days removed as noise |
| Time gap bins | `(0–30]` `(30–60]` `(60–120]` `(120–180]` `(180–240]` minutes |

**Final dataset columns:**

| Column | Type | Description |
|--------|------|-------------|
| `Student ID` | String | Anonymized unique student identifier |
| `Lecture ID` | String | Unique identifier for each lecture |
| `Lecture Completed` | Yes / No | Whether the lecture was completed before the quiz |
| `Lecture Time` | Timestamp | Date and time of lecture completion |
| `Quiz ID` | String | Unique identifier for each quiz (used as skill name) |
| `Quiz Correct (1)/Incorrect (0)` | Binary | Quiz outcome: 1 = correct, 0 = incorrect |
| `Quiz Time` | Timestamp | Date and time of quiz attempt |
| `Time Gap (mins)` | Integer | Minutes elapsed between lecture and quiz |

### 3.4 Experiment and Data Analysis

The experiment was conducted on a dataset of over **6,000 lecture–quiz records** using Python in a Jupyter Notebook environment.

**Two BKT models were developed:**

| Model | Input Features |
|-------|----------------|
| 📘 **Lecture-Quiz Model** | Quiz outcome + lecture completion status + time gap |
| 📋 **Quiz-Only Model** | Quiz outcome only (baseline) |

Both models were implemented using **pyBKT** with `seed=42` and `num_fits=1`, estimating four key parameters:

| Parameter | Description |
|-----------|-------------|
| `p(Know₀)` | Initial probability that a student already knows the skill |
| `p(Learn)` | Probability of transitioning from unknown → known after practice |
| `p(Slip)` | Probability of answering incorrectly despite knowing |
| `p(Guess)` | Probability of answering correctly without knowing |

**Evaluation metrics:**

| Metric | Description |
|--------|-------------|
| **AUC** | Measures the model's ability to distinguish correct from incorrect outcomes — higher is better |
| **Log-Loss** | Quantifies prediction confidence — lower is better |

---

## 4. Results

### RQ1 — Effect of Lecture Completion on p(Know₀)

<!-- Add your RQ1 bar chart here -->
<p align="center">
  <img src="images/rq1_initial_knowledge.png" alt="RQ1 - Initial Knowledge States" width="700"/>
  <br/>
  <em>Figure 1 — Initial Knowledge States p(Know₀) by Lecture Completion across Quiz Topics</em>
</p>

**Quiz ID to Skill Name Mapping:**

| Quiz ID | Skill Name / Topic |
|---------|--------------------|
| `CjbTn` | The Role of Social Work |
| `Etc8T` | The Cost of Child Care |
| `pjoH6` | Key Concept Quiz |
| `qKBkT` | Identify Examples of Health Disparities |
| `sCXTz` | Into America: Dirty Air & COVID-19 Vulnerability |
| `U1Uhm` | Aging Onto The Street |
| `uhKwf` | Unpacking Intersectionality |
| `XCbMm` | The Moral Determinants of Health |
| `YOTjX` | Case Study: George Floyd Protests |

**Findings:**
- Initial knowledge states varied significantly across quiz topics, indicating differences in learners' prior knowledge
- `pjoH6` *(Key Concept Quiz)* — highest p(Know₀) **> 0.9** → effective understanding of lecture material
- `U1Uhm` *(Aging Onto The Street)* — lowest p(Know₀) **< 0.2** → learners likely skipped or partially completed the lecture
- Confirms that **lecture engagement results in stronger foundational knowledge**

---

### RQ2 — Effect of Time Gap on p(Learn)

<!-- Add your RQ2 line graph here -->
<p align="center">
  <img src="images/rq2_learning_rate.png" alt="RQ2 - Learning Rate by Time Interval" width="700"/>
  <br/>
  <em>Figure 2 — Learning Rate p(Learn) across Time Intervals Between Lecture and Quiz</em>
</p>

Students were grouped by the delay between lecture completion and quiz attempt using intervals: `(0–30]`, `(30–60]`, `(60–120]`, `(120–180]`, `(180–240]` minutes.

**Findings:**
- A clear positive trend emerged — **longer time intervals correlate with higher learning rates**
- Learners who waited **> 60 minutes** showed higher learning rates; `p(Learn)` peaked at **1.0** in the 60–120 minute interval
- Learners who took the quiz **within 60 minutes** showed noticeably lower learning rates, indicating reduced content retention or rushed attempts

---

### RQ3 — Predictive Accuracy: Lecture-Quiz vs. Quiz-Only

<!-- Add your RQ3 comparison chart here -->
<p align="center">
  <img src="images/rq3_model_comparison.png" alt="RQ3 - Model Comparison" width="700"/>
  <br/>
  <em>Figure 3 — Comparison of Predictive Accuracy: Lecture-Quiz Model vs. Quiz-Only Model</em>
</p>

| Metric | Quiz-Only Model | Lecture-Quiz Model | Improvement |
|--------|:--------------:|:-----------------:|:-----------:|
| **AUC** ↑ | 0.9370 | **0.9640** | +2.7% |
| **Log-Loss** ↓ | 0.0272 | **0.0156** | −42.6% |

**Findings:**
- The Lecture-Quiz model outperformed the Quiz-Only model across **all evaluation metrics**
- Lower Log-Loss (`0.0156` vs `0.0272`) confirms better prediction confidence and model fit
- Higher AUC (`0.9640` vs `0.9370`) confirms better discrimination between correct and incorrect predictions
- Adding lecture engagement data **significantly improves BKT model accuracy**

---

## 5. Discussion

This study exposes the various learning behaviors that directly contribute to a learner's knowledge state. Using BKT, we analyzed the impact of lecture completion, time spent on instructional content, and quiz timing on learning progression and prediction accuracy.

- **RQ1** — Learners who completed lectures before quizzes revealed higher initial knowledge states, confirming that full engagement with instructional content builds a strong foundation
- **RQ2** — Higher learning rates were observed in learners who spent more time reviewing lectures before quizzes, supporting the view that reflection time improves knowledge retention
- **RQ3** — The Lecture-Quiz BKT model outperformed the Quiz-Only model, providing a more comprehensive and credible perspective on learners' knowledge progression

**Implications for MOOC Design:**

1. Platforms could **encourage or require** learners to complete lectures before accessing related quizzes
2. Allowing a **delay between lecture completion and quiz attempt** may aid knowledge retention
3. Combining lecture engagement and quiz data enables **personalized support** — targeted feedback, suggested lecture replays, or adaptive quiz scheduling

---

## 6. Limitations & Future Work

### Limitations

| Limitation | Description |
|------------|-------------|
| Binary outcomes | Quiz results binarized (correct/incorrect) — partial knowledge cannot be captured |
| Skill proxies | Quiz IDs used as skill proxies may represent overlapping concepts |
| Uniform parameters | BKT parameters held constant across all learners — no individualization |
| Narrow behavioral signals | Limited to lecture completion and quiz outcomes; video replays, rewind actions, and forum activity excluded |
| Single platform | Results derived from one MOOC platform — generalizability untested |

### Future Work

- [ ] Adopt **refined models** accommodating partial correctness and Q-matrix skill mapping
- [ ] Incorporate **richer behavioral features** — task duration, media interaction patterns, forum engagement
- [ ] Explore **Deep Knowledge Tracing (DKT)** and **Relation-Aware Knowledge Tracing (RKT)**
- [ ] Extend the framework to **K–12 education** and **corporate training** environments
- [ ] Evaluate generalizability across **multiple MOOC platforms and subject domains**

---

## 🙏 Acknowledgments

Special thanks to **Fengjiao Tu** for valuable assistance with Research Question 3.

---

## 📚 References

1. Badrinath, A., Wang, F., & Pardos, Z. (2021). pyBKT: An accessible Python library of Bayesian knowledge tracing models. *arXiv preprint arXiv:2105.00385*
2. Baker, R. S., Corbett, A. T., & Wagner, A. Z. (2021). Optimizing Bayesian Knowledge Tracing with neural network methods. *Journal of Educational Data Mining, 13*(1), 1–17
3. Ben David, Y., Segal, A., & Gal, Y. (2016). Sequencing in classrooms using Bayesian knowledge tracing. *LAK '16*, 350–354
4. Carlon, M. K., & Cross, J. S. (2022). Knowledge tracing for adaptive learning in a metacognitive tutor. *Open Education Studies, 4*(1), 206–224
5. Dai, M., et al. (2021). Knowledge tracing: A review of available techniques. *Journal of Educational Technology Development and Exchange, 14*(2), 1–20
6. Guo, P. J., Kim, J., & Rubin, R. (2014). How video production affects student engagement. *L@S '14*, 41–50
7. Hidayah, I., & Am, E. H. (2023). Tracing knowledge states through student assessment in a blended learning environment. *Jurnal Teknik Elektro, 15*(2), 46–57
8. Kose, & Wei-Kocsis. (2025). Diffusion model for artificial learning records in knowledge tracing
9. Liu, F., et al. (2021). Fuzzy Bayesian knowledge tracing. *IEEE Transactions on Fuzzy Systems, 30*(7), 2412–2425
10. Ma, F., et al. (2025). Enhanced learning behaviors and ability knowledge tracing. *Applied Sciences, 15*(2), 883
11. Pandey, S., & Srivastava, J. (2020). RKT: Relation-aware self-attention for knowledge tracing. *arXiv:2008.12736*
12. Pardos, Z. A., & Heffernan, N. T. (2021). Twenty-five years of Bayesian knowledge tracing: A systematic review. *User Modeling and User-Adapted Interaction, 31*(1), 1–49
13. Rogers & Feng. (2024). Fairness-aware methods in Bayesian Knowledge Tracing
14. Shen, S., et al. (2024). Survey of Knowledge Tracing: Models, variants, and applications. *IEEE Transactions on Learning Technologies, 17*, 1858–1879
15. Spaulding, S., & Breazeal, C. (2015). Affect and inference in Bayesian Knowledge Tracing with a robot tutor. *HRI'15*, 219–220
16. Sridhara, A., et al. (2023). Leveraging inference: A regression-based learner performance prediction system. *IEEE Access, 11*, 123458–123475
17. Van de Sande, B. (2016). Properties of the Bayesian Knowledge Tracing model. *IJAIED, 26*(3), 720–740
18. Xu, B., et al. (2023). Learning behavior-oriented knowledge tracing. *ACM SIGKDD*, 2789–2800
19. Xu, Z., & Huang, X. (2023). Multi-modal Bayesian Knowledge Tracing for personalized learning. *Computers & Education, 186*, 104523
20. Zhang, J., et al. (2024). Bayesian analysis in cognitive-aware key-value memory networks. *Expert Systems with Applications, 257*, 124933

---

<div align="center">
  <sub>INFO 5731 — University of North Texas, Spring 2025</sub>
</div>
