---
title: Instalación y configuración de miniconda para AEDV
author: Aurora Zuoris
date: 2023-02-05
---

# Instalación

Esta práctica se realizó en __EndeavourOS Linux x86_64 (6.1.8-arch1-1)__.
Con lo que para empezar, se descarga el script de instalación de miniconda.

```sh
$ curl https://repo.anaconda.com/miniconda/Miniconda3-py310_22.11.1-1-Linux-x86_64.sh \
> miniconda.sh ; bash miniconda.sh
```

Una vez instalado, se puede comprobar que funciona con la siguiente instrucción

```sh
$ conda -V
conda 23.1.0
```

# Configuración de entorno

Una vez conda esta instalado, se puede utilizar este para crear y configurar entornos.

Primero se crea un entorno `aedv` que se utilizará para la asignatura:

```sh
$ conda create -n aedv python=3.10
```

Una vez creada, esta se puede activar usando el siguiente comando:

```sh
$ conda activate aedv
```

Desde aquí se puede comprobar que python está instalado

```sh
$ python -V
Python 3.10.9
```

A continuación, se instalan los paquetes que se utilizarán para trabajar:

```sh
conda install pandas matplotlib jupyterlab numpy scikit-learn
```

Estos se pueden comprobar que funcionan entrando en python e importando las librerías.

Para ver las versiones de los paquetes instalados, se usa `conda list`:

```sh
$ conda list | grep "\(pandas\|matplotlib\|jupyterlab\|numpy\|scikit-learn\)\s"
jupyterlab                3.5.2           py310h06a4308_0  
matplotlib                3.6.2           py310h06a4308_0  
numpy                     1.23.5          py310hd5efca6_0  
pandas                    1.5.2           py310h1128e8f_0  
scikit-learn              1.2.0           py310h6a678d5_0  
```

# Exportar el entorno

Por último, para exportar la configuración de este entorno de forma
agnóstica al sistema operativo, se puede ejecutar `conda env export --from-history`:

```sh
$ conda env export --from-history
name: aedv
channels:
  - defaults
dependencies:
  - python=3.10
  - numpy
  - scikit-learn
  - jupyterlab
  - pandas
  - matplotlib
prefix: /home/aurora/miniconda3/envs/aedv
```

Aunque se podría argumentar que el prefijo sobra.
Dado que no todos tendrían su instalación de conda identica a la mía, además de que hay algunos sistemas operativos en los que un camino se especifique con
otros separadores de línea, etc.

# Dificultades

En general la instalación de miniconda y
configuración de un entorno es muy simple.
Los mayores retos con los que uno puede enconrarse sería asegurarse de
tener una conección a internet para instalar los paquetes, y encontrar
la documentación de conda para saber como configurar conda.
