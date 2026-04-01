# data-detective

> Toss in a data file. Get back a detective report with anomalies, patterns, and insights.

A [Claude Code](https://claude.ai/code) skill that automatically investigates CSV/JSON data files, discovers anomalies, hidden patterns, and interesting insights — outputting a detective-themed HTML report.

## Features

- **5-Phase Investigation Pipeline**
  1. **Scene Survey** — Shape, dtypes, missing values, basic statistics
  2. **Fingerprinting** — Duplicates, format inconsistencies, encoding issues
  3. **Anomaly Tracking** — IQR + Z-score outliers, rare categories (<2%)
  4. **Correlation Search** — Numeric correlations, category-numeric group differences, distribution skewness
  5. **Case Summary** — Top findings ranked by severity with confidence scores
- **Severity Levels** — Critical / Warning / Info classification
- **Detective-Themed HTML Report** — Dark UI with collapsible sections and Chart.js visualizations

## Installation

```bash
claude skill add daizhouchen/data-detective
```

## How It Works

1. **Investigate** — `scripts/investigate.py` runs all 5 analysis phases on your data
2. **Report** — `scripts/report.py` generates an interactive HTML report

## Manual Usage

```bash
# Run investigation on a CSV file
python3 scripts/investigate.py path/to/data.csv

# Generate the HTML report
python3 scripts/report.py
# Output: /tmp/data_detective_report.html
```

## Trigger Phrases

- "分析一下" / "帮我看看数据"
- "数据有没有问题" / "有什么有趣的发现"
- Just drop a CSV file — the skill suggests itself

## Project Structure

```
data-detective/
├── SKILL.md                # Skill definition and workflow
├── scripts/
│   ├── investigate.py      # 5-phase data investigation
│   └── report.py           # HTML report generator
├── assets/
│   └── test_data.csv       # Sample data with planted anomalies
└── README.md
```

## Report Sections

| Section | Content |
|---------|---------|
| Case Summary | Top 3 most important findings |
| Evidence Board | Charts: missing values, outliers, correlations, skewness |
| Suspect List | Data quality issues to address |
| Cross-References | Correlation matrix and group comparisons |
| Leads | Directions for further analysis |

## Requirements

- Python 3.8+
- pandas (`pip install pandas`)

## Supported File Formats

- CSV (`.csv`)
- JSON (`.json`) — flat or records-oriented

## License

MIT
