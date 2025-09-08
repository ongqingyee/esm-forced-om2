# esm-forced-om2

Scripts to apply ACCESS-ESM model output as forcing to ACCESS-OM2, based on JRA55-do reanalysis forced runs. 
* Eg_atm_forcing_w_ESM1p5.ipynb : reformat UM variables to be read by OM2
* Eg_make_friver_variable.ipynb : reformat ESM ocean runoff data for runoff and calving input
* Eg_ocean_restart_ESMtoOM.ipynb : interpolate ESM ocean temp and salt restart file to OM2 vertical grid.

Config file for ACCESS-OM2 with accomodations for the ESM forcing are here: https://github.com/ongqingyee/1deg_esm1p5_multiyrtest. 

See ACCESS-Hive and ERA forced run issues for discussion:
* https://github.com/COSIMA/access-om2/issues/242
* https://forum.access-hive.org.au/t/forcing-access-om2-using-esm1-5-data/4349

#### Runoff and calving forcing

* Runoff: extract ```friver``` variable from ESM ocean output and interpolate to JRA grid
* Calving: blank forcing file with same dimensions as JRA

#### Remapping UM to MOM

Documentation for generating remapping files in progress. 

#### Mapping of JRA55-do variables to UM atmospheric variables

| JRA55-do Variable | UM atm Variable | UM Dimension         | UM Description                                    |
|-------------------|-----------------|----------------------|--------------------------------------------------|
| tas – 10m air temperature (θA), units: K | fld_s03i236 | (time, lat, lon)    | TEMPERATURE AT 1.5M, units: K                    |
| huss – 10m specific humidity (qA), units: kg kg⁻¹ | fld_s03i237 | (time, lat, lon)    | SPECIFIC HUMIDITY AT 1.5M                        |
| uas – 10m eastward wind, units: m s⁻¹ | fld_s03i209 | (time, lat, lon_u)  | 10 METRE WIND U-COMP                             |
| vas – 10m northward wind, units: m s⁻¹ | fld_s03i210 | (time, lat_v, lon)  | 10 METRE WIND V-COMP                             |
| psl – Sea level pressure (SLP), units: Pa | fld_s00i409 | (time, lat, lon)    | SURFACE PRESSURE AFTER TIMESTEP, units: Pa       |
| rsds – Downward shortwave (QDSW), units: W m⁻² | fld_s01i235 | (time_0, lat, lon) | TOTAL DOWNWARD SURFACE SW FLUX, units: W m⁻² |
| rlds – Downward longwave (QDLW), units: W m⁻² | fld_s02i207 | (time_0, lat, lon) | DOWNWARD LW RAD FLUX: SURFACE, units: W m⁻²       |
| prra – Rainfall flux, units: kg m⁻² s⁻¹ | fld_s05i214 | (time_0, lat, lon) | RAINFALL RATE: LS+CONV, units: kg m⁻² s⁻¹        |
| prsn – Snowfall flux, units: kg m⁻² s⁻¹ | fld_s05i215 | (time_0, lat, lon) | TOTAL SNOWFALL RATE: LS+CONV, units: kg m⁻² s⁻¹  |
