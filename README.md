##  Key Findings

Analysis of **500 patient records** (after removing 15 duplicates) from the Safira Hospital dataset, covering 5 hospitals, 6 departments, and 8 diagnoses.

- **Cardiology** is the busiest department (98 patients), followed closely by **Emergency** (93) and **Orthopedics** (91).
- **Pediatrics** has the longest average length of stay at **17.5 days**, despite having the fewest patients (68) — worth investigating further.
- **St. Mary's Clinic** bills the highest on average per patient (**$4,381**) and also has the highest total billing (**$459,964**) across the 5 hospitals.
- **Migraine** and **Malaria** are tied as the most common diagnoses (61 cases each), followed by Anemia (60).
- **Fracture**, **Hypertension**, and **Appendicitis** are the most expensive diagnoses on average, each billing over $4,300 per case.
- Patients are split almost evenly by gender (**50.4% male / 49.6% female**) and admission type (Elective 36%, Outpatient 33%, Emergency 30%).
- Of the 500 patients, **128 (25.6%) died**, with an average age of 38.8 — younger than the overall patient average — and Typhoid/Malaria were the most common diagnoses among them.
- **Dr. Agyei** treated the most patients (73), ahead of Dr. Boateng (61) and Dr. Mensah (60).

##  Visualizations

### Patient Count by Age Group

<img width="1184" height="657" alt="image" src="https://github.com/user-attachments/assets/64953d54-02dc-4fbf-b221-d849675bd947" />


Adults (136) and Seniors (116) make up the largest share of patients, together accounting for over half the dataset. Children (98) and Young Adults (85) are notably fewer, and Elderly patients (65) are the smallest group. This suggests the hospital network's caseload skews toward middle-aged and older patients rather than pediatric or young-adult care.

### Age Distribution

<img width="1184" height="657" alt="image" src="https://github.com/user-attachments/assets/d138950d-3682-4190-9189-17588ce54611" />

[Age distribution histogram](charts/02_age_distribution.png)

The histogram is fairly flat across the 20–80 range rather than peaking sharply at one age — there's no single dominant age band, just a broad spread with slightly heavier density in the 30s–60s. This is consistent with a general hospital network treating a wide cross-section of the population rather than a specialized clinic.

### Average Billing by Department

<img width="1184" height="657" alt="image" src="https://github.com/user-attachments/assets/c246b560-37ae-409e-a71d-2c8fb18c0342" />

[Average billing by department](charts/03_avg_billing_by_department.png)

Department-level average billing is fairly close together (roughly $3,900–$4,400), with no department standing out as dramatically more expensive. This implies billing amounts are likely driven more by individual diagnosis or treatment complexity than by which department a patient is admitted to — worth cross-checking against diagnosis-level billing, where Fracture, Hypertension, and Appendicitis stood out.

### Patient Status Breakdown

<img width="851" height="884" alt="image" src="https://github.com/user-attachments/assets/e6bac667-4936-4e79-856e-5f4677515be4" />

[Patient status pie chart](charts/04_patient_status_pie.png)

Patients are spread across four outcomes — Discharged (27%), Deceased (25.6%), Admitted (25.4%), Transferred (22%) — in roughly even quarters. The 25.6% mortality rate is unusually high for a general hospital dataset (real-world inpatient mortality is typically low single digits), which suggests this is either a synthetic/practice dataset or "Deceased" here captures a specific high-risk subset. Worth calling out explicitly rather than treating as a real-world clinical rate.

### Length of Stay by Department

<img width="1184" height="657" alt="image" src="https://github.com/user-attachments/assets/f7388547-8960-4fe3-bc80-dcae25cc97bb" />

[Length of stay boxplot](charts/05_length_of_stay_boxplot.png)

Pediatrics has the highest median and average stay despite having the fewest patients, while the other five departments cluster closer together. The spread (box height) looks similar across departments, meaning no department has wildly inconsistent stay durations — Pediatrics is just consistently longer, not pulled up by outliers. Worth a follow-up: is it driven by diagnosis severity, age-related caution, or how pediatric cases are tracked?

##  Conclusion

This analysis of 500 hospital patient records (after removing 15 duplicates) shows a patient population that is broadly representative in age and gender, but with a few standout patterns: Cardiology and Emergency carry the heaviest patient volume, Pediatrics cases run longer than any other department despite low volume, and billing is more strongly tied to diagnosis type than to department. The most notable — and most concerning if this were real clinical data — finding is the 25.6% deceased rate, which is far above typical hospital mortality and should be flagged as either a data-quality artifact or a deliberate characteristic of this dataset rather than presented as a real-world statistic. Overall, the dataset is clean enough for exploratory analysis but would benefit from clarifying what "Deceased" actually represents before drawing any real clinical conclusions from it.

---
*Tools used: Python, pandas, matplotlib, seaborn (Jupyter Notebook)*
