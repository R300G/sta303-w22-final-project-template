This is the template for the STA303/1002 Final Project, Winter 2022. For full information on this project, please see the [website](https://sta303-bolton.github.io/sta303-w22-final-project/).

# Guide to the folders and files

This files is a Markdown based README file. It will be rendered on GitHub as a landing page of sorts to help someone understand this project. It is good practice to have a README file to help orient a viewer to your project.

## Folder
- The `data-raw` folder should have the raw data provided by the client, as well where the licensed data for the postcode conversion, the census data and your web scrapign results should be saved. This file should NOT be made publicly available. 

- The `data` folder should contain any datasets created in the `data-cleaning.Rmd` and used in `sta303-final-project.Rmd`.

- The `cache` folder will appear after you set up the Canadian census data. It doesn't not need to be submitted as part of you assessment.

## Files 

- `README.MD` this file that you're reading! It tells you about the contents and set up of this project.

- `data-prep.Rmd` is where you should write the code for creating the datasets you will use in your main report. It should read in data from `raw-data` and the data sets you plan to use for the report into `data`. All other modelling, summaries, etc., should be done in the main Rmd. 
  - The purpose of this is to make sure that your main report is __reproducible__ with the data you would be allowed to share publicly, should you choose to do so. I.e., you could upload your `data` folder and your `sta303-final-project.Rmd` to a public GitHub repo. 

- `sta303-final-project.Rmd` is the file that should be updated to create your final report. It should only use data from the `data` folder.

- `report.tex` is the LaTeX template that helps create the final report. You should not need to edit it.

## A note on files paths

All files paths should be __relative__ to `sta303-final-project.Rmd` and of the form `data/filename` or `raw-data/filename`.

# Guide to the data

+------------------+-------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| Dataset          | Variables                                                         | Description                                                                                                     |
+==================+===================================================================+=================================================================================================================+
| `cust_dev.Rds`   | `cust_id`, `dev_id`                                               | Matches each customer to their current device.                                                                  |
+------------------+-------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| `customer.Rds`   | `cust_id`, `dob`, `postcode`, `sex`, `pronouns`, `emoji_modifier` | General information we held about each customer for use in the app and associated profile and chat features.    |
+------------------+-------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| `device.Rds`     | `dev_id`, `device_name`, `line`, `released`                       | Additional information about each device in these data. May be useful for connecting with the industry dataset. |
+------------------+-------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
| `cust_sleep.Rds` | `cust_id`, `date`, `duration`, `flags`                            | Sleep data for each customer.                                                                                   |
+------------------+-------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+

: Table 1: Guide to client provided data

### Guide to the variables

+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Variable         | Description                                                                                                                                                                                                                                                                                                      |
+==================+==================================================================================================================================================================================================================================================================================================================+
| `cust_id`        | Unique ID for each customer.                                                                                                                                                                                                                                                                                     |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `dob`            | Date of birth, as entered by customer. Year, month, day format.                                                                                                                                                                                                                                                  |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `postcode`       | Postal code of customer.                                                                                                                                                                                                                                                                                         |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `sex`            | Biological sex, used for calculations of health metrics, like body-mass index and base metabolic rate.                                                                                                                                                                                                           |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `pronouns`       | Pronouns for social profile.                                                                                                                                                                                                                                                                                     |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `emoji_modifier` | Code for skin tone modifier for emojis when using the chat and react features of the social component of our app. These are the standard [unicode modifiers](https://unicode.org/emoji/charts/full-emoji-modifiers.html), based on the Fitzpatrick scale. If not set, this means the default yellow colour used. |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `dev_id`         | Unique ID for each device registered with our app.                                                                                                                                                                                                                                                               |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `device_name`    | Name of device type.                                                                                                                                                                                                                                                                                             |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `line`           | Line of products this device belongs to.                                                                                                                                                                                                                                                                         |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `released`       | Release date for this particular device type. Year, month, day format.                                                                                                                                                                                                                                           |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| `date`           | For sleep data, date sleep session started. Year, month, day format.                                                                                                                                                                                                                                             |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| duration         | Duration, in minutes, of sleep session.                                                                                                                                                                                                                                                                          |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| flags            | Number of times there was a quality flag during the sleep session. Flags may occur due to missing data, or due to data being recorded but sufficiently unusual to suggest it may be a sensor error or other data quality issue.                                                                                  |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

: Table 2: Client data variables

## Additional hints

+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------+
| Dataset                  | Variables                                                                                                                                                                                                                | Description                                                                                  |
+==========================+==========================================================================================================================================================================================================================+==============================================================================================+
| Web scraped device data  | `Device name`, `Line`, `Recommended retail price`, `Battery life`, `Water resitance`, `Heart rate sensor`, `Pulse oximiter`, `GPS`, `Sleep tracking`, `Smart notifications`, `Contactless payments`, `Released`, `Brand` | Source: <https://fitnesstrackerinfohub.netlify.app/>.                                        |
|                          |                                                                                                                                                                                                                          |                                                                                              |
|                          |                                                                                                                                                                                                                          | See [*Data and hints*](https://sta303-bolton.github.io/sta303-w22-final-project/hints.html). |
+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------+
| Median income data       | `CSDuid`, `hhld_median_inc`, `Population`                                                                                                                                                                                | Procured through the Census Mapper API.                                                      |
|                          |                                                                                                                                                                                                                          |                                                                                              |
|                          |                                                                                                                                                                                                                          | See [*Data and hints*](https://sta303-bolton.github.io/sta303-w22-final-project/hints.html). |
+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------+
| Postcode conversion file | `PC`, `CSDuid`                                                                                                                                                                                                           | Sourced through U of T Libraries.                                                            |
|                          |                                                                                                                                                                                                                          |                                                                                              |
|                          |                                                                                                                                                                                                                          | See [*Data and hints*](https://sta303-bolton.github.io/sta303-w22-final-project/hints.html). |
+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------+

: Table 3: Hints for data you must acquire elsewhere
