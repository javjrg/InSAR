# Interferometría SAR

La interferometría es una técnica utilizada para el seguimiento de deformaciones en la superficie y también en la generación de modelos de terreno. La idea central de la llamada Interferometría Diferencial o DInSAR, es hacer uso de la fase de la señal del radar de apertura sintética (SAR), el cual permite analizar la topografía y los cambios en la elevación del terreno entre las pasadas consecutivas del satélite en el mismo lugar.

El objetivo de este repositorio es dar a conocer las aplicaciones de la interferometría en el estudio de las deformaciones de la suferpicie. Para ello, este repositporio cuenta con una sección donde se enseña como utilizar esta metodología [link](/Notebooks/) como también algunos proyectos donde esta técnica es usada [link](#proyectos)<br>

## ISCE

El paquete de software escogido para poder calcular los interferogramas es *InSAR Scientific Computing Environment (ISCE)*, desarrollado en el Jet Propulsion Laboratory (JPL) de NASA, específicamente para este fin. Debido a que el cálculo de un interferograma involucra varias fases o etapas, es posible particionar en proceso más reducidos de manera de controlar el flujo. ISCE es un software de código abierto que actualmente admite el procesamiento de datos adquiridos por las siguientes plataformas: ALOS, ALOS2, COSMO-SkyMed, EnviSAT, ERS, KOMPSAT5, RadarSAT2, RISAT1, Sentinel1, TerraSAR-X, Tandem-X y UAVSAR. ISCE también puede leer algunos datos en formato SICD.

ISCE está disponible en si pagina de GitHub [link](https://github.com/isce-framework/isce2)

### Instalación 

#### Linux y MacOSX (intel)

La instalación de ISCE2 la haremos mediante anaconda, para ellos necesitamos los siguientes requerimientos:

```
python<3.10
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
isce2 
boto3 
jupyter 
conda-build
```
Podemos escribir los requerimientos en un archivo de texto llamado "requirimientos.txt" y con ellos crear el entorno mediante anaconda con el comando
```bash
> conda create --name env_isce
```
Activamos el entorno antes creado
```bash
> conda activate env_isce
```
Instalamos las librerías necesarias
```bash
> conda install -c conda-forge --file requerimientos.txt
``` 

<div class="alert alert-danger">
<b>Advertencia:</b>
Es necesario considerar una versión de python menos a 3.10 esto debido a errores al ejecutar el paso `rangecoreg` en `topsApp.py`. He probado con la versión python 3.9.13 y ha funcionado sin problemas.
</div>

#### MacOSX (Apple Silicon)

Para las computadoras con Apple Silicon, podemos instalar ISCE2 con anaconda mediante Rosetta 2 siguiendo los siguientes pasos:
```bash
> CONDA_SUBDIR=osx-64 conda create --name env_isce
> conda activate env_isce
> conda config --env --set subdir osx-64 
> conda install -c conda-forge --file requerimientos.txt
```

#### Microsoft Windows

Para Microsoft Windows, se debe intalar mediante WSL2 y seguir las instrucciones de instalación de Linux.

## MintPy

El software Miami INsar Time-series en PYthon (MintPy) es un paquete de código abierto para el análisis de series temporales de radar de apertura sintética interferométrica (InSAR). Lee la pila de interferogramas (corregistrados y no envueltos) en formato ISCE, ARIA, FRInGE, HyP3, GMTSAR, SNAP, GAMMA o ROI_PAC, y produce un desplazamiento de la superficie terrestre tridimensional (2D en el espacio y 1D en el tiempo) en línea de dirección de la vista. Incluye un análisis de serie temporal de rutina (`smallbaselineApp.py`) y una caja de herramientas independiente.

### Instalación 

#### Linux 

Ejecute lo siguiente en su terminal para descargar la versión de desarrollo de MintPy:

```bash
> mkdir tools
> cd ~/tools
> git clone https://github.com/insarlab/MintPy.git
```
Instale las dependencias en un entorno existente personalizado ejecutando:

```bash
> conda create --name mintpy_env
> conda activate mintpy_env
> conda install -c conda-forge --file ~/tools/MintPy/requirements.txt
```
Instale MintPy en el entorno actual con pip ejecutando:

```bash
> cd ~/tools
> python -m pip install -e MintPy
```

#### macOS (intel)

Instale Xcode con herramientas de línea de comandos, si aún no lo ha hecho.

- Instalar `Xcode` desde la tienda de aplicaciones
- instale `command line tools` dentro de XCode y acepte los términos de la licencia.

```bash
> xcode-select --install -s /Applications/Xcode.app/Contents/Developer/
> sudo xcodebuild -license
```
- Instale [XQuartz](https://www.xquartz.org/), luego reinicie la terminal.

Instalar MintPy a través de conda siguiendo las instrucciones para Linux.

#### macOS (Apple Silicon)

Para las computadoras con Apple Silicon, podemos instalar MintPy con anaconda mediante Rosetta 2 siguiendo los siguientes pasos:
```bash
> CONDA_SUBDIR=osx-64 conda create --name mintpy_env
> conda activate mintpy_env
> conda config --env --set subdir osx-64 
> conda install -c conda-forge --file ~/tools/MintPy/requirements.txt
```

Luego, instale MintPy en el entorno actual con pip ejecutando:

```bash
> cd ~/tools
> python -m pip install -e MintPy
```

#### Microsoft Windows

Para Microsoft Windows, se debe intalar mediante WSL2 y seguir las instrucciones de instalación de Linux.

<a id="proyectos"></a>
## Proyectos

En esta sección describiremos algunos preyecto donde se utilizó InSAR....

* Desarrollo de un sistema de monitoreo de glaciares rocosos y cubiertos de detritos con uso de sensores remotos e inteligencia artificial [link](/Proyectos/Glaciar_de_Roca)