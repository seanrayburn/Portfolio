# i-Connect Payroll Extract User Guide

# Table of Contents

[1\. Revision history](#revision-history)

[2\. Purpose of this guide](#purpose-of-this-guide)

[2.1. Further reading](#further-reading)

[3\. Preparation](#preparation)

[3.1. Record matching](#record-matching)

[3.2. Unique payroll identifier](#unique-payroll-identifier)

[4\. Extract file creation preparation](#extract-file-creation-preparation)

[4.1. File format](#file-format)

[4.2. Header row](#header-row)

[4.3. Duplicate records](#duplicate-records)

[4.4. Other payroll extract file considerations](#other-payroll-extract-file-considerations)

[5\. Uploading data](#uploading-data)

[5.1. Preparing to upload data](#preparing-to-upload-data)

[5.2. Preparing to upload data](#preparing-to-upload-data-1)

[6\. i-Connect payroll extract file specification](#i-connect-payroll-extract-file-specification)

[7\. Example payroll extract file](#example-payroll-extract-file)

[8\. Frequently asked questions (FAQs)](#frequently-asked-questions-\(faqs\))

[9\. About this version](#about-this-version)

[10\. Need more help?](#need-more-help-?)

# 

# Revision history

| Version | Date | Updated By | Approved By | Details |
| :---- | :---- | :---- | :---- | :---- |
| 2.00 | 30/11/2016 | J Dale | C Lewis  | Updated for GAD and DCLG reporting requirements for LGPS pension fund transactions for cashflows from 1 April 2017 onwards.  |
| 2.10 | 05/10/2017 | J Dale | C Lewis | Member address changed to Mandatory to align with the Pensions Regulator Codes of Practice. |
| 2.20 | 08/11/2017 | J Dale  | C Lewis | Data Item 37 renamed Auto-Enrollment Qualifying Earnings. Example files replaced.  |
| 3.00 | 07/06/2018 | K Pridgeon | J Dale/E Fisher | Rebrand. |
| 3.10 | 01/08/2018 | C Lewis | C Lewis | Description of Data Item 48 corrected.  |
| 3.20  | 02/11/2018 | J Dale | C Lewis | Telephone number changed. |
| 3.30 | 29/04/2018 | J Dale | C Lewis | Suspension renamed to Employment Break and reason codes added. Auto-Enrollment Qualifying Earnings Retired. Service examples added to FAQs. Part-Time Hours Effective Dates notes amended.  “What’s Changed” section added.  |
| 3.40 | 12/07/2019 | J Dale | C Lewis | Suspension Reason renamed Employment Breal Reason. Notes updated.  |
| 3.50 | 19/12/2019 | J Dale | P Stocks | Data Item 48 (Employer's Contribution) maximum number of characters corrected.  |
| 3.60 | 12/03/2021 | C Lewis | J Dale | Clarification on part-time hours for term-time employees.  |
| 3.70 | 19/01/2023 | C Lewis | J Dale | Data Item 37 changed to Auto- Enrollment Qualifying Earnings. |
| 3.80 | 07/12/2024 | C Lewis | Unknown | Clarification on part-time hours effective date.  |
| 3.90 | 12/02/2026 | S Rayburn |  | Accessibility and formatting issues addressed. |


# Purpose of this guide

This guide provides a comprehensive understanding of the i-Connect payroll extract file specification, including each of the data items that must be submitted to your administering authority every pay period. 

**Note:** Data items are mandatory, conditional, or optional for i-Connect data processing. Your administering authority may require that some of the conditional or optional data items provided be mandatory. 

## Further reading 

If you are an employer, refer to the [i-Connect User Guides for Employers](https://media.buckinghamshire.gov.uk/documents/i-connect-document-upload-guide.pdf) for more information about the i-Connect Service. 

1. Logon to your i-Connect portal  
2. Navigate to Reporting  
3. Onboarding  
4. Online Return  
5. File Upload

If you are an administering authority, refer to the [i-Connect User Guides for Employers](https://media.buckinghamshire.gov.uk/documents/i-connect-document-upload-guide.pdf) and the i-Connect User Guide for Administering Authorities. 

Please email [support@i-Connectdata.co.uk](mailto:support@i-Connectdata.co.uk) if you have not received copies of these guides. 

# Preparation 

## Record matching

i-Connect automatically matches each post on your payroll system to a corresponding record on your administering authority’s pensions administration system—known as ‘the target system’ in this document—when possible. 

The matching process uses employees’ National Insurance numbers and in addition to a unique payroll identifier.

## Unique payroll identifier

A unique payroll identifier must be present for each payee/post on the payroll extract file. This key can be a combination of fields held on the payroll system (e.g., payroll reference, employee reference, and post number). There are three 12-character fields available on the payroll extract file to output the unique payroll identifier:

* Payroll Reference 1 (Data Item 2\)  
* Payroll Reference 2 (Data Item 3\)  
* Payroll Reference 3 (Data Item 4\)

These three fields provide you and your administering authority with the flexibility to create a unique payroll identifier in a single field or across multiple fields.  
The examples in the table below use the following information:

* National Insurance Number: AA123123A  
* Payroll Reference: 555444  
* Post Number: 144-543

| Unique Payroll Identifier  | National Insurance Number | Payroll Reference 1 | Payroll Reference 2 | Payroll Reference 3 |
| :---- | :---- | :---- | :---- | :---- |
| Single Field | AA123123A | 555444144543 |  |  |
| Multiple Fields (2) |  | 555444 | 144-543 |  |
| Multiple Fields (3) |  | 555444 | 144 | 543 |

Each of the three payroll reference fields corresponds to a specific field on the target system. Your administering authority will provide you with their specific field-level matching requirements as part of the i-Connect implementation process. Please contact them as soon as possible if this information has not been provided.

**Note:** The selected matching method must be consistent for all records on the payroll extract file.

# Extract file creation preparation

##  File format
All payroll extract files uploaded into i-Connect must be saved as comma-separated value (CSV) files. Files not in this format will be rejected during the upload process.

Fields containing commas must be embedded within a set of double quotes (commonly referred to as ‘text qualifiers’) to maintain data integrity. For example, a data entry in Address Line 1 (Data Item 15\) containing a comma would be output as:

"Dun Roamin, Dun Campin"

##  Header row

Each payroll extract file must have a header row to describe the i-Connect data items. i-Connect assumes the first row of a file is the header; failure to include a header row results in the first record in the file being omitted from processing.

An example header row is:   
NI\_NUMBER, PAY\_REF\_1, PAY\_REF\_2, PAY\_REF\_3, ADD\_LINE\_1, ADD\_LINE\_2, ADD\_LINE\_3, ADD\_LINE\_4, ADD\_LINE\_5, POSTCODE, EMAIL\_ADDRESS, TELEPHONE\_NUMBER, MOBILE\_NUMBER, WORKS\_PLACE\_NAME, WORKS\_ADD\_LINE\_1, WORKS\_ADD\_LINE\_2, WORKS\_ADD\_LINE\_3, WORKS\_ADD\_LINE\_4, WORKS\_ADD\_LINE\_5, WORKS\_POSTCODE, WORKS\_EMAIL\_ADDRESS, DATE\_OF\_LEAVING, PAYROLL\_PERIOD\_END\_DATE, ADDITIONAL\_CONTRIBUTIONS\_1, ADDITIONAL\_CONTRIBUTIONS\_2, EMPLOYMENT\_BREAK\_START, EMPLOYMENT\_BREAK\_END, FILLER\_1, EMPLOYMENT\_BREAK\_REASON, SURNAME, FORENAMES, GENDER, DOB, MARITAL\_STATUS, TITLE, FILLER\_2, FILLER, ANNUAL\_PENSIONABLE\_SALARY, PENSIONABLE\_PAY, EFFECTIVE\_DATE, DATE\_JOINED\_PENSION\_SCHEME, JOB\_TITLE, PART\_TIME\_HOURS\_EFFECTIVE\_DATE, PART\_TIME\_HOURS, PART\_TIME\_INDICATOR, WHOLE\_TIME\_EQUIVALENT\_HOURS, EMPLOYEES\_MAIN\_SECTION\_CONTS, EMPLOYERS\_CONTS, SCHEME\_CONT\_RATE, OPT\_OUT\_DATE, OPT\_IN\_DATE, MAIN\_SECTION\_CUMULATIVE\_PEN\_PAY, 5050\_SECTION\_CUMULATIVE\_PEN\_PAY, FTE\_FINAL\_PAY, CUMULATIVE\_EMPLOYEES\_MAIN\_SECTION\_SCHEME\_CONTS, CUMULATIVE\_EMPLOYERS\_SCHEME\_CONTS, REASON\_FOR\_LEAVING, CUMULATIVE\_SCAPCs, CUMULATIVE\_APCs, EMPLOYEES\_5050\_CONTS, CUMULATIVE\_EMPLOYEES\_5050\_CONTS, SCAPCs, APCs

**Note:** The column names do not have to be identical to those shown above, but the field ordering must match the order specified in Section 4. 

##  Duplicate records

All records on the i‑Connect payroll extract file must be unique. Files with records containing duplicate National Insurance Numbers and the unique payroll identifier will be rejected. 

##  Other payroll extract file considerations

4.4.1 The order of the data items must match the order specified in the file layout.​  
4.4.2 The payroll period end date (Data Item 23\) must be the same on all records.​  
4.4.3 Blank rows must not be present in the payroll extract file.​  
4.4.4 Ensure all leading zero values remain if the file has to be converted to CSV format.​  
4.4.5 Ensure all transactions processed after the payroll cut-off date are included on the i‑Connect payroll extract file report; this must include new starters, leavers, post changes, and similar updates.​  
4.4.6 Part‑time hours must be pro‑rated for term‑time employees.​  
4.4.7 Negative values are indicated by a minus “-” character at the beginning of the data field (e.g., \-115.64).

# Uploading data

## Preparing to upload data

You must be able to answer “Yes” to the following questions before attempting to upload any data into i-Connect: 

* Is the file in the correct format?  
* Have you used the correct payroll‑period‑end date?  
* Are all the records unique?  
* Has your administering authority provided you with a username?

If you answered “No” to any questions, please refer to the i-Connect User Guide for Employers.

## Preparing to upload data

The following table provides approximate processing times for payroll extract files in i-Connect. The first stage, **File Upload/Employment Check**, checks the structure of the file, validates the data, and checks whether any payees have been deleted from the target system by the administering authority. The second stage, **Target System Update**, uploads the detected events to the administering authority’s target system.

|  Number of Records | Approximate Processing Times (minutes) |  |
| :---- | :---- | :---- |
|  | **File Upload/Unemployment Check** | **Target System Update** |
| 1,000 | 15 | 20 |
| 2,000 | 20 | 40 |
| 5,000 | 30 | 100 |
| 7,500 | 50 | 150 |
| 10,000 | 70 | 200 |
| 15,000 | 100 | 300 |
| 20,000 | 120 | 400 |

# i-Connect payroll extract file specification
| Item | Data Item |  | Description | Maximum Number of Characters | Mantatory / Optional |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **1** | NATIONAL INSURANCE NUMBER  |  | National Insurance Number of the employee. | 9 | **Mandatory** |
| Example: | AB123456C |  |  |  |  |
| Notes: | Please enter the employee’s NINo, which is used in conjunction with one or more of the payroll reference fields (Items 2-4) to identify the correct record on the administering authority’s target system. Please contact your administering authority if any of the employees do not have a NINo, as it is a mandatory field on the target system. **This data must be completed to process the data.**  |  |  |  |  |
| **2** | PAYROLL  REFERENCE 1 |  | An additional unique identifier for each post in your organisation. Generally, this is the employee’s payroll number with the current employer. | 12 | **Conditional\*** |
| Example: | 134-0547 |  |  |  |  |
| Notes: | Please enter a unique identifier to match the post to the correct target system record, such as a Payroll Reference Number. Contact your administering authority to confirm whether this unique identifier should be placed in Payroll Reference 1, Payroll Reference 2 or Payroll Reference 3\.  If this field is not used as a unique identifier, it can be used to store additional payroll identification information for new starters, such as Post or Contract Number. **\*Mandatory if the administering authority specifies this field as a unique identifier.**  |  |  |  |  |
| **3** | PAYROLL REFERENCE 2 |  | An additional unique identifier for each post in your organisation. Generally, this is the employee’s payroll number with the current employer. | 12 | **Conditional\*** |
| Example: | TY0123456 |  |  |  |  |
| Notes | Please enter a unique identifier to match the post to the correct target system record, such as a Payroll Reference Number. Contact your administering authority to confirm whether this unique identifier should be placed in Payroll Reference 1, Payroll Reference 2 or Payroll Reference 3\.  If this field is not used as a unique identifier, it can be used to store additional payroll identification information for new starters, such as Post or Contract Number. **\*Mandatory if the administering authority specifies this field as a unique identifier.** |  |  |  |  |
| **4** | PAYROLL REFERENCE 3 |  | An additional unique identifier for each post in your organisation. Generally, this is the employee’s payroll number with the current employer. | 12 | **Conditional\*** |
| Example: | 07 |  |  |  |  |
| Notes: | Please enter a unique identifier to match the post to the correct target system record, such as a Payroll Reference Number. Contact your administering authority to confirm whether this unique identifier should be placed in Payroll Reference 1, Payroll Reference 2 or Payroll Reference 3\.  If this field is not used as a unique identifier, it can be used to store additional payroll identification information for new starters, such as Post or Contract Number. **\*Mandatory if the administering authority specifies this field as a unique identifier.**  |  |  |  |  |
| **5** | ADDRESS LINE 1  |  | Address Line 1 of the correspondence address of the employee. | 30 | **Mandatory** |
| Example: | Riverview |  |  |  |  |
| Notes: | Please enter the first address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **6** | ADDRESS LINE 2  |  | Address Line 2 of the correspondence address of the employee.  | 30 | **Mandatory** |
| Example: | 23 Upper Riverbank |  |  |  |  |
| Notes: | Please enter the second address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **7** | ADDRESS LINE 3  |  | Address Line 3 of the correspondence address of the employee. | 30 | Optional |
| Example: | Hale Barns |  |  |  |  |
| Notes: | Please enter the third address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **8** | ADDRESS LINE 4  |  | Address Line 4 of the correspondence address of the employee. | 30 | Optional |
| Example: | Altrincham |  |  |  |  |
| Notes: | Please enter the fourth address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **9** | ADDRESS LINE 5  |  | Address Line 5 of the correspondence address of the employee. | 30 | Optional |
| Example: | Cheshire |  |  |  |  |
| Notes: | Please enter the fifth address line of where the employee lives. Upper- and lower-case characters are valid.  Valid characters are A – Z, hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **10** | POSTCODE |  | Postcode of the correspondence address.  | 10 | **Mandatory** |
| Example: | WA14 1TT |  |  |  |  |
| Notes: | Please enter letters A-Z, numbers 0-9, and a single space.  |  |  |  |  |
| **11** | EMAIL ADDRESS |  | Personal email address of the employee. | 72 | Optional |
| Example: | hsmith@domain.co.uk |  |  |  |  |
| Notes: | Please enter the employee’s personal email address in the format:  [niceandsimple@example.com](mailto:niceandsimple@example.com) or [very.common@example.co.uk](mailto:very.common@example.co.uk).  Confirm if your administering authority requires a personal email, as it may affect members’ access to self-service systems.  |  |  |  |  |
| **12** | TELEPHONE NUMBER |  | Personal telephone number of the employee. | 14 | Optional |
| Example: | 01234 567890 |  |  |  |  |
| Notes: | Please enter the employee’s personal landline number with numeric characters and spaces only.  |  |  |  |  |
| **13** | MOBILE NUMBER |  | Personal mobile number of the employee. | 14 | Optional |
| Example: | 07777 777777 |  |  |  |  |
| Notes: | Please enter the employee’s personal landline number with numeric characters and spaces only.  |  |  |  |  |
| **14** | WORK’S PLACE NAME |  | Address Line 1 of where the employee currently works. | 40 | Optional |
| Example: | Elmridge Primary School |  |  |  |  |
| Notes: | Please enter the name of the employee’s workplace. |  |  |  |  |
| **15** | WORK’S ADDRESS LINE 1  |  | Address Line 1 of where the employee currently works. | 30 | Optional |
| Example: | Wilton Drive |  |  |  |  |
| Notes: | Please enter the first address line of where the employee works.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **16** | WORK’S ADDRESS LINE 2  |  | Address Line 2 of where the employee currently works. | 30 | Optional |
| Example: | Hale Barns |  |  |  |  |
| Notes: | Please enter the second address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **17** | WORK’S ADDRESS LINE 3  |  | Address Line 3 of where the employee currently works. | 30 | Optional |
| Example: | Altrincham |  |  |  |  |
| Notes: | Please enter the third address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **18** | WORK’S ADDRESS LINE 4  |  | Address Line 4 of where the employee currently works. | 30 | Optional |
| Example: | Cheshire |  |  |  |  |
| Notes: | Please enter the fourth address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **19** | WORKS ADDRESS LINE 5  |  | Address Line 5 of where the employee currently works. | 30 | Optional |
| Example: | United Kingdom |  |  |  |  |
| Notes: | Please enter the fifth address line of where the employee lives.  Valid characters are A – Z (upper- and lower-case), hyphen (-), and apostrophe (').  If any of the address lines (1 to 5\) are present for the employee, a minimum of two (2) address lines must be provided. |  |  |  |  |
| **20** | WORKS POST CODE  |  | Postcode of the address where the employee works.  | 10 | Optional |
| Example: | WA15 1PS |  |  |  |  |
| Notes: | Please enter letters A-Z, numbers 0-9, and a single space.  |  |  |  |  |
| **21** | WORKS EMAIL ADDRESS  |  | Work email address of the employee. | 72 | Optional |
| Example: | hsmith@domain.co.uk |  |  |  |  |
| Notes: | Please enter the employee’s work email address in the format: [niceandsimple@example.com](mailto:niceandsimple@example.com) or [very.common@example.co.uk](mailto:very.common@example.co.uk).  |  |  |  |  |
| **22** | DATE OF LEAVING  |  | Date the employee left this post. | 10 | **Conditional\*** |
| Example: | 31/05/2015 |  |  |  |  |
| Notes: | Please enter date format **DD/MM/YYYY**. **\*Mandatory for leavers.** |  |  |  |  |
| **23** | PAYROLL PERIOD END DATE  |  | End date of the earnings period that the pay relates to.  | 10 | **Mandatory** |
| Example: | 30/06/2015 |  |  |  |  |
| Notes: | Please enter date format **DD/MM/YYYY**. The same date must be present for each record on the file; mixed payroll period end dates are not acceptable.  **Note on non-monthly payrolls:** please note that the payroll period end date is used to determine the scheme year to which the financial information is written back on the target system. The pay date should be used instead of the Payroll l Period End Date if the payroll is paid in advance or arrears. **This data item must be completed.**  |  |  |  |  |
| **24** | ADDITIONAL CONTRIBUTIONS 1 |  | Additional regular contributions that the employee is paying. | 10 | Optional |
| Example: | 10.01 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the total of the cumulative contributions to date for any additional voluntary contributions the employee is paying.  Enter only numbers (0-9) and decimal points (.).  **Leave blank or populate with zero values if the value is null.** |  |  |  |  |
| **25** | ADDITIONAL CONTRIBUTIONS 2  |  | Additional regular contributions that the employee is paying. | 10 | Optional |
| Example: | 15.99 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the total of the cumulative contributions to date for any additional voluntary contributions the employee is paying.  Enter only numbers (0-9) and decimal points (.).  **Leave blank or populate with zero values if the value is null.** |  |  |  |  |
| **26** | EMPLOYMENT BREAK START DATE |  | The start date of any unpaid employment breaks for the employee.  | 10 | Optional |
| Example: | 17/06/2015 |  |  |  |  |
| Notes:  | Please enter the start date of commencement of any **unpaid** employment break (e.g., strike, maternity, or paternity).  Please enter the date format **DD/MM/YYYY**.  |  |  |  |  |
| **27** | EMPLOYMENT BREAK END DATE |  | The end date of any unpaid employment breaks for the employee.  | 10 | Optional |
| Example: | 18/16/2015 |  |  |  |  |
| Notes:  | Please enter the end date of termination of any **unpaid** employment break (e.g., strike, maternity, or paternity).  Please enter the date format **DD/MM/YYYY**.  The end date can be left blank until known. |  |  |  |  |
| **28** | FILLER |  | A spare field for future use.  | 10 | N/A |
| Example: | N/A |  |  |  |  |
| Notes | Leave blank or zero fill.  |  |  |  |  |
| **29** | EMPLOYMENT BREAK REASON |  | The reason for the employment break.  | 1 | Optional |
| Example: | M |  |  |  |  |
| Notes:  | Please enter the reason for the employment break from the following valid entries:  A \- Leave of Absence E \- Education Break M \- Parental Break\* S \- Strike U \- Unauthorised  **Note**: The employment break reason will default to ‘U’ – Unauthorised if the data item is left blank. \*‘Y’ can be used to indicate the employment break reason was due to maternity or paternity. |  |  |  |  |
| **30** | SURNAME |  | Surname(s) of the employee.  | 25 | **Mandatory** |
| Example: | James  Howard-Jones Vaughan Williams O’Hara |  |  |  |  |
| Notes:  | Please enter the last name of the employee.  Valid characters are A to Z (upper- and lower-case), hyphen (-) and apostrophe (').  **This data item must be completed.** |  |  |  |  |
| **31** | FORENAMES |  | Forename(s) of the employee.  | 25 | **Mandatory** |
| Example: | Myfawny Amelia- Lily Lewis Watson |  |  |  |  |
| Notes:  | Please enter a **maximum of three (3)** forenames of the employee.  Valid characters are A to Z (upper- and lower-case), hyphen (-) and apostrophe (').  **This data item must be completed.** |  |  |  |  |
| **32** | GENDER |  | Gender of the employee.  | 1 | **Mandatory**  |
| Example: | M |  |  |  |  |
| Notes:  | Please enter either M (male) or F (female).  **This data item must be completed.** |  |  |  |  |
| **33** | DATE OF BIRTH |  | Date of birth of the employee | 10 | **Mandatory** |
| Example: | 06/05/1971 |  |  |  |  |
| Notes:  | Please enter the date format **DD/MM/YYYY**.  **This data item must be completed.** |  |  |  |  |
| **34** | MARITAL STATUS |  | The employee’s marital/partnership status. | 1 | Optional |
| Example: | M |  |  |  |  |
| Notes:  | Please enter the employee’s marital/partnership status from the following valid entries:  C \- Civil Partnership D \- Divorced M \- Married P \- Declared Partnership S \- Single W \- Widowed |  |  |  |  |
| **35** | TITLE |  | Title |  |  |
| Example: | Mr |  |  |  |  |
| Notes:  | Please enter one of the following valid titles:  Mr Mrs  Miss  Ms  Dr |  |  |  |  |
| **36** | FILLER |  | A spare field for future use.  | 10 | N/A |
| Example: | N/A |  |  |  |  |
| Notes:  | Leave blank or zero fill.  |  |  |  |  |
| **37** | FILLER |  | A spare field for future use.  | 10 | N/A |
| Example: | N/A |  |  |  |  |
| Notes:  | Leave blank or zero fill.  |  |  |  |  |
| **38** | ANNUAL PENSIONABLE SALARY |  | The annual pensionable salary for the employee.  | 10 | Optional |
| Example: | 18500.00 | ANNUAL |  |  |  |
| Notes:  | Please enter the employee's annual pensionable salary for the post. An effective date must be entered in Data Item 40 if an annual pensionable salary is entered. Enter only numbers (0-9) and decimal points (.).  **Leave blank if null.** |  |  |  |  |
| **39** | PENSIONABLE PAY |  | The pensionable pay or assumed pensionable pay of the employee for the current pay period.  | 10 | **Mandatory** |
| Example: | 1000.01 | PAY PERIOD |  |  |  |
| Notes:  | Please enter the employee's pensionable pay for the current payroll period.  Enter only numbers (0-9) and decimal points (.).  **Mandatory \- populate with “0.00” if null pay this period.**  |  |  |  |  |
| **40** | EFFECTIVE DATE |  | The effective date for the annual pensionable salary rate.  | 10 | **Conditional\*** |
| Example: | 01/04/2015 |  |  |  |  |
| Notes:  | Please enter the date from which the annual pensionable salary entered in item 38 is applicable.  Please enter the date in the format **DD/MM/YYYY**. **\*Mandatory if Data Item 38 is present; leave blank if Data Item 38 is blank.** |  |  |  |  |
| **41** | DATE JOINED PENSION SCHEME  |  | The date the employee joined the pension scheme.  |  | **Conditional\*** |
| Example: | 01/04/2015 |  |  |  |  |
| Notes:  | Please enter the date the member joined one of the following: Local Government Pension Scheme Police Pension Scheme Firefighters' Pension Scheme Please enter the date in the format **DD/MM/YYYY**. **\*Mandatory for new starters.** |  |  |  |  |
| **42** | JOB TITLE |  | Job title/description of the employee.  | 20 | Optional |
| Example: | Payroll Officer |  |  |  |  |
| Notes:  | Please enter the employee’s job title for this post.  |  |  |  |  |
| **43** | PART-TIME/WHOLE-TIME HOURS EFFECTIVE DATE |  | The date the employee started working the contracted part-time/whole-time hours.  | 10 | **Conditional\*** |
| Example: | 15/03/2015 |  |  |  |  |
| Notes:  | Please enter the effective date the employee started working the contracted part-time hours specified in Data Item 44 below. This should be the last date the member had a change in part-time hours, moved from part-time to full-time/casual, or vice versa. The date must be greater than the date entered in Data Item 41\.  This data item should also be populated for whole-time members.  Please enter the date in the format **DD/MM/YYYY**.  **\*Mandatory for part-timers and casuals (Data Item 45 set to Y or C).** |  |  |  |  |
| **44** | PART-TIME HOURS |  | The part-time hours of the employee working at this post.  | 5 | **Conditional\*** |
| Example: | 15.75 |  |  |  |  |
| Notes:  | Please enter the contracted part-time hours the employee is working for this post. If the member is whole-time or casual, this field should be left blank. Part-time hours must be pro-rated if the employee works term-time only. See section 7 below for examples.  **Note:** This figure cannot be equal to or greater than the value in Data Item 46\.  Enter only numbers (0-9) and a decimal point (.).  **\*Mandatory for part-timers.** |  |  |  |  |
| **45** | PART-TIME INDICATOR |  | An indicator to identify that the employee is part-time in this post.  | 1 | **Conditional\*** |
| Example: | Y |  |  |  |  |
| Notes:  | Please enter ‘Y’ if the employee is working part-time in this post. Please enter ‘C’ if the employee is a casual worker in this post.  Firefighters' Pension Scheme Only: Please enter ‘M’ if the employee is in the Modified section of the Firefighters' Pension Scheme. Please enter ‘R’ if the employee is in the Retained section of the Firefighters' Pension Scheme.  **\*Mandatory if PART-TIME HOURS (Data Item 44\) are present; leave blank for whole-time or casual members.** |  |  |  |  |
| **46** | WHOLE-TIME EQUIVALENT HOURS |  | The notional whole-time hours a part-time member would be working in this post.  | 5 | **Conditional\*** |
| Example: | 37.50 |  |  |  |  |
| Notes:  | Please enter the notional whole-time equivalent hours the employee would be working for this post. If the member is whole-time or casual, this field should be left blank. If Y is entered in Data Item 45, a figure greater than zero (0) must be entered.  Enter only numbers (0-9) and a decimal point (.).  **\*Mandatory for part-timers.** |  |  |  |  |
| **47** | EMPLOYEE’S MAIN SECTION CONTRIBUTION  |  | Employee's main section scheme contributions for the current payroll period.  | 10 | **Mandatory** |
| Example: | 120.00 | PAY PERIOD |  |  |  |
| Notes:  | Please enter the employee's main section scheme contributions for the current payroll period.  Enter only numbers (0-9) and a decimal point (.).  **Mandatory: populate with '0.00' if null pay this period.  Negative values are valid.** |  |  |  |  |
| **48** | EMPLOYERS CONTRIBUTIONS |  | Employer’s scheme contributions for the current pay period.  | 10 | **Mandatory** |
| Example: | 240.00 | PAY PERIOD |  |  |  |
| Notes:  | Please enter the employer's scheme contributions for the current payroll period.  Enter only numbers (0-9) and a decimal point (.).  **Mandatory: populate with '0.00' if null pay this period.  Negative values are valid.** |  |  |  |  |
| **49** | SCHEME  CONTRIBUTION RATE |  | Employer’s scheme contribution rate.  | 5 | **Mandatory** |
| Example: | 6.25 | PAY PERIOD |  |  |  |
| Notes:  | Please enter the member's scheme contribution rate (2.75 to 12.50) for the current payroll period.  Enter only numbers (0-9) and a decimal point (.).  **Mandatory: default rate required for members who have left or opted out of the scheme.** |  |  |  |  |
| **50** | OPT OUT DATE |  | The date the employee opted out of the pension scheme.  | 10 | **Conditional\*** |
| Example: | 31/05/2015 |  |  |  |  |
| Notes:  | Please enter the date the employee opted out of the pension scheme.  The Opt Out Date should be removed if the member opts back into the scheme and an Opt In Date is entered in Data Item 51\. All opt-outs should remain on the payroll extract file until they leave employment (at which point a date of leaving should be entered in Data Item 22).  Please enter the date in the format **DD/MM/YYYY**.  **Mandatory for opt-outs.**  |  |  |  |  |
| **51** | OPT IN DATE |  | The date the employee opted into the pension scheme.  | 10 | **Conditional\*** |
| Example: | 01/05/2015 |  |  |  |  |
| Notes:  | Please enter the date the employee opted into the pension scheme. The Opt In Date should be removed if the member opts out of the scheme, and an Opt Out Date is entered in Data Item 50\. Please enter the date in the format **DD/MM/YYYY**.   \***Mandatory for opt-ins; leave blank for existing LGPS members.** |  |  |  |  |
| **52** | MAIN SECTION CUMULATIVE PENSIONABLE PAY |  | The total pensionable pay or assumed pensionable pay in the main section of the CARE scheme for the scheme year (1 April \- 31 March) | 10 | **Mandatory** |
| Example: | 1000.01 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the cumulative pay to date total for the employee's main section pensionable pay for the current financial year.  Enter only numbers (0-9) and a decimal point (.).  **Mandatory: populate with '0.00' if null or the member is not in the CARE scheme.  Negative values are not valid.** |  |  |  |  |
| **53** | 50/50 SECTION CUMULATIVE PENSIONABLE PAY |  | The total pensionable pay or assumed pensionable pay in the main section of the CARE scheme for the scheme year (1 April \- 31 March) | 10 | **Mandatory** |
| Example: | 1000.01 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the cumulative pay to date total for the employee's 50/50 section pensionable pay for the current financial year. This is required only for members of the LGPS.  Enter only numbers (0-9) and a decimal point (.).  **Mandatory: populate with '0.00' if null or if the employee is not in the CARE scheme or a member of the Police or Firefighters' Pension Scheme.  Negative values are not valid.** |  |  |  |  |
| **54** | FULL-TIME EQUIVALENT FINAL PAY |  | Full-time equivalent pensionable pay in respect of the employment for the scheme year (pre-CARE scheme definition).  | 10 | **Mandatory** |
| Example: | 180000.0 | ANNUAL |  |  |  |
| Notes:  | Please enter the member's annual final pay, based on the pre-CARE definition of pay for the current financial year.  Please contact your administering authority if you are unable to provide an accurate FTE final pay. i-Connect recommends that this field be populated with '0.00' until a satisfactory arrangement has been agreed with theadministering authority.  A value is required before the scheme year end for use with annual benefit statements andmember self-service systems.  Enter only numbers (0-9) and a decimal point (.).   **Mandatory: populate with '0.00' if null.** |  |  |  |  |
| **55** | CUMULATIVE EMPLOYEE’S MAIN SECTION CONTRIBUTIONS |  | Employee’s main section cumulative scheme contributions.  | 10 | **Mandatory** |
| Example: | 999.99 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the cumulative contributions to date total for the employee's main section scheme contributions for the current financial year. Enter only numbers (0-9) and a decimal point (.).  **Mandatory: populate with '0.00' if null.** |  |  |  |  |
| **56** | CUMULATIVE EMPLOYER’S CONTRIBUTIONS |  | Employer’s cumulative scheme contributions.  | 10 | **Mandatory** |
| Example: | 1999.98 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the cumulative contributions to date total for the employer's main section scheme contributions for the current financial year. Enter only numbers (0-9) and a decimal point (.).  **Mandatory: populate with '0.00' if null.** |  |  |  |  |
| **57** | REASON FOR LEAVING  |  | Reason the employee terminated employment.  | 100 | Optional |
| Example: | Voluntary early retirement |  |  |  |  |
| Notes:  | This is a 100-character (including spaces) field to hold the reason why the employee's employment has terminated. |  |  |  |  |
| **58** | CUMULATIVE EMPLOYER SHARED COST APCs |  | Cumulative shared cost, additional pension contributions (employer contributions only).  | 10 | Optional |
| Example: | 1050.00 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the cumulative contributions to date total for any shared cost, additional pension contributions you pay on behalf of the employee (employee contributions should be excluded). Enter only numbers (0-9) and a decimal point (.). **Leave blank or populate with zero values if null.** |  |  |  |  |
| **59** | CUMULATIVE EMPLOYEE APCs |  | Cumulative employee's additional pension contributions (include employee SCAPC contributions, but exclude employer SCAPC contributions).  | 10 | Optional |
| Example: | 1050.00 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the cumulative contributions to date total for any additional pension contributions the employee is paying. Employee SCAPC contributions should be included; please do not include any employer SCAPC contributions.  Enter only numbers (0-9) and a decimal point (.). **Leave blank or populate with zero values if null.** |  |  |  |  |
| **60** | EMPLOYEE’S 50/50 SECTION CONTRIBUTIONS |  | Employee's 50/50 section scheme contributions for the current payroll period. | 10 | **Mandatory** |
| Example: | 360.00 | PAY PERIOD |  |  |  |
| Notes:  | Please enter the employee's 50/50 section scheme contributions for the current payroll period.  Enter only numbers (0-9) and a decimal point (.). **Mandatory: populate with '0.00' if null pay this period.  Negative values are valid** |  |  |  |  |
| **61** | CUMULATIVE EMPLOYEE’S 50/50 SECTION CONTRIBUTIONS  |  | Employee's cumulative 50/50 section scheme contributions.  | 10 | **Mandatory** |
| Example: | 999.99 | CUMULATIVE |  |  |  |
| Notes:  | Please enter the cumulative contributions to date total for the employee's 50/50 section scheme contributions for the current financial year.  Enter only numbers (0-9) and a decimal point (.). **Mandatory: populate with '0.00' if null** |  |  |  |  |
| **62** | PAY PERIOD SHARED COST |  | Pay period shared cost additional pension contributions (employer contributions only). | 10 | Optional |
| Example: | 100.50 | PAY PERIOD |  |  |  |
| Notes:  | Please enter the pay period total for any shared cost, additional pension contributions you pay on behalf of the employee (employee contributions should be excluded).  Enter only numbers (0-9) and a decimal point (.). **Leave blank or populate with zero values if null.** |  |  |  |  |
| **63** | PAY PERIOD EMPLOYEE APCs |  | Pay period employee additional pension contributions (include employee SCAPC contributions, but exclude employer SPAPC contributions.  | 10 | Optional |
| Example: | 100.50 | PAY PERIOD |  |  |  |
| Notes:  | Please enter the pay period total for any additional pension contributions the employee is paying. Employee SCAPC contributions should be included, but please do not include any employer SPAPC contributions Enter only numbers (0-9) and a decimal point (.). **Leave blank or populate with zero values if null.** |  |  |  |  |

# Example payroll extract file

NI\_NUMBER,PAY\_REF\_1,PAY\_REF\_2,PAY\_REF\_3,ADD\_LINE\_1,ADD\_LINE\_2,ADD\_LINE\_3,ADD\_LINE\_4,ADD\_LINE\_5,POSTCODE,EMAIL\_ADDRESS,TELEPHONE\_NUMBER,MOBILE\_NUMBER,WORKS\_PLACE\_NAME,WORKS\_ADD\_LINE\_1,WORKS\_ADD\_LINE\_2,WORKS\_ADD\_LINE\_3,WORKS\_ADD\_LINE\_4,WORKS\_ADD\_LINE\_5,WORKS\_POSTCODE,WORKS\_EMAIL\_ADDRESS,DATE\_OF\_LEAVING,PAYROLL\_PERIOD\_END\_DATE,ADDITIONAL\_CONTRIBUTIONS\_1,ADDITIONAL\_CONTRIBUTIONS\_2,EMPLOYMENT\_BREAK\_START,EMPLOYMENT\_BREAK\_END,FILLER\_1,EMPLOYMENT\_BREAK\_REASON,SURNAME,FORENAMES,GENDER,DOB,MARITAL\_STATUS,TITLE,FILLER\_2,FILLER,ANNUAL\_PENSIONABLE\_SALARY,PENSIONABLE\_PAY,EFFECTIVE\_DATE,DATE\_JOINED\_PENSION\_SCHEME,JOB\_TITLE,PART\_TIME\_HOURS\_EFFECTIVE\_DATE,PART\_TIME\_HOURS,PART\_TIME\_INDICATOR,WHOLE\_TIME\_EQUIVALENT\_HOURS,EMPLOYEES\_MAIN\_SECTION\_CONTS,EMPLOYERS\_CONTS,SCHEME\_CONT\_RATE,OPT\_OUT\_DATE,OPT\_IN\_DATE,MAIN\_SECTION\_CUMULATIVE\_PEN\_PAY,5050\_SECTION\_CUMULATIVE\_PEN\_PAY,FTE\_FINAL\_PAY,CUMULATIVE\_EMPLOYEES\_MAIN\_SECTION\_SCHEME\_CONTS,CUMULATIVE\_EMPLOYERS\_SCHEME\_CONTS,REASON\_FOR\_LEAVING,CUMULATIVE\_SCAPCs,CUMULATIVE\_APCs,EMPLOYEES\_5050\_CONTS,CUMULATIVE\_EMPLOYEES\_5050\_CONTS,SCAPCs,APCs

BB000001A,200001,1,,1 Willow Bank,Timperley,Altrincham,Cheshire,England,WA15 6LU,m.jones@gmail.com,1612823232,7901300648,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,100,,,,,,Jones,Martin,M,01/01/1961,M,Mr,,,17199,1433.25,01/04/2017,01/01/2008,30/12/1946,Supervisor,,,,,83.13,207.83,5.8,,,2866.5,0,17199,166.26,415.66,,,,0,0,,

BB000002A,200002,1,,5 Sandy Bank,Timperley,Altrincham,Cheshire,England,WA15 8YY,d.denton@aol.com,1612343223,7902500332,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,50,,,,,Denton,Daniel,M,02/01/1961,S,Miss,,,10617,884.75,01/04/2017,06/05/2010,03/05/1949,Carer,06/05/2010,20,Y,40,48.66,121.65,5.5,,,1769.5,0,21234,97.32,243.3,,,,0,0,,

BB000003A,200003,1,,85 Ash Close,Timperley,Altrincham,Cheshire,England,WA15 3TB,p.allen@yahoo.com,1612875441,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,,,,,,Allen,Pauline Tricia,F,03/01/1961,M,Mr,,,9328.5,777.38,01/04/2017,28/09/2005,24/09/1944,Carer,01/03/2012,20,Y,40,0,106.9,5.5,,,0,1554.76,18657,0,213.8,,,,42.76,85.52,,

BB000004A,200004,1,,47 South Parade,Timperley,Altrincham,Cheshire,England,WA15 1SS,coleen.carbery@hotmail.com,1612850984,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,,,,,,Carbery,Coleen,F,04/01/1961,S,Miss,,,25412,2117.67,01/04/2017,10/08/2012,06/08/1951,Carer,,,,,137.65,344.13,6.5,,,4235.34,0,25412,275.3,688.26,,,,0,0,,

BB000005A,200005,1,,7 Springwell Terrace,Timperley,Altrincham,Cheshire,England,WA15 3JD,c.johnston@live.co.uk,1612377643,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,,,,,,Johnston,Carol,F,05/01/1961,S,Miss,,,19598,1633.17,01/04/2017,24/12/2000,19/12/1939,Carer,,,,,94.72,236.8,5.8,,,3266.34,0,19598,189.44,473.6,,320.04,160.02,0,0,160.02,80.01

BB000006A,200006,1,,16 Upwell Road,Timperley,Altrincham,Cheshire,England,WA15 4NN,harry.james@talktalk.net,1612844423,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,,,,,,James,Harry Horrace,M,06/01/1961,M,Mr,,,3380.88,281.74,01/04/2017,02/10/2010,25/09/1949,Groundskeeper,02/10/2010,5,Y,40,15.5,38.75,5.5,,,563.48,0,27047,31,77.5,,,,0,0,,

BB000007A,200007,1,,87 Malpas Road,Timperley,Altrincham,Cheshire,England,WA15 9GF,m.brunt@sky.com,1612832267,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,,,,,,Brunt,Mary Jane,F,17/05/1991,M,Mrs,,,23478,1956.5,01/04/2017,03/03/2010,17/10/1918,Chef,,,,,127.17,317.93,6.5,,,3913,0,23478,254.34,635.86,,,,0,0,,

BB000008A,200008,1,,71 Hall Avenue,Timperley,Altrincham,Cheshire,England,WA15 7SW,alex.may@plusnet.com,1612899653,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,,,,,,May,Alex,M,08/01/1961,M,Mr,,,13992.75,1166.06,01/04/2017,15/10/1999,06/10/1938,Chef,08/01/2010,30,Y,40,64.13,160.33,5.5,,,2332.12,0,18657,128.26,320.66,,,,0,0,,

BB000009A,200009,1,,81 Deansgate Lane,Timperley,Altrincham,Cheshire,England,WA15 1WE,j.queen@tiscali.co.uk,1612333418,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,,31/05/2017,,,,,,,Queen,Jennifer,F,09/01/1961,S,Miss,,,24456,2038,01/04/2017,11/09/2013,01/09/1952,Senior Manager,,,,,132.47,331.18,6.5,,,4076,0,24456,264.94,662.36,,,,0,0,,

BB000010A,200010,1,,31 Bloomsbury Lane,Timperley,Altrincham,Cheshire,England,WA15 8CC,h.smith@homecall.co.uk,1612366598,,Outreach Unit,Timperley,Altrincham,Cheshire,,,WA15 3MJ,,31/05/2017,31/05/2017,45.12,,,,,,Smith,Harry,M,10/01/1961,M,Mr,,,12500.5,1041.71,01/04/2017,10/05/2010,29/04/1949,Director,10/05/2010,20,Y,40,57.29,143.23,5.5,,,2083.42,0,25001,114.58,286.46,Ill


# Frequently asked questions (FAQs) 

Below is a list of common questions and answers. Please contact the i-Connect support desk if you have any additional questions or comments relating to this guide. 

1. **Should I include all payees on the payroll extract file, including those employees who have previously opted out of the scheme?**

Whether you include opt-outs on the payroll extract file is entirely up to you and your administering authority, and the inclusion of opt-outs should be agreed during the implementation stage.

If you do decide to include opt-outs, the difference between the 'Opt Out Date' (Data Item 50\) and the 'Date Joined Scheme' (Data Item 41\) must be less than three months. This is because i-Connect will create new starter records on your administering authority's target system for each opt-out, irrespective of whether they ever existed on the target system, and a date of less than three months will ensure that the starter records are created with a status of 'Opt Out'.

2. **What should I do if an Opt Out re-joins the scheme?**

You must remove the 'Opt Out Date' from Data Item 50 and insert an 'Opt In Date' in Data Item 51\. The 'Opt In Date' should remain on the payroll extract file each month.

3. **How do I record service?** 
Examples:  
![][image1]

4. **How do I record part-time hours for casual employees?**

Part-time hours should be left blank if the employee is casual. Your administering authority will ask you for a summary of the total hours worked as part of their year-end process.

5. **How do I pro-rata the hours for term-time-only employees?**

Part-time hours must be pro-rated if the employee is term-time only. Two examples are provided below. Please check with your administering authority to ensure this complies with their own guidelines for pro-rating term-time service:

**Example 1 – Part-time, term-time only:**  
 Jennifer works for 12 hours per week during term time (full-time equivalent hours are 37). Her contract is for 39 weeks per year, plus 4.4 weeks' holiday, totalling 43.4 weeks. The following calculation can be used to pro-rate her hours:  
			43.4 weeks/52 weeks × 12 hours \= 10.02

Jennifer's part-time hours should be supplied as 10.02 and her whole-time equivalent hours as 37.00.

**Example 2 – Whole-time, term-time only:**  
Colin works whole-time during term time (37 hours per week). His contract is also for 39 weeks per year, plus 4.4 weeks' holiday, totalling 43.4 weeks. The following calculation can be used to pro-rate his hours:  
			 43.4 weeks/52 weeks × 37 hours \= 30.88  
 Colin's part-time hours should be supplied as 30.88 and his whole-time equivalent hours as 37.00.

6. **What happens if there is more than one part-time hours change in a single pay period?**

i-Connect can process only one part-time hours change in a single pay period. The latest hours change in the pay period, together with the effective date, should be output to the payroll extract file. Any earlier changes within the same pay period should be communicated via a separate report to the administering authority. 

7. **Why are payroll extract files with duplicate records rejected?**

This is because your administering authority records separate data on the target system for each active post on the payroll system, and there are one or more records containing duplicate combinations of National Insurance Number and the unique payroll identifier on the payroll extract file.

8. **My payroll system does not store all the elements required to calculate Full-Time Equivalent Pay (Data Item 54\) for employees who joined the scheme before 1 April 2014 (England and Wales) or 1 April 2015 (Scotland/Police and Fire); are there any alternative values I can use?**

You should discuss the use of alternative values for Data Item 54 with your administering authority.

9. **Why have salary validation errors been detected?**

This is because an annual salary is in Data Item 38, but an effective date has been omitted from Data Item 40, or vice versa.

10. **One or more of my payees do not have a National Insurance number; what should I do?**

You will be unable to include the member on the payroll extract file until a National Insurance number is provided, as this is a mandatory field on your administering authority's target system. They may be happy to accept a temporary National Insurance number for pension administration purposes.

11. **How do I record additional contributions?**

Cumulative additional voluntary contributions should be output to 'Additional Contributions 1' (Data Item 24); the cumulative values of all other additional contributions should be added together and output to 'Additional Contributions 2' (Data Item 25). Employer contributions cannot be stored on the target system.

12. **What type of employment break should I notify to the administering authority?**

You should notify your administering authority only of any unpaid breaks in service, for example, strike, maternity or paternity breaks.

13. **How long should leavers remain on the payroll extract file?**

Leavers can remain on the payroll extract file indefinitely, although it is recommended that they be purged on a regular basis. Generally, leavers remain on the payroll extract file for an additional pay period after the leaver notification, to ensure that any arrears of pay (usually for claims-based employees) are processed via i-Connect.

14. **How do I record assumed pensionable pay?**

This should be included in pensionable pay (Data Item 39\) and the main and/or 50/50 section cumulative pay (Data Items 52 and 53).

# About this version

This user guide version makes the following updates: 

* Corrections ToC format (e.g., sections starting at 2).  
* Uniform formatting in headers, letter spacing, font style, font size, font colour, revision history dates/names formatting, table layouts, and accessibility.   
* Corrections to passive and future voice, instructional phrasing, and concision.   
* Corrected Data Item 35 notes format.   
* Corrected Data Item 38 (FILLER) to match Data Items 36 and 37 (FILLERS) maximum number of characters.   
* Changed “Mandatory” text to bold, black text for accessibility.   
* Updated notes in Data Item 43 to reference Data Item 41\.   
* Removed “About this version” table in section 9 to avoid redundancy with 1: Revision history.

Sometimes we need to make changes to our specification due to circumstances outside of our control, such as legislation changes. If this happens, we will make sure we minimise disruption and give you plenty of time to start using the new payroll extract file specification.

# Need more help?

If you need any further assistance, you can contact the i-Connect support desk by: 

* Phone: 0161 613 4333  
* Email: support@i-Connect.co.uk

[image1]: <data:image/png;base64,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t27l7L333oujVZpmzZq5n/3sZ+7jjz+ODwkhhBBFpVrE/pNPPnF/+9vf3AYbbJCxQrPFFlu43XffPQ52N954Y7lyYLfddlscrdKcd955Pq3p06fHh4QQQoiiUnjVLePEE0/0QtioUSP36aefujfffNOHL1261A0ePNg98MAD7plnnim3DD5q1Cg/637xxRf9cjzHP/vsM39s9uzZfn/x4sV+n8FE3759ffy3337bh+UT+0ceecQtWLDA25o1a3x6CxcudMOGDXO9e/fOHHv44Yfdc889l3kkMHXqVPfSSy/5OEOHDnXffPOND4/FnvivvPKK69mzp3v++efdqlWr/HmEGaRF2tQbo669evVyb7zxRibOV1995VdEHn300Uz9hRBCiMpQcLFftmyZX97ecsst/VJ+yJ/+9CcvkD//+c/939q1a/vw5s2b+/3f/va3/twJEyb4/fbt2/vjt99+u99HHMeMGePPJx5GeJ8+ffKKPWI9f/78zICBsO233z4z2//zn//sttlmm8z+Nddc4+Mh6htvvHEmvEGDBplwE3uE++ijj87Ewf7+979723DDDd0XX3zhz9lvv/3cJpts4gcZhx56qI+36aab+r833XSTmzRpkm+D//mf//F1/N///V/32muvfV8RIYQQooIUXOwRLMTrwAMPjA+5e++9182cOdPPrP/5z396IWQb0d122239zP+jjz5yS5Ys8WkkiT2zembfDCqmTZvmw08++eS8Ym/GAIFBCNs77bSTGz16tNt77739fp06dXweiC3HwESd2Tdl5Hxm3KHYM9hgu2HDhu7rr792F1xwgd+3cnfq1Mmfw7m1atXyqxKEd+jQwS1fvtztueeefhBwwgkn+L+8B2DteMopp0Q1EkIIIXJTcLGfMmWKFykELIYl81NPPdUddNBB7te//rWPx0y7cePGfpvVgKuvvtqtXr3a7yeJPbPodu3aueOOO87tv//+PvyYY47JK/aXXXaZF9n+/fv7cMLatGnjtznGvj1u4H0DZthgoh5us7oQiv2ll17qt1999VUfb+zYsX6fRxjM0Clnly5dfBhluOKKK/w2g5xdd93Vbb755n5/u+228/EJwwg74IADfJpCCCFERSm42K9cudJttNFG3ngT3mC2Sthuu+3m7r//fj+zR8wQe342169fP7fHHnv4MFYA+Gsv0t1www1+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>
