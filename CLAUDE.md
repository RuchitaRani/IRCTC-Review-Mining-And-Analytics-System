# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
This is an IRCTC Review Analysis Dashboard built with Streamlit that analyzes 90,000+ app reviews to provide real-time insights, department-wise segregation, root cause analysis, and trend visualization.

## Development Commands

### Running the Application
```bash
# Install dependencies
pip install -r requirements.txt

# Run the main Streamlit dashboard
streamlit run streamlit_app.py

# Run specific dashboard variants
streamlit run src/dashboard/app.py                    # Basic dashboard
streamlit run src/dashboard/analytics_dashboard.py   # Advanced analytics
streamlit run src/dashboard/root_cause_dashboard.py  # Root cause analysis
streamlit run src/dashboard/professional_app.py      # Professional theme
streamlit run src/dashboard/modern_app.py            # Modern theme
streamlit run src/dashboard/tesla_dashboard.py       # Tesla-inspired theme
streamlit run src/dashboard/segregated_dashboard.py  # Department segregated
```

### Dependencies
Core dependencies defined in `requirements.txt`:
- streamlit>=1.31.0 (web framework)
- pandas>=2.0.3 (data manipulation)
- numpy>=1.26.0 (numerical computing)
- plotly>=5.18.0 (interactive visualizations)

Additional dependencies used in dashboard variants:
- sqlite3 (database connectivity)
- wordcloud (text visualization)
- matplotlib (plotting)
- PIL/Pillow (image processing)

## Architecture

### Main Application Structure
- **`streamlit_app.py`** - Primary dashboard deployment file for Streamlit Cloud with unified interface
- **`src/dashboard/`** - Contains multiple dashboard variants with different themes and features
- **`data/`** - Contains SQLite database (`reviews.db`) and analysis artifacts
- **`.streamlit/config.toml`** - Streamlit configuration with dark theme settings

### Data Architecture
- **SQLite Database**: `data/reviews.db` contains review data with tables for reviews and review_classifications
- **Pre-computed Models**: Stored as pickle files in `data/models/` and `data/analysis/`
  - `improved_topics.pkl` - Topic modeling results
  - `root_cause_analysis.pkl` - Root cause analysis results
  - `full_analysis_results.pkl` - Complete analysis pipeline results

### Dashboard Components
Each dashboard variant follows a similar pattern:
1. **Data Loading**: Database connections and cached data loading functions
2. **Visualization**: Plotly charts with consistent dark theme styling
3. **Multi-page Navigation**: Sidebar navigation between Overview, Department Analysis, Root Cause Analysis, and Trends
4. **Custom CSS**: Professional dark theme with metric cards and styled components

### Key Features
- **Real-time Analytics**: Live data updates from SQLite database
- **Department Segregation**: Classification of reviews into app, railway, unclear, and mixed categories
- **Root Cause Analysis**: Automated identification of issue patterns and recommended solutions
- **Trend Analysis**: Time series visualization of review volume and ratings
- **Interactive Visualizations**: Plotly-based charts with hover interactions and filtering

### Database Schema
- `reviews` table: Contains review text, ratings, dates, and metadata
- `review_classifications` table: Contains department classifications and issue categories
- Queries use aggregations and JOINs to compute metrics and statistics

### Styling and Theming
- Consistent dark theme (#0e1117 background, #1e293b cards)
- Custom CSS classes: `.metric-card`, `.section-header`, `.recommendation-card`
- Professional color palette with blue accents (#3b82f6)
- Responsive design with Streamlit's column layouts