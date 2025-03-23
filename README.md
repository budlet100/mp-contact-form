
Overview
This project provides a web-based form for users to contact their UK Member of Parliament (MP) about Bitcoin policy. Key features include:
Collects user details: name, email, and postcode.
Uses the TheyWorkForYou API to fetch MP information based on the postcode.
Sources MP email addresses from a hardcoded CSV within the script.
Includes GDPR consent for data processing compliance.
Installation and Setup
Dependencies
Internet Connection: Required for Tailwind CSS, loaded via CDN (https://cdn.tailwindcss.com).
Local Server: Not required; the file can run as a static HTML page in a browser.
API Key
Obtain an API key from TheyWorkForYou for the MP lookup feature.
Replace the hardcoded key (FncmgQEVdkSUE32UAMFKFsca) in the JavaScript with your own for security in production.
Usage
Open the HTML file in a web browser.
Fill in the form with:
Your full name.
Your email address.
Your UK postcode.
Check the GDPR consent box to agree to data processing for contacting your MP.
Click "Find My MP" to submit the form.
View your MP's details (name, constituency) and use the provided clickable email link with a pre-filled subject and body to contact them.
Technical Details
Technologies
HTML5: For the structure of the form.
Tailwind CSS: For styling, loaded via CDN.
Vanilla JavaScript: For form handling and API integration.
API Integration
Endpoint: Uses the TheyWorkForYou API at https://www.theyworkforyou.com/api/getMP?postcode=${postcode}&key=${apiKey} to fetch MP data by postcode.
Limitation: The API does not provide email addresses, so these are sourced from a hardcoded CSV.
Hardcoded Data and API Source
Current Implementation
The JavaScript includes a CSV string with MP details (forename, surname, constituency, email).
This CSV is used to match the API-returned MP name to an email address, as the TheyWorkForYou API excludes emails.
API for Updates
To replace the hardcoded CSV, use the UK Parliament dataset available at data.parliament.uk.
This dataset provides current MP names, constituencies, and email addresses in CSV format.
Creating a Database for Automatic Updates
To avoid manual updates to the CSV, you can set up a database with the following steps:
Data Source:
Download the latest MPs dataset from data.parliament.uk in CSV format.
Setup:
Parse the CSV and store it in a local database (e.g., SQLite) or a JSON file.
Include fields: Forename, Surname, Constituency, Email.
Automation:
Use a script (e.g., Python) and a scheduled task (e.g., cron job) to periodically (e.g., weekly) fetch and update the database with the latest data.
Integration:
Modify the JavaScript function getMpData to query this database instead of the CSV string.
Notes
Data Compliance: Ensure compliance with data.parliament.uk usage policies when automating updates.
Security: For production, secure the API key by moving API calls to a server-side script to prevent exposure in client-side code.
