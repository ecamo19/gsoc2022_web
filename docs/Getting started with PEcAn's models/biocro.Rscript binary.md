``` r

#!/usr/bin/env Rscript

args   <- commandArgs(trailingOnly = TRUE)
rundir <- args[1]
outdir <- args[2]

if(interactive()) {
  runid <- readLines(file.path(settings$rundir, "runs.txt"))[1]
  rundir <- file.path(settings$rundir, runid)
  outdir <- file.path(settings$outdir, "out", runid)
}

config <- PEcAn.BIOCRO::read.biocro.config(file.path(rundir, "config.xml"))

metpath <- config$run$met.path

if(!is.null(config$run$soil.file)){
  soil.nc <- ncdf4::nc_open(config$run$soil.file)
} else {
  soil.nc <- NULL
}

# atmco2.nc <- ncdf4::nc_open(file.path(inputdir, "co2/CO2_Global_HD_v1.nc"))

lat <- as.numeric(config$location$latitude)
lon <- as.numeric(config$location$longitude)

out <- PEcAn.BIOCRO::run.biocro(lat, lon,
                  metpath = metpath,
                  soil.nc = soil.nc, 
                  config = config)

daily <- out$daily
save(daily, file = file.path(outdir, 'daily.result.RData'))

biocro_result <- data.table::data.table(lat = lat, lon = lon, out$daily)
save(biocro_result, file = file.path(outdir, "biocro_output.RData"))

#hourly <- out$hourly
#save(hourly, file = file.path(outdir, "biocro_hourly.RData"))

PEcAn.BIOCRO::model2netcdf.BIOCRO(result = out$hourly,
                    genus = config$pft$type$genus, 
                    outdir = outdir, 
                    lat = lat, lon = lon)
```