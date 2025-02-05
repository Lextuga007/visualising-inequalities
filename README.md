
<!-- README.md is generated from README.Rmd. Please edit that file -->

# visualising-inequalities

<!-- badges: start -->
<!-- badges: end -->

This repository is aimed at sharing the R code underlying the joint
Strategy Unit / British Heart Foundation (BHF) project to visualise
socio-economic inequalities along the CHD pathway

The project included development of a new tool, built using Shiny and
aimed at helping Integrated Care Boards (ICBs) get an overview of the
points on the care pathway where inequalities emerge and are amplified.

In this repository we aim to provide key sections of code to facilitate
re-use on similar projects.

The first two sections of published code are the RII calculations and
the calculations that assign GP practices into IMD deciles.

The next code to be published will be the shiny app and the code
required to generate the RDS needed for the shiny app.

**RII Calculations:**

The code rii_calculations.R can be used to calculate the RII with lower
and upper confidence intervals and with a confidence interval determined
within the code

The input data for this stage of the process is the rds
activity_by_type_decile_stg1_testdata.rds

This data has a row for each IMD decile. The first column is the IMD
decile number, the second column is the total GP list size for that
decile. Each of the other columns is the total activity for that metric
and decile. In this example there are 32 metrics.

This test dataset has been created using a random number generator with
data items in a range similar to the original dataset.

The output of this stage of the process is sii_table which contains one
row per metric and columns for SII, UCI, LCI, RII, UCI_RII, LCI_RII and
RR

**Assign GP practices into IMD deciles:**

The code calculate_gpprac_imd_deciles.R takes three xlsx files as inputs
and generates a GP practice list with each practice assigned to an IMD
decile and a July-2022 ICB.

The three input files are  
1) patients_by_lsoa_to_gp.xlsx

The file here is from January 2020, used in this project as the GP
practice list sizes timeframe is consistent with much of the data used
for the metrics and is also pre-pandemic. The file contains practice
list sizes split by LSOA. The latest version of this file can be
obtained from :

<https://digital.nhs.uk/data-and-information/publications/statistical/patients-registered-at-a-gp-practice/april-2022>

2)  imd_2019.xlsx

This file contains the IMD 2019 scores, ranks and deciles for each 2011
LSOA

3)  gp-reg-pat-prac-map-jul22.xlsx

This file maps each GP practice to a July 2022 ICB

The output of this code is a patient weighted GP practice IMD.

**Strategy Unit / British Heart Foundation (BHF) project:**

The tool is available here:
<https://connect.strategyunitwm.nhs.uk/content/b05b649b-511d-4921-9069-2a7a62d694dd/>

The accompanying report including methodology and a recording of a
webinar about the tool is available here:
<https://www.bhf.org.uk/-/media/files/publications/research/bhf_visualising-socio-economic-inequalities-in-chd-progression-and-pathways_sept2022.pdf?rev=e43c10defd7a4579a2795887d6728b37&hash=C3933086783DC0E35F4341FEADD087DA>

Here is an example of the visualisation used in the tool to display the
data generated using the RII calculations

<img src="img/example-chart.png" height="600"/>
