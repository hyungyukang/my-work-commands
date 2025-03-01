# My work commands

## $${\color{red}Shell}$$
### Background transfer job
1. Start transfer using `rsync`
2. `CTRL + z`
3. `ps -u hgkang` (PID check)
4. `disown $PID`


### Parallel (efficient) tar using `pigz`
#### Compression
```shell
tar cf - paths-to-archive | pigz -9 -p 32 > file.tar.gz
```
or
```shell
tar -cf bigbackup.tar.gz -I pigz /opt
```
##### Decompression
```shell
tar -I pigz -xf file.tar.gz
```



##
## $${\color{red}NCO}$$
### Extract variables
```shell
ncks -C -v lonCell,latCell x1_20km_era5_init_2022010100.nc mpas_grid.nc
```

### Remapping
```shell
ncremap -m map.nc in.nc out.nc
```




##
## $${\color{red}CDO}$$
### Merging GRIB files
```shell
cdo merge in1.grib in2.grib out.grb
```

### Split GRIB files daily
```shell
cdo splitday in.grib out
```




##
## $${\color{red}ESM}$$
### Shorterm archive
```shell
./case.st_archive --last-date 0101-01-01 --force-move --no-incomplete-logs
```

### Creating mapping files
```shell
ESMF_RegridWeightGen  -s ne30np4_091226_pentagons.nc   -d 129x256_SCRIP.nc   -w map_ne30np4_fv129x256_aave.DATE.nc --method conserve
```
```shell
ESMF_RegridWeightGen  -s ne30np4_091226_pentagons.nc   -d 257x512_SCRIP.nc     -w map_ne30np4_fv257x512_bilin.DATE.nc --method bilinear
```

### Creating MPAS-O SCRIP file
```shell
conda activate mpas-analysis
```
```shell
create_SCRIP_file_from_MPAS_mesh.py -m x1_20km_era5_init_2022010100.nc -s mpasScrip.nc
```

### Omega clang format check

