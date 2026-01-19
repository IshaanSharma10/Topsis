# TOPSIS Web Service - Frontend Only

A pure client-side web application for TOPSIS (Technique for Order Preference by Similarity to Ideal Solution) analysis. All processing happens in the browser using JavaScript - no backend required!

## Features

- ✅ Pure frontend solution - no backend needed
- ✅ File upload (CSV or XLSX)
- ✅ Real-time validation
- ✅ TOPSIS calculation in JavaScript
- ✅ Automatic file download
- ✅ Email sending via EmailJS (client-side email service)
- ✅ Beautiful, modern UI

## Usage

1. Open `index.html` in a web browser
2. Upload your input data file (CSV or XLSX)
3. Enter weights (comma-separated, e.g., "1,1,1,1")
4. Enter impacts (comma-separated, + or -, e.g., "+,+,-,+")
5. Enter your email address
6. Click "Process TOPSIS"
7. The result file will be automatically downloaded and sent to your email

## Input File Format

- **First column**: Alternative names/identifiers
- **Remaining columns**: Numeric values for each criterion

Example:
```
Alternative,Criterion1,Criterion2,Criterion3,Criterion4
A1,0.5,0.3,0.2,0.4
A2,0.6,0.4,0.3,0.5
A3,0.4,0.5,0.4,0.3
```

## Validation Rules

- Number of weights must equal number of impacts
- Impacts must be either '+' (beneficial) or '-' (non-beneficial)
- Weights and impacts must be comma-separated
- Email format must be valid
- Input file must have at least 3 columns
- All criteria values must be numeric

## Email Setup (Optional)

The application uses EmailJS for sending emails. To enable email functionality:

1. Sign up for a free account at [EmailJS](https://www.emailjs.com/)
2. Create an email service (Gmail, Outlook, etc.)
3. Create an email template
4. Get your Public Key, Service ID, and Template ID
5. Update the following in `index.html`:
   - Uncomment the `emailjs.init()` line and add your Public Key
   - Update `service_id` in the `sendEmail` function
   - Update `template_id` in the `sendEmail` function
   - Update `user_id` in the `sendEmail` function

If EmailJS is not configured, the application will use a mailto: link as a fallback.

## Dependencies

All dependencies are loaded via CDN:
- **SheetJS (xlsx.js)**: For reading/writing Excel files
- **EmailJS**: For sending emails (optional)

No installation or build process required!

## Browser Compatibility

Works in all modern browsers that support:
- ES6 JavaScript
- File API
- Fetch API

## How It Works

1. User uploads a file which is read using FileReader API
2. File is parsed using SheetJS library (supports CSV and XLSX)
3. TOPSIS algorithm is calculated entirely in JavaScript
4. Result is converted to Excel format using SheetJS
5. File is automatically downloaded
6. Email is sent via EmailJS (client-side service)

## Example

```
Input File: data.xlsx
Weights: 1,1,1,1
Impacts: +,+,-,+
Email: user@example.com
```

The result will include:
- All original columns
- Topsis Score column
- Rank column

## Notes

- All processing happens in your browser - your data never leaves your device
- No server or backend required
- Email sending requires EmailJS setup (free tier available)
- Large files may take a moment to process
