Warranty Fraud Detection
Project Overview
This project is a comprehensive fraud detection system for warranty claims. It uses a hybrid approach that combines rule-based logic with an Isolation Forest machine learning model to identify suspicious and potentially fraudulent claims. The system processes multiple datasets—claims, dealer, vehicle, and service history—to build a robust set of features for analysis. It generates detailed reports, visualizations, and a final list of suspicious claims, providing a clear and actionable output for business stakeholders.

Key Features
Data Integration: Merges claims data with dealer, vehicle, and service history records for a holistic view.

Rule-Based Detection: Flags claims based on predefined business rules, such as invalid dates, high mileage, suspicious quantities, and data inconsistencies.

Anomaly Detection: Utilizes the Isolation Forest algorithm to detect irregular patterns that might not be caught by static rules.

Performance Evaluation: Provides a classification report and a confusion matrix to evaluate the model's effectiveness in identifying fraudulent claims.

Automated Reporting: Generates visual reports (bar charts, pie charts, scatter plots) and saves final outputs as CSV and Excel files for easy sharing and analysis.

Getting Started
Prerequisites
Make sure you have Python installed. You can install the necessary libraries using pip.

Bash

pip install pandas scikit-learn matplotlib seaborn
File Structure
Ensure your project directory is structured as follows:

.
├── fraud_warranty_detection/
│   └── new_file_detector.py      # Main script for fraud detection
├── claims.csv
├── dealer_master.csv
├── service_history.csv
├── vehicle_master.csv
└── fraudulent_claims_full_details.csv
How to Run the Script
To run the analysis, execute the new_file_detector.py script from your terminal.

Bash

python fraud_warranty_detection/new_file_detector.py
The script will process the data and save the outputs to the specified directories.

Output
The script generates a output directory containing two subdirectories:

output/csv/: Contains CSV files with the raw data and flagged claims.

all_claims_with_flags.csv: The complete dataset with all a-dded flags and scores.

false_claims_list.csv: A filtered list of all claims identified as suspicious or fraudulent.

output/excle/: Contains an Excel file with the final list of fraudulent claims.

false_claims_list.xlsx: An Excel version of the list for easy viewing.

output/visual_output/: Contains image files of the generated charts and plots.

claim_cost_comparison_bar.png

suspicious_vs_non_suspicious_pie.png

combined_donut_charts.png

confusion_matrix.png

claim_cost_vs_km_failure_scatter_comparison.png

Project Logic
Data Preprocessing
The detect_fraudulent_claims function first reads all CSV files. It then performs data cleaning and feature engineering, including:

Dropping duplicate entries.

Converting relevant columns to the correct data types.

Calculating vehicle_age from purchase dates.

Detection Rules
Several flags are created based on predefined business rules, such as:

invalid_claim_no: Checks for missing or empty claim numbers.

invalid_vehicle_age: Flags claims for vehicles older than 20 years.

invalid_distance: Identifies claims with unusually high mileage (> 350,000 km).

suspicious_chassis_match: Detects if a single chassis number is associated with multiple vehicle types or models.

Anomaly Detection
The Isolation Forest model is trained on a selection of key numerical and boolean features. This model works by isolating anomalies as "outliers," which helps identify claims with unusual combinations of characteristics that may not be covered by the manual rules.

Final Output
The final list of fraudulent claims is determined by combining the flags from both the rule-based system and the Isolation Forest model. A detailed Reason_for_False_Claim column is generated to provide a clear explanation for why each claim was flagged.

Contributing
Feel free to open an issue or submit a pull request if you find any bugs or have suggestions for improvements.

License
This project is licensed under the MIT License.
