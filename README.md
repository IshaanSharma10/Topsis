# TOPSIS - Technique for Order Preference by Similarity to Ideal Solution

A comprehensive toolkit for performing TOPSIS (Technique for Order Preference by Similarity to Ideal Solution) multi-criteria decision analysis. Available as both a command-line Python tool and a modern web application.

## Description

TOPSIS is a multi-criteria decision analysis method that identifies the best alternative by calculating the distance from the ideal best solution and the ideal worst solution. This project provides two implementations:

1. **Command-Line Tool** (`topsis.py`) - Python script for batch processing
2. **Web Service** (`index.html`) - Interactive web application with modern UI

---

## 🖥️ Command-Line Tool

## Requirements

- Python 3.x
- pandas
- numpy
- openpyxl (for Excel file support)

## Installation

Install the required dependencies using pip:

```bash
pip install pandas numpy openpyxl
```

## Usage

```bash
python topsis.py <InputDataFile> <Weights> <Impacts> <OutputResultFileName>
```

### Parameters

- **InputDataFile**: Path to the input file containing the decision matrix (CSV or XLSX format)
- **Weights**: Comma-separated weights for each criterion (e.g., "1,1,1,1")
- **Impacts**: Comma-separated impact values for each criterion. Use '+' for beneficial criteria (higher is better) and '-' for non-beneficial criteria (lower is better) (e.g., "+,+,-,+")
- **OutputResultFileName**: Path to the output file where results will be saved (CSV or XLSX format)

## Input File Format

The input file must be in CSV or XLSX format with the following structure:

- **First column**: Alternative names/identifiers
- **Remaining columns**: Numeric values for each criterion

Example:

| Alternative | Criterion1 | Criterion2 | Criterion3 | Criterion4 |
|-------------|------------|------------|------------|------------|
| A1          | 0.5        | 0.3        | 0.2        | 0.4        |
| A2          | 0.6        | 0.4        | 0.3        | 0.5        |
| A3          | 0.4        | 0.5        | 0.4        | 0.3        |

**Note**: The input file must contain at least 3 columns (1 for alternatives + at least 2 criteria).

## Example

Given an input file `data.xlsx` with decision matrix data:

```bash
python topsis.py data.xlsx "1,1,1,1" "+,+,-,+" output.xlsx
```

This command will:
- Read the decision matrix from `data.xlsx`
- Apply equal weights (1,1,1,1) to all criteria
- Treat the first two and fourth criteria as beneficial (+) and the third as non-beneficial (-)
- Calculate TOPSIS scores and rankings
- Save results to `output.xlsx`

## Output

The output file will contain:
- All original columns from the input file
- **Topsis Score**: The calculated TOPSIS score for each alternative (higher is better)
- **Rank**: The ranking of alternatives based on TOPSIS scores (1 is the best)

## How TOPSIS Works

1. **Normalization**: The decision matrix is normalized to eliminate units of measurement
2. **Weighted Normalization**: Each normalized value is multiplied by its corresponding weight
3. **Ideal Solutions**: Determines the ideal best and ideal worst solutions based on impact types
4. **Distance Calculation**: Calculates Euclidean distance from each alternative to ideal best and ideal worst
5. **TOPSIS Score**: Computes the relative closeness to the ideal solution
6. **Ranking**: Ranks alternatives based on TOPSIS scores

## Error Handling

The tool will display error messages and exit if:
- Input file is not found
- Unsupported file format is used
- Input file has less than 3 columns
- Non-numeric values are found in criteria columns
- Number of weights/impacts doesn't match number of criteria
- Invalid impact values (must be '+' or '-')
- Incorrect number of command-line arguments

---

## 🌐 Web Service

A pure client-side web application for TOPSIS analysis. All processing happens in the browser using JavaScript - no backend required!

### Web Service Features

- ✅ **Pure frontend solution** - no backend needed
- ✅ **Drag & drop file upload** - intuitive file handling
- ✅ **Real-time data preview** - see your data before processing
- ✅ **Interactive results visualization** - formatted tables with statistics
- ✅ **TOPSIS calculation in JavaScript** - all processing in browser
- ✅ **Automatic file download** - results saved immediately
- ✅ **Email integration** - results sent via EmailJS
- ✅ **Modern, responsive UI** - beautiful interface with animations
- ✅ **Enhanced XLSX support** - robust Excel file handling

### Web Service Usage

1. Open `index.html` in a web browser (Chrome, Firefox, Edge, Safari)
2. **Upload your input data file** (CSV or XLSX) - drag and drop or click to browse
3. **Enter weights** (comma-separated, e.g., "1,1,1,1")
4. **Enter impacts** (comma-separated, + or -, e.g., "+,+,-,+")
5. **Enter your email address** for receiving results
6. Click **"Process TOPSIS Analysis"**
7. View results in the results panel with statistics and rankings
8. Result file is automatically downloaded and sent to your email

### Web Service Input Format

Same as command-line tool:
- **First column**: Alternative names/identifiers
- **Remaining columns**: Numeric values for each criterion

### Web Service Validation

The web service validates:
- Number of weights must equal number of impacts
- Impacts must be either '+' (beneficial) or '-' (non-beneficial)
- Weights and impacts must be comma-separated
- Email format must be valid
- Input file must have at least 3 columns
- All criteria values must be numeric

### Email Setup (Web Service)

The web application uses EmailJS for sending emails. To enable email functionality:

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

### Web Service Dependencies

All dependencies are loaded via CDN (no installation needed):
- **SheetJS (xlsx.js)**: For reading/writing Excel files
- **EmailJS**: For sending emails (optional)
- **Font Awesome**: For icons

### Web Service Browser Compatibility

Works in all modern browsers that support:
- ES6 JavaScript
- File API
- Fetch API

### Web Service Features in Detail

- **Data Preview Tab**: View your uploaded data in a formatted table
- **Results Tab**: See TOPSIS scores, rankings, and statistics
- **Statistics Dashboard**: Shows alternatives count, best score, average score, and top alternative
- **Rank Badges**: Color-coded rankings (gold, silver, bronze)
- **Progress Indicators**: Visual feedback during processing
- **Error Handling**: Clear, helpful error messages

---

## 📊 How TOPSIS Works

1. **Normalization**: The decision matrix is normalized to eliminate units of measurement
2. **Weighted Normalization**: Each normalized value is multiplied by its corresponding weight
3. **Ideal Solutions**: Determines the ideal best and ideal worst solutions based on impact types
4. **Distance Calculation**: Calculates Euclidean distance from each alternative to ideal best and ideal worst
5. **TOPSIS Score**: Computes the relative closeness to the ideal solution
6. **Ranking**: Ranks alternatives based on TOPSIS scores

## 🔧 Error Handling

Both tools will display error messages if:
- Input file is not found (CLI) or cannot be read (Web)
- Unsupported file format is used
- Input file has less than 3 columns
- Non-numeric values are found in criteria columns
- Number of weights/impacts doesn't match number of criteria
- Invalid impact values (must be '+' or '-')
- Incorrect number of command-line arguments (CLI only)
- Invalid email format (Web only)

## 📝 Example Usage

### Command-Line Example

```bash
python topsis.py data.xlsx "1,1,1,1" "+,+,-,+" output.xlsx
```

### Web Service Example

1. Open `index.html` in browser
2. Upload `data.xlsx`
3. Enter weights: `1,1,1,1`
4. Enter impacts: `+,+,-,+`
5. Enter email: `user@example.com`
6. Click "Process TOPSIS Analysis"

Both will produce the same results with:
- All original columns
- **Topsis Score** column
- **Rank** column

## 🚀 Quick Start

### For Command-Line Tool:
```bash
pip install pandas numpy openpyxl
python topsis.py <InputFile> <Weights> <Impacts> <OutputFile>
```

### For Web Service:
1. Open `index.html` in any modern web browser
2. No installation required - everything runs in the browser!

## 📄 License

This project is open source and available for use.
