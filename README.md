# esm-forced-om2

Scripts to apply ACCESS-ESM model output as forcing to ACCESS-OM2. 

Config file for ACCESS-OM2 with accomodations for the ESM forcing are here: https://github.com/ongqingyee/1deg_esm1p5_multiyrtest. 

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
