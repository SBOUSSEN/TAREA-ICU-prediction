ICU Mortality Prediction Model-TAREA 

Status: This repository is based on work submitted to "Computer in Biology and Medicine" and is currently under review.
Note: Our method is in development and is planned to evolve for enhanced user-friendliness.
Overview
We've developed a machine learning model to predict mortality outcomes in ICU patients using a curated set of predictors.


Predictors:
•	Age
•	Worst Glasgow Coma Scale (GCS): Recorded in the first 24 hours.
•	Heart Rate Complexity: Requires at least 5 points per minute and is measured by:
o	NPeaks
o	Higushi Fractal Dimension
o	High-frequency content of the Heart Rate
•	Blood Pressure Metrics:
o	Time spent between 70 and 90 mmHg of Systolic Blood Pressure.
o	Time spent under 50 mmHg of Diastolic Blood Pressure.
o	Time spent under 65 mmHg of Mean Blood Pressure.
Additional parameters include Age, GCS of the first 24 hours, SAPS2 score, and the length of stay (LOS).



Repository Contents:
•	TREATEMENT.m: Computes features extracted from the Heart rate curve and Systolic, Diastolic, and Mean Blood Pressure.
•	PATIENT1.mat & PATIENT2.mat: Sample data from two patients. Data structure includes:
o	Data.FC: Heart rate
o	Data.Pas: Systolic Blood Pressure
o	Data.Pad: Diastolic Blood Pressure
o	Data.Pam: Mean Blood Pressure
o	Data.Date: Date in the format YYYYMMDDHHmmss


Other recordings are present but not utilized in this method.
The output of TREATEMENT.m provides features computed every 24 hours. Outputs include:
•	PATIENT1RESULTS.mat: MATLAB file.
•	PATIENT1RESULTS.csv: CSV file without headers.
The CSV output is used by an R script TAREA_PROB.R to compute the probability of death. This script leverages a .data file containing the model (TAREA_BOOST) and a recalibration model (PLATT_REC) trained on the training data.
The script outputs:
•	Predicted probability of death and the forecasted outcome.
•	SAPS 2 computed probability of death and the forecasted outcome.
•	True outcome.



Progress:
This project is ongoing, and we aim to consolidate the process into a single file soon.



Disclaimer:
This is a research tool and is not intended for clinical use.
