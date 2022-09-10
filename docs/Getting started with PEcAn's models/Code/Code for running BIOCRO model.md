``` r
# Clean environment ------------------------------------------------------------
rm(list = ls())

# Load packages ----------------------------------------------------------------
library(PEcAn.all)
library(PEcAn.BIOCRO)
library(PEcAn.utils)
library(RCurl)

# Working directory ------------------------------------------------------------
setwd('/home/carya')
getwd()

# Read settings file -----------------------------------------------------------
settings <- PEcAn.settings::read.settings("basic_biocro_model.xml")


# PEcAn Workflow ---------------------------------------------------------------
settings <- PEcAn.settings::prepare.settings(settings, force = FALSE)

## Write pecan.CHECKED.xml -----------------------------------------------------
PEcAn.settings::write.settings(settings, outputfile = "pecan.CHECKED.xml")
PEcAn.settings::check.workflow.settings(settings)

## Do conversions --------------------------------------------------------------
settings <- PEcAn.workflow::do_conversions(settings)

##  Query the trait database for data and priors -------------------------------
settings <- runModule.get.trait.data(settings)

## Check db connection ---------------------------------------------------------
print(db.open(settings$database$bety))

## Run the PEcAn meta.analysis -------------------------------------------------
runModule.run.meta.analysis(settings)

## Write model specific configs ------------------------------------------------

settings <- PEcAn.workflow::runModule.run.write.configs(settings)
PEcAn.settings::write.settings(settings, outputfile='pecan.CONFIGS.xml')

## Start ecosystem model runs --------------------------------------------------

PEcAn.remote::runModule.start.model.runs(settings, stop.on.error = FALSE)

### Get results of model runs --------------------------------------------------
# Step for generating ensemble.output

runModule.get.results(settings)

## Run ensemble analysis on model output ---------------------------------------
runModule.run.ensemble.analysis(settings, TRUE)

## Run sensitivity analysis on model output ------------------------------------
runModule.run.sensitivity.analysis(settings)

# End --------------------------------------------------------------------------
rm(list = ls())


```