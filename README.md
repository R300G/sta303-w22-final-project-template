This is the template for the STA303/1002 Final Project, Winter 2022. For full information on this project, please see the [website](https://sta303-bolton.github.io/sta303-w22-final-project/).

# Guide to the folders and files

This files is a Markdown based README file. It will be rendered on GitHub as a landing page of sorts to help someone understand this project. It is good practice to have a README file to help orient a viewer to your project.

## Folder
- The `raw-data` folder should have the raw data provided by the client, as well where the licensed data for the postcode conversion file should be saved. This file should NOT be made publicially available if you share this project to your own github.

- The `data` folder should contain any datasets created in the `data-cleaning.Rmd` and used in `sta303-w22-final-project-template.Rmd`.

## Files 

- `data-preparation.Rmd` is where you should write the code for creating the datasets you will use in your main report. It should read in data from `raw-data` and the data sets you plan to use for the report into `data`. All other modelling, summaries, etc., shoul dbe done in the main Rmd. 
  - The purpose of this is to make sure that your main report is reproducible with the data you would be allowed to share publically, should you choose to do so. I.e., you could upload your `data` folder and your `sta303-w22-final-project-template.Rmd` to a public GitHub repo. 

- `sta303-w22-final-project-template.Rmd` is the file that should be updated to create your final report. It should only use data from the `data` folder.

- `report.tex` is the LaTeX template that helps create the final report. You should not need to edit it.

## A note on files paths

All files paths should be __relative__ to `sta303-w22-final-project-template.Rmd` and of the form `data/filename` or `raw-data/filename`.
