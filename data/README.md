# Data

This folder contains the data used for this project. 

## Directory Structure

The `archived` folder contains data that was either filtered or updated into other files and is no longer in use.

The `original` folder contains the files listed on the [ASUC Financial Disclosure](https://asuc.org/financial-disclosure/) webpage, the initial 2018-2019 and 2019-2020 allocations, and a list of organizations that filed an appeal for the 2019-2020 budget year. Spreadsheets hosted on Google Docs were downloaded as _.xlsx_ files, and PDFs were downloaded as is.

The `reformatted` folder contains the initial and final allocation datasets from the `original` folder with special formatting and aggregated sub-totals / totals manually removed. The records for 2013-2014, 2014-2015, and 2015-2016 were converted from _.pdf_ to _.xlsx_ files using [Zamzar](https://www.zamzar.com/convert/pdf-to-xlsx/). Each file was then saved in _.txt_ format to more easily import to Jupyter Notebook. The folder also includes initial allocations 

### Files

| Name | Description | 
| ----- | ----- |
| `callink_data` | Scraped RSO names and designations from CalLink. |
| `initial_allocs_XXXX` | Initial allocations with cleaned RSO names for that particular budget year. |
| `norm_rso_data` | Normalized `rso_data_v2`. |
| `rso_appeals_2019` | Cleaned names of RSOs that filed an appeal for the 2019-2020 budget year. |
| `rso_data_v2` |  `all_data` and `callink_data` combined and filtered for RSOs with corrections to `Standing`.  |

All source code can be found in the `notebooks` folder.

## Data Structure

The cleaned `rso_data`, to be used for analysis and modeling, contains the following data: 

| Column | Description |
| ----- | ----- |
| `Year` | The budget year of the data point. For example, a value of `2012` indicates that the budget year is 2012-2013. |
| `Organization` | An RSO's registered name under the ASUC. |
| `Type` | Organization type as defined by the ASUC. For example, `SAG` stands for 'Student Activity Group'. |
| `Designation` | RSO type as labelled on CalLink. |
| `Standing` | How long an RSO has been officially recognized by the ASUC. |
| `Allocation` | The final funding allocation an RSO received in the given budget year. |

The `initial_allocs_XXXX` files have a similar structure, except `Allocation` refers to the initial allocation for an RSO. These distinctions are made clear within the notebooks.

## Data Sources

### Budget Data

The budget data from 2012 to 2020 can be found on the [ASUC Financial Disclosure](https://asuc.org/financial-disclosure/) webpage. The initial allocations for the 2018-2019 and 2019-2020 budget years were acquired through emails from the OCFO during my time as an RSO leader. All of this data was manually inputted and updated by the OCFO. Additionally, ASUC CFO David Wang provided the list of RSOs that filed an appeal in the 2019-2020 budget year.

Because this data is made public by the ASUC, a non-profit and unincoporated association, I do not anticipate encountering any issues with licensing. I do, however, take ownership of and responsibility for the cleaned `rso_data_v2.txt`; in addition to uniformizing the budget data, I also fixed inconsistencies with RSO names to better track individual RSO funding over time. These fixes, as well as any name changes, were confirmed using CalLink.

### CalLink Data

[CalLink](https://callink.berkeley.edu/) is a centralized hub of information for UC Berkeley's RSOs.

Using [Selenium](https://pypi.org/project/selenium/), I created a web scraper to extract the official names and CalLink Designations (such as Technology RSO, Academic RSO, Spiritual RSO, etc.) for active RSOs on CalLink's [Organizations](https://callink.berkeley.edu/organizations) page. This data would be used to:

1. Make RSO names consistent in regard to capitalizations and/or abbreviations.
2. Introduce CalLink Designation as a new feature to distinguish club types.

Much like the ASUC's budget data, CalLink is available for public use, so I do not anticipate any licensing issues. That said, I take responsibility for manually inputting CalLink Designations for inactive RSOs. Because inactive RSOs aren't listed on the aforementioned Organizations webpage, I used the web address `callink.berkeley.edu/organization/XYZ` -- where `XYZ` is replaced by an RSOs name or abbreviation -- to look up former RSO pages and edit `callink_data.csv`.