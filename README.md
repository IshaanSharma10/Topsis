# TOPSIS - Technique for Order Preference by Similarity to Ideal Solution

A command-line Python tool for performing TOPSIS (Technique for Order Preference by Similarity to Ideal Solution) multi-criteria decision analysis.

## Description

TOPSIS is a multi-criteria decision analysis method that identifies the best alternative by calculating the distance from the ideal best solution and the ideal worst solution. This tool automates the TOPSIS calculation process for decision matrices.

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

## License

This project is open source and available for use.
