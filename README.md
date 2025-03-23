Overview
This project is a web-based form that allows users to contact their UK Member of Parliament (MP) regarding Bitcoin policy. It collects user details (name, email, postcode) and uses the TheyWorkForYou API to fetch MP information based on the postcode. MP email addresses are sourced from a hardcoded CSV within the script, and the form includes GDPR consent for data processing compliance.
Installation and Setup
Dependencies: 
Requires an internet connection for Tailwind CSS (loaded via CDN: https://cdn.tailwindcss.com).
No local server is needed; the file can run as a static HTML page in a browser.
API Key: 
Obtain an API key from TheyWorkForYou to use the MP lookup feature.
Replace the hardcoded key (FncmgQEVdkSUE32UAMFKFsca) in the JavaScript with your own for security in production.
Usage
Open the HTML file in a web browser.
Enter your full name, email address, and UK postcode in the form fields.
Check the GDPR consent box to agree to data processing for contacting your MP.
Click "Find My MP" to submit the form.
The form will display your MP's details (name, constituency) and provide a clickable email link with a pre-filled subject and body.
Technical Details
Technologies: 
HTML5 for structure.
Tailwind CSS (via CDN) for styling.
Vanilla JavaScript for form handling and API integration.
API Integration: 
Uses the TheyWorkForYou API endpoint https://www.theyworkforyou.com/api/getMP?postcode=${postcode}&key=${apiKey} to fetch MP data by postcode.
Note: The API does not provide email addresses, so these are sourced from the hardcoded CSV.
Hardcoded Data and API Source
Current Implementation: The JavaScript contains a CSV string with MP details (forename, surname, constituency, email). This is used to match the API-returned MP name to an email address, as the TheyWorkForYou API excludes emails.
API for Updates: To replace the hardcoded CSV, use the UK Parliament dataset available at data.parliament.uk. This CSV includes current MP names, constituencies, and email addresses.
Creating a Database for Automatic Updates
To avoid manual updates to the CSV:
Data Source: Download the latest MPs dataset from data.parliament.uk in CSV format.
Setup: Parse the CSV and store it in a local database (e.g., SQLite) or a JSON file with fields: Forename, Surname, Constituency, Email.
Automation: Use a script (e.g., Python) and a scheduled task (e.g., cron job) to periodically (e.g., weekly) fetch and update the database with the latest data.
Integration: Modify the JavaScript function getMpData to query this database instead of the CSV string.
Notes
Ensure compliance with data.parliament.uk usage policies when automating updates.
For production, secure the API key by moving API calls to a server-side script to prevent exposure in client-side code.
