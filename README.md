# Parsing Human-Entered Spreadsheet Marks into Analytics Datasets

## Description

This project was developed to display information about dental health plans. In a Google Sheets file, an administrator fills in the areas, procedures, and prices, and then marks with an "X" which plans do not cover each procedure. After that, an Apps Script reorganizes this information into a new sheet so it can be read, displayed, and filtered in Looker Studio.

---
### Input model

| Field       | Procedure   | Cost        | Plan 1      | Plan 2      | Plan 3      | Plan 4      |     ...     | Plan N      |
|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|
| Field 1     | Procedure 1 |‎ Value       |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |
|             | Procedure 2 |‎ Value       |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |
|             | Procedure 3 |‎ Value       |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |
| Field 2     | Procedure 4 |‎ Value       |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |
|             | Procedure 5 |‎ Value       |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |             |             |             |
|             | Procedure 6 |‎ Value       |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |
|             | Procedure 7 |‎ Value       |             |             |‎             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |‎             |
| Field 3     | Procedure 8 |‎‎ Value       |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |
|             | Procedure 9 |‎ Value       |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             |             |             |             |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |
|     ...     |     ...     |     ...     |     ...     |     ...     |     ...     |     ...     |     ...     |     ...     |
| Field N     | Procedure N |‎ Value       |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |‎ ‎ ‎ ‎ X‎ ‎ ‎ ‎     |             | ‎ ‎ ‎ X‎ ‎ ‎ ‎     |

### Database model

| Field       | Procedure   | Cost        | Plan        |
|-------------|-------------|-------------|-------------|
| Field 1     | Procedure 1 |‎ Value       | Plan 1      |
| Field 2     | Procedure 4 |‎ Value       | Plan 1      |
| Field 2     | Procedure 5 |‎ Value       | Plan 1      |
| Field 3     | Procedure 8 |‎ Value       | Plan 1      |
| Field 3     | Procedure 9 |‎ Value       | Plan 1      |
| Field 2     | Procedure 6 |‎ Value       | Plan 2      |
| Field 3     | Procedure 8 |‎‎ Value       | Plan 2      |
| Field 1     | Procedure 2 |‎‎ Value       | Plan 3      |
| Field 1     | Procedure 3 |‎ Value       | Plan 3      |
| Field 2     | Procedure 6 |‎ Value       | Plan 3      |
| Field 3     | Procedure 8 |‎ Value       | Plan 3      |
|     ...     |     ...     |     ...     |     ...     |
| Field N     | Procedure N |‎ Value       | Plan N      |

### Looker Studio Visualization
![Tratamentos_Particulares_-_Amil_Dental](https://github.com/user-attachments/assets/af54c242-cbd7-4a54-b98b-01c85143026a)
