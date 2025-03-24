# MP Contact Form

A simple web form for users to contact their UK Member of Parliament (MP) about Bitcoin policy, built with HTML, Tailwind CSS, and JavaScript.

## Features

- Collects user details: name, email, and UK postcode.
- Fetches MP information using the TheyWorkForYou API.
- Displays MP details with a clickable email link for direct contact.
- Includes GDPR consent for data processing compliance.
- Sources MP email addresses from a hardcoded CSV (with an option to upgrade to a database).

## Getting Started

### Prerequisites

- An internet connection for Tailwind CSS (loaded via CDN: [Tailwind CDN](https://cdn.tailwindcss.com)).
- No local server required; runs as a static HTML file in a browser.

### API Key Setup

1. Get an API key from TheyWorkForYou.
2. Replace the hardcoded key (`FncmgQEVdkSUE32UAMFKFsca`) in the JavaScript with your own key for security.

### Usage

1. Open the HTML file in a web browser.
2. Enter your name, email, and UK postcode.
3. Check the GDPR consent box.
4. Click "Find My MP" to submit.
5. View your MP's details (name, constituency) and use the email link to contact them.

## Technical Details

### Built With

- **HTML5**: Form structure.
- **Tailwind CSS**: Styling (via CDN).
- **JavaScript**: Form handling and API integration.

### API Integration

- **Endpoint**: `https://www.theyworkforyou.com/api/getMP?postcode=${postcode}&key=${apiKey}`
- **Limitation**: The TheyWorkForYou API does not provide email addresses, so these are sourced from a hardcoded CSV in the script.

## Managing MP Data

### Current Approach: Hardcoded CSV

- The script includes a CSV string with MP details (forename, surname, constituency, email).
- Used to match the API-returned MP name to an email address.

### Upgrading to a Database

To keep MP data up-to-date without manual updates:

1. **Source**: Download the latest MP dataset in CSV format from [data.parliament.uk](https://data.parliament.uk).
2. **Storage**: Parse the CSV and store in a local database (e.g., SQLite) or JSON file with fields: Forename, Surname, Constituency, Email.
3. **Automation**: Use a script (e.g., Python) with a scheduled task (e.g., cron job) to update the database weekly.
4. **Integration**: Update the `getMpData` function in the JavaScript to query the database instead of the CSV.

## Important Notes

- **Data Compliance**: Follow data.parliament.uk usage policies for automated updates.
- **Security**: In production, secure the API key by handling API calls server-side to avoid exposure in client-side code.
