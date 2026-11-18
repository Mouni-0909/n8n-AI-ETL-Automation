# AI-Powered ETL Automation Using n8n

## Project Overview

This project demonstrates an AI-powered ETL (Extract, Transform, Load) automation workflow built using n8n, OpenAI, Google Drive, and JavaScript.

The workflow automatically downloads student enrollment data from Google Drive, extracts CSV records, cleans and standardizes the data using OpenAI, and uploads the cleaned CSV file back to Google Drive.

## Technologies Used

- **n8n** – Workflow automation platform
- **OpenAI (GPT-5 Mini)** – AI-powered data cleaning
- **Google Drive** – Input and output file storage
- **JavaScript** – Processing and transforming JSON data
- **CSV and JSON** – Data formats used for processing

## Workflow Architecture

The workflow consists of seven main steps:

1. **Manual Trigger:** Starts the workflow when the Execute Workflow button is clicked.
2. **Google Drive – Download File:** Downloads the raw student enrollment CSV file from Google Drive.
3. **Extract from File:** Extracts 50 student records from the CSV file.
4. **Basic LLM Chain:** Uses the OpenAI GPT-5 Mini model to clean and standardize student information.
5. **JavaScript Code:** Converts the AI-generated JSON array into individual student records.
6. **Convert to File:** Converts the cleaned records into a CSV file.
7. **Google Drive – Upload File:** Uploads the cleaned CSV file to the Student_ETL folder in Google Drive.

## Data Cleaning Operations

The OpenAI model is instructed to perform the following cleaning operations:

- Remove duplicate records based on Student_ID.
- Remove unnecessary spaces from text fields.
- Convert student names and city names to title case.
- Convert email addresses to lowercase.
- Keep missing or invalid email addresses and phone numbers empty.
- Avoid generating missing information.
- Preserve the original student data fields.
- Return the cleaned records in JSON format.

## Dataset

The input dataset contains 50 student enrollment records with the following fields:

| Field | Description |
|---|---|
| Student_ID | Unique student identifier |
| Name | Student name |
| Email | Student email address |
| Phone | Contact number |
| Course | Enrolled course |
| Fee_Paid | Fee payment status |
| City | Student city |
| Enrolled_Date | Enrollment date |

**Input File:** `student_enrollment_raw.csv`

**Output File:** `student_enrollment_cleaned.csv`

## How to Run the Workflow

1. Install or access an n8n instance.
2. Import the `student_etl_workflow.json` file into n8n.
3. Configure Google Drive OAuth credentials.
4. Configure OpenAI API credentials.
5. Select the input CSV file from Google Drive.
6. Configure the destination folder for the cleaned CSV file.
7. Click **Execute Workflow**.
8. Verify that all workflow nodes execute successfully.
9. Check Google Drive for the generated cleaned CSV file.

## JavaScript Transformation

The following JavaScript code converts the AI-generated JSON output into individual records for CSV generation.

```javascript
const aiOutput = $input.first().json.text;

const students = JSON.parse(aiOutput);

return students.map(student => ({ json: student }));
```

## Execution Results

- Successfully connected n8n with Google Drive and OpenAI.
- Extracted 50 student enrollment records from the input CSV.
- Executed AI-based data cleaning and standardization.
- Converted the AI-generated JSON into structured student records.
- Generated a cleaned CSV file.
- Successfully uploaded the output file to Google Drive.
- Verified successful execution of the complete workflow.

## Key Learnings

Through this assignment, I learned:

- How to build an end-to-end ETL pipeline using n8n.
- How to integrate OpenAI models into automation workflows.
- How to connect Google Drive using OAuth authentication.
- How to extract and process CSV data.
- How to use AI prompts for data cleaning and standardization.
- How to transform JSON data using JavaScript.
- How to automate file generation and uploading.
- How to test and debug individual n8n workflow nodes.

## Conclusion

This project helped me gain practical experience in building an AI-powered ETL automation pipeline using n8n.

By integrating OpenAI, JavaScript, and Google Drive, I was able to automate student enrollment data extraction, cleaning, transformation, and file uploading.

The assignment provided hands-on experience with workflow automation, AI integration, data processing, and debugging.

It also helped me understand how AI-powered automation can reduce manual effort in real-world data processing tasks.
