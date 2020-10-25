# Data

This folder contains the data used for this project. 

## Folder Structure

The `original` folder contains the files listed on the [ASUC Financial Disclosure](https://asuc.org/financial-disclosure/) webpage. Spreadsheets hosted on Google Docs were downloaded as _.xlsx_ files, and PDFs were downloaded as is.

The `reformatted` folder contains the datasets, with special formatting and aggregated sub-totals / totals manually removed, separated by year. The records for 2013-2014, 2014-2015, and 2015-2016 were converted from _.pdf_ to _.xlsx_ files using [Zamzar](https://www.zamzar.com/convert/pdf-to-xlsx/). Each file was then saved in _.txt_ format to more easily import to Jupyter Notebook.

`all_data.csv` combines the files in `reformatted`; the source code can found in `create_all_data.ipynb` in the `notebooks` directory. `all_data.csv` contains the following: 

| Column | Description |
| ----- | ----- |
| `Year` | The budget year of the data point. For example, a value of `2012` indicates that the budget year is 2012-2013. |
| `Organization` | An RSO's registered name under the ASUC. |
| `Type` | Organization type as defined by the ASUC. For example, `SAG` stands for 'Student Activity Group'. |
| `Standing` | How long an RSO has been officially recognized by the ASUC. |
| `Allocation` | How much funding an RSO received in the given budget year. |

*Folder to be updated with cleaned budget data (rso_data.csv) and CalLink data (callink_data.csv)*

## Data Sources

### Budget Data

The budget data from 2012 to 2020 can be found on the [ASUC Financial Disclosure](https://asuc.org/financial-disclosure/) webpage. Up until the 2017-2018 budget year, the ASUC published the amount of funding RSOs requested, the Chief Finance Officer's first pass at allocations, the Finance Committee's subsequent pass, and the final allocation value. From 2018 and on, only the final allocations are available. 

It appears that the data is manually updated throughout the ABSA process, as I noticed typing errors throughout the data cleaning process. That said, I plan to interview the CFO about how these spreadsheets are created and maintained in order to confirm these findings.

Because this data is made public by the ASUC, a non-profit and unincoporated association, I do not anticipate encountering any issues with licensing. I do, however, take ownership and responsibility for the cleaned `rso_data.csv`; in addition to uniformizing the budget data, I also fixed inconsistencies with RSO names to better track individual RSO funding over time. These fixes, as well as any name changes, were confirmed using CalLink.

### CalLink Data

[CalLink](https://callink.berkeley.edu/) is a centralized hub of information for UC Berkeley's RSOs.

Using [Selenium](https://pypi.org/project/selenium/), I created a web scraper to extract the official names and CalLink Designations (such as Technology RSO, Academic RSO, Spiritual RSO, etc.) for active RSOs on CalLink's [Organizations](https://callink.berkeley.edu/organizations) page. This data would be used to:

1. Uniformize RSO names in regard to capitalizations and/or abbreviations.
2. Introduce CalLink Designation as a new feature to distinguish club types.

Much like the ASUC's budget data, CalLink is available to the public for use, so I do not anticipate any licensing issues. That said, I take responsibility for manually inputting CalLink Designations for inactive RSOs. Because inactive RSOs aren't listed on the aforementioned Organizations webpage, I used the web address `callink.berkeley.edu/organization/XYZ` -- where `XYZ` is replaced by an RSOs name or abbreviation -- to look up former RSO pages and edit `callink_data.csv`.