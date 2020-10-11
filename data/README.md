# Data

This folder contains the data used for this project. 


The `original` folder contains the files listed on the [ASUC Financial Disclosure](https://asuc.org/financial-disclosure/) webpage. Spreadsheets hosted on Google Docs were downloaded as _.xlsx_ files, and PDFs were downloaded as is.


The `reformatted` folder contains the datasets, with special formatting and aggregated sub-totals / totals manually removed, separated by year. The records for 2013-2014, 2014-2015, and 2015-2016 were converted from _.pdf_ to _.xlsx_ files using [Zamzar](https://www.zamzar.com/convert/pdf-to-xlsx/). Each file was then saved in _.txt_ format to more easily import to Jupyter Notebook.


`all_data.csv` combines the files in `reformatted`; the source code can found in `create_all_data.ipynb` in the `notebooks` directory. `all_data.csv` contains the following data: 

| Column | Description |
| ----- | ----- |
| `Year` | The budget year of the data point. For example, a value of `2012` indicates that the budget year is 2012-2013. |
| `Organization` | An RSO's registered name under the ASUC. |
| `Type` | Organization type as defined by the ASUC. For example, `SAG` stands for 'Student Activity Group'. |
| `Standing` | How long an RSO has been officially recognized by the ASUC. |
| `Allocation` | How much funding an RSO received in the given budget year. |