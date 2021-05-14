# Notebooks

This folder contains the Jupyter Notebook files for this project.

| Notebook | Description |
| ----- | ----- |
| `clean_data` | Creates `rso_data.txt` by cleaning `all_data.csv` and adding CalLink designations, `callink_data.txt`, for RSO naming consistency. `rso_data_v2.txt`, created at the end of the notebook, adds adjustments to `Standing`. |
| `compare_allocs_XXXX` | Creates `initial_allocs_XXXX.csv` and `rso_appeals_2019`; compares allocations and appeal success. |
| `create_all_data` | Creates `all_data.csv`. | 
| `eda` | Exploratory data analysis on the cleaned `rso_data.txt`. |
| `preprocessing` | Creates bins for `Standing` and `norm_rso_data`. |
| `scrape_callink` | Creates `callink_data.txt` by scraping CalLink for RSO names and designations. | 