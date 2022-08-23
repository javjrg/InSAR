# Interferometría SAR

El objetivo de este repositorio.....

## ISCE

InSAR Scientific Computing Environment (ISCE) es un marco diseñado para procesar datos de radar de apertura sintética (SAR) y SAR interferométrico (InSAR) de código abierto. Actualmente, ISCE admite el procesamiento de datos adquiridos por las siguientes plataformas: ALOS, ALOS2, COSMO-SkyMed, EnviSAT, ERS, KOMPSAT5, RadarSAT2, RISAT1, Sentinel1, TerraSAR-X, Tandem-X y UAVSAR. ISCE también puede leer algunos datos en formato SICD.

ISCE está disponible en si pagina de GitHub [link](https://github.com/isce-framework/isce2)

### Instalación para Linux y MacOSX (intel)

La instalación de ISCE2 la haremos mediante anaconda, para ellos necesitamos los siguientes requerimientos:

```
Python 3.6
cython
gdal
git
h5py
libgdal
pytest
numpy
fftw
scipy
basemap
scons
opencv
```
Podemos escribir los requerimientos en un archivo de texto llamado "requirimientos.txt" y con ellos crear el entorno mediante anaconda con el comando
```bash
> conda create --name env_isce --file requerimientos.txt
```
Activamos el entorno antes creado
```bash
> conda activate env_isce
```
Instalamos ISCE2
```bash
> conda install –c conda-forge isce2 boto3 jupyter conda-build
```

### MacOSX (Apple Silicon)

Para las computadorar con Apple Silicon, podemos instalar ISCE2 con anaconda mediante Rosetta 2 siguiendo los siguientes pasos:
```bash
> CONDA_SUBDIR=osx-64 conda create --name env_isce --file requerimientos.txt 
> conda activate env_isce
> conda install –c conda-forge isce2 boto3 jupyter conda-build
```

### Microsoft Windows

Para instalar en Microsoft Windows se debe intalar mediante WSL2 y seguir las instrucciones de instalación de Linux.

## Proyectos

En esta sección describiremos algunos preyecto donde se utilizó InSAR....