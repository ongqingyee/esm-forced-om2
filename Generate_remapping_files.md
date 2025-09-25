## Generate remapping files for ESM forced ocean runs 

Why new remapping files are needed:
* Remapping files map the UM atmosphere model onto MOM5.
* Includes information about ocean masking (wet vs. dry cells)
* ESM1.5 remapping files have a map on the atmosphere as well, but the YATM of ACCESS-OM2 does not include that.

#### Obtaining atmospheric mask
* `mask_scrip_files.ncl` reads in UM `grids.nc` and `masks.nc`
* use the following to make scrip files have a mask of 1 everywhere
   * ncap2 -s 'grid_imask=grid_imask*0+1' um1t_scrip.nc um1t_scrip_nomask.nc`
   * `ncap2 -s 'grid_imask=grid_imask*0+1' um1u_scrip.nc um1u_scrip_nomask.nc`
   * `ncap2 -s 'grid_imask=grid_imask*0+1' um1v_scrip.nc um1v_scrip_nomask.nc`
* use `make_remap_weights.py` – save scrip files from those of arbitrary names. 
(CHECK ORDER OF OPERATIONS)

#### Replace OM mask to match new topography/wet cells
* MOM5_1deg_scrip.nc mask with that from ESM
`/home/561/qo9901/esm1p5_mask/ocean_mask.nc` – created from gridspec.nc of ESM
* Run `replace_ocean_mask_ESM.py` in lg87
* Then run reshape_scrip.py to reshape array to 1 dimension only
* Now we rerun make_esmf_cmds.sh to convert scrip to remapping file
	* Or make_esmf_1cpu.sh 
* Run `rename_for_oasis.py`
