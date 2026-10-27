# Healthcare Data Governance and Cleaning

## Project goal
Prepare a small healthcare training CSV responsibly using documented, repeatable data-quality checks.

## Files
- `healthcare_patients_cleaned.csv` — cleaned sample (conservative text formatting only; no clinical values imputed).
- `data_dictionary.csv` — field definitions, sensitivity, privacy risks, and validation rules.
- `exception_log.csv` — row/field-level validation findings and actions.
- `healthcare_data_governance_cleaning.ipynb` — reproducible notebook to rerun checks.
- `healthcare_patients_sample.csv` — original supplied sample, included so the notebook runs in the same folder.

## Privacy statement
The task describes the data as synthetic/de-identified. The file itself cannot prove that claim. `PatientID` appears pseudonymous (for example, PAT-201), but pseudonymization is not the same as anonymization. Keep the data restricted to the intended training purpose and do not add direct identifiers or try to re-identify anyone.

## Cleaning and validation policy
1. Trim leading/trailing whitespace from text.
2. Standardize capitalization for selected categorical fields; normalize Yes/No.
3. Validate ID presence/uniqueness, missing values, selected numeric ranges, categorical vocabularies, and blood-pressure format.
4. Flag questionable data in the exception log rather than silently deleting records or making clinical corrections.
5. Preserve missing clinical values; never guess diagnoses, medication, dosage, readmission, blood pressure, or cholesterol values.

## Important limitations
- Small sample size limits conclusions.
- Dosage and cholesterol units/ranges need confirmation from the data owner.
- The broad technical checks are not clinical decision rules.
- A valid-looking blood-pressure string is not proof that the measurement is clinically plausible.
- Review flagged rows with an authorized data owner before any operational use.

## Run locally
Install Python 3, pandas, numpy, and Jupyter. Put `healthcare_patients_sample.csv` next to the notebook, then run all notebook cells. Outputs are written to `outputs/`.
