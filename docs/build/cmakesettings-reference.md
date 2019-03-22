---
title: Referencia del esquema de CMakeSettings.json
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 893bc5c8efe3fdae80a4a0de8204d391baa63d07
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356119"
---
# <a name="cmakesettingsjson-schema-reference"></a>Referencia del esquema de CMakeSettings.json

El **cmakesettings.json**' archivo contiene información que especifica cómo Visual Studio debe interactuar con CMake para compilar un proyecto para una plataforma específica. Use este archivo para almacenar información como variables de entorno o argumentos para el entorno cmake.exe.

## <a name="environments"></a>Entornos

La matriz `environments` contiene una lista de `items` de tipo `object` que definen un "entorno". Un entorno puede usarse para aplicar un conjunto de variables a un elemento `configuration`. Cada elemento de la matriz `environments` consta de lo siguiente:

- `namespace`: son los nombres de entorno, para que se pueda hacer referencia a sus variables desde una configuración con el formato `namespace.variable`. El objeto de entorno predeterminado se denomina `env` y se rellena con ciertas variables de entorno del sistema, entre las que se incluye `%USERPROFILE%`.
- `environment`: identifica de forma única este grupo de variables. Permite que el grupo se herede más adelante en una entrada `inheritEnvironments`.
- `groupPriority`: entero que especifica la prioridad de estas variables al evaluarlas. Los elementos con un número más alto se evalúan primero.
- `inheritEnvironments`: matriz de valores que especifican el conjunto de entornos que este grupo hereda. Se puede usar cualquier entorno personalizado, o bien los siguientes entornos predefinidos:
 
  - linux_arm: se destina a Linux ARM de forma remota.
  - linux_x64: se destina a Linux x64 de forma remota.
  - linux_x86: se destina a Linux x86 de forma remota.
  - msvc_arm: se destina a Windows ARM con el compilador de MSVC.
  - msvc_arm_x64: se destina a Windows ARM con el compilador de MSVC de 64 bits.
  - msvc_arm64: se destina a Windows ARM64 con el compilador de MSVC.
  - msvc_arm64_x64: se destina a Windows ARM64 con el compilador de MSVC de 64 bits.
  - msvc_x64: se destina a Windows x64 con el compilador de MSVC.
  - msvc_x64_x64: se destina a Windows x64 con el compilador de MSVC de 64 bits.
  - msvc_x86: se destina a Windows x86 con el compilador de MSVC.
  - msvc_x86_x64: se destina a Windows x86 con el compilador de MSVC de 64 bits.

## <a name="configurations"></a>Configuraciones

La matriz `configurations` consiste en una serie de objetos que representan las configuraciones de CMake que se aplican al archivo CMakeLists.txt en la misma carpeta. Puede usar estos objetos para definir varias configuraciones de compilación y cambiar fácilmente entre ellas en el IDE. 

Un elemento `configuration` tiene las siguientes propiedades:
- `name`: nombres de la configuración.
- `description`: descripción de esta configuración que aparecerá en los menús.
- `generator`: especifica el generador de CMake que se usará para esta configuración. Puede ser uno de los siguientes:

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Archivos Make Unix
  - Ninja

- `configurationType`: especifica la configuración del tipo de compilación del generador seleccionado. Puede ser uno de los siguientes:
 
  - Depuración
  - Release
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`: especifica uno o más entornos de los que depende esta configuración. Puede ser cualquier entorno personalizado, o bien uno de los entornos predefinidos.
- `buildRoot`: especifica el directorio en el que CMake genera los scripts de compilación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `installRoot`: especifica el directorio en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `cmakeCommandArgs`: especifica las opciones adicionales de la línea de comandos que se pasan a CMake cuando se invoca para generar la memoria caché.
- `cmakeToolchain`: especifica el archivo de la cadena de herramientas. Para pasarlo a CMake se usa -DCMAKE_TOOLCHAIN_FILE.
- `buildCommandArgs`: especifica los modificadores de compilación nativa que se pasan a CMake después de --build --.
- `ctestCommandArgs`: especifica opciones adicionales de la línea de comandos que se pasan a CTest al ejecutar las pruebas.
- `codeAnalysisRuleset`: especifica el conjunto de reglas que se usa al ejecutar el análisis de código. Puede ser una ruta de acceso completa o el nombre de un archivo de conjunto de reglas que Visual Studio ha instalado.
- `intelliSenseMode`: especifica el modo que se usa para calcular la información de IntelliSense. Puede ser uno de los siguientes:
 
  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm

- `cacheRoot`: especifica la ruta de acceso a una caché de CMake. El directorio debe contener un archivo CMakeCache.txt existente.
- `remoteMachineName`: especifica el nombre del equipo Linux remoto que hospeda CMake, compilaciones y el depurador. Use el Administrador de conexiones para agregar nuevas máquinas Linux. Entre las macros admitidas se incluye `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity`: especifica el nivel de detalle de la operación de copia de origen en la máquina remota. Puede ser " Normal", "Detallado" o "Diagnóstico".
- `remoteCopySourcesConcurrentCopies`: especifica el número de copias simultáneas que se usan durante la sincronización de los orígenes con la máquina remota.
- `remoteCopySourcesMethod`: especifica el método para copiar los archivos en la máquina remota. Puede ser "rsync" o "sftp".
- `remoteCMakeListsRoot`: especifica el directorio del equipo remoto que contiene el proyecto de CMake. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `remoteBuildRoot`: especifica el directorio de la máquina remota en el que CMake genera los scripts de compilación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `remoteInstallRoot`: especifica el directorio de la máquina remota en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`, donde `VARIABLE` es una variable de entorno que se ha definido en el nivel de sistema, usuario o sesión.
- `remoteCopySources`: `boolean` que especifica si Visual Studio debe copiar archivos de código fuente en el equipo remoto. El valor predeterminado es true. Establézcalo en false si administra usted mismo la sincronización de archivos.
- `remoteCopyBuildOutput`: `boolean` que especifica si deben copiarse las salidas de compilación del sistema remoto.
- `rsyncCommandArgs`: especifica un conjunto de opciones adicionales de la línea de comandos que se pasan a rsync.
- `remoteCopySourcesExclusionList`: `array` que especifica una lista de rutas de acceso que se van a excluir al copiar archivos de código fuente. Una ruta de acceso puede ser el nombre de un archivo o directorio, o bien una ruta relativa a la raíz de la copia. Los caracteres comodín \\\"*\\\" y \\\"?\\\" se pueden usar para la coincidencia de patrones globales.
- `cmakeExecutable`: especifica la ruta de acceso completa al ejecutable del programa CMake, incluidos el nombre y la extensión del archivo.
- `remotePreGenerateCommand`: especifica el comando que debe ejecutarse antes que CMake para analizar el archivo CMakeLists.txt.
- `remotePrebuildCommand`: especifica el comando que debe ejecutarse en la máquina remota antes de compilar.
- `remotePostbuildCommand`: especifica el comando que debe ejecutarse en la máquina remota después de compilar.
- `variables`: `array` que especifica las variables que se pasan a CMake como -Dname1=value1 -Dname2=value2, etc. 


