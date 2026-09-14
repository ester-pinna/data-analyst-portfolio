# Channel Performance Analysis

Marketing performance data for a home decor e-commerce brand, across 5 channels (Google Ads, Meta Ads, Influencer, Email, Earned Media) and 13 campaigns, over roughly a year. Data cleaning in Python → modeling, DAX measures, and dashboard in Power BI.

## Structure
- `data/raw` — original marketing data export
- `data/processed` — cleaned dataset used in Power BI
- `01-data-cleaning` — cleaning and preparation notebook
- `02-dashboard` — Power BI dashboard (`.pbix`) and custom theme file (`.json`)

## Data Cleaning
- Standardized inconsistent channel naming ("meta ads" vs "Meta Ads")
- Removed 13 fully duplicated rows
- Handled 40 rows with missing revenue: filled with 0 where conversions = 0, filled with the channel-campaign average where conversions > 0
- Cast the date column to a proper datetime type

## Dashboard
Built in Power BI, with a custom theme (`Channel_Performance_Theme.json`) applied for consistent styling across visuals.

## Tools
Python (pandas) · Power BI (DAX)
