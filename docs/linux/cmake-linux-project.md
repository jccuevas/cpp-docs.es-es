---
title: Creación y configuración de un proyecto de CMake de Linux en Visual Studio
description: Cómo crear, configurar, editar y compilar un proyecto de CMake de Linux en Visual Studio
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 9c6a60162c2dbbab8e348b27d1987d7f1001bee0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79429191"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Creación y configuración de un proyecto de CMake en Linux

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range="vs-2019"

Para crear un proyecto de CMake de Linux en Visual Studio 2019:

1. Seleccione **Archivo > Nuevo proyecto** en Visual Studio o pulse **Ctrl + Mayús + N**.
1. Establezca **Lenguaje** en **C++** y busque "CMake". Después, seleccione **Siguiente**. Especifique un **Nombre** y una **Ubicación** y elija **Crear**.

Visual Studio crea un archivo CMakeLists.txt mínimo con solo el nombre del ejecutable y la versión mínima de CMake necesaria. Puede editar manualmente este archivo como quiera; Visual Studio nunca sobrescribirá los cambios. Puede especificar variables de entorno y argumentos de línea de comandos de CMake haciendo clic con el botón derecho en el archivo CMakeLists.txt raíz, en el **Explorador de soluciones** y eligiendo **Configuración de CMake para el proyecto**. Para especificar opciones de depuración, haga clic con el botón derecho en el nodo del proyecto y elija **Configuración de depuración e inicio**.

::: moniker-end

Cuando se abre una carpeta que contiene un proyecto de CMake, Visual Studio usa las variables de la memoria caché de CMake para configurar IntelliSense y las compilaciones automáticamente. La configuración local y los ajustes de depuración se almacenan en archivos JSON, que opcionalmente se pueden compartir con otras personas que usan Visual Studio.

Visual Studio no modifica los archivos CMakeLists.txt, de manera que las personas que trabajen en el mismo proyecto puedan seguir usando las herramientas que ya estén empleando. Visual Studio vuelve a generar la memoria caché al guardar modificaciones en el archivo CMakeLists.txt o, en algunos casos, en CMakeSettings.json. Sin embargo, si usa una configuración **Caché existente**, Visual Studio no modificará la caché.

Para obtener información general sobre la compatibilidad de CMake en Visual Studio, vea el artículo sobre los [proyectos de CMake para Visual Studio](../build/cmake-projects-in-visual-studio.md). Léalo antes de continuar aquí.

## <a name="before-you-begin"></a>Antes de empezar

En primer lugar, asegúrese de que tiene instalada la carga de trabajo de **desarrollo de Linux con C++** , incluido el componente de CMake. Vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

En el sistema Linux, asegúrese de tener instalado lo siguiente: 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

La compatibilidad de Linux con proyectos de CMake requiere tener instalada una versión reciente de CMake en el equipo de destino. A menudo, la versión ofrecida por el Administrador de paquetes predeterminado de distribución no es lo suficientemente reciente como para admitir todas las características que Visual Studio requiere. Visual Studio 2019 detecta si hay una versión reciente de CMake instalada en el sistema Linux. Si no encuentra ninguna, muestra una barra de información encima del panel del editor que ofrece la posibilidad de instalarlo desde [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. En Visual Studio, se recomienda Visual Studio 2019 versión 3.14 o posterior.

::: moniker-end

::: moniker range="vs-2017"

La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

Estos se instalarán en `~/.vs/cmake`. Después de su implementación, el proyecto se volverá a generar automáticamente. Tenga en cuenta que, si la versión de CMake especificada en el campo `cmakeExecutable` de `CMakeSettings.json` no es válida (no existe o es una versión no compatible) y los binarios creados previamente están presentes, Visual Studio ignorará `cmakeExecutable` y usará los binarios creados previamente.

:::moniker-end

## <a name="open-a-folder"></a>Abrir una carpeta

Para empezar, elija **Archivo** > **Abrir** > **Carpeta** en el menú principal, o bien escriba `devenv.exe <foldername>` en la línea de comandos. La carpeta que abra debe contener un archivo CMakeLists.txt, junto con el código fuente.
En el ejemplo siguiente se muestra un archivo CMakeLists.txt simple y un archivo .cpp:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt:

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Elija un destino de Linux

En cuanto se abre la carpeta, Visual Studio analiza el archivo CMakeLists.txt y especifica un destino de Windows de **x86-Debug**. Para establecer un sistema Linux remoto como destino, cambie la configuración del proyecto a **Linux-Debug** o **Linux-Release**. Consulte [Configuración de CMake para Linux](#configure_cmake_linux) a continuación.

::: moniker range="vs-2019"

Para establecer el subsistema de Windows para Linux como destino, haga clic en **Administrar configuraciones** en la lista desplegable de configuración en la barra de herramientas principal. Luego, pulse el botón **Agregar configuración** y elija **WSL-Debug** o **WSL-Release** si usa GCC, o bien las variantes de Clang correspondientes si usa el conjunto de herramientas de Clang/LLVM. 

**Visual Studio 2019 versión 16.1** Cuando se establece WSL como destino, no es necesario copiar nada ni disponer de orígenes o encabezados, porque el compilador de Linux tiene acceso directo al sistema de archivos de Windows donde están los archivos de origen. En la versión de Windows 1903 y posterior, las aplicaciones de Windows del mismo modo pueden tener acceso a los archivos de encabezado de Linux directamente, pero Visual Studio aún no aprovecha esta funcionalidad.

::: moniker-end

Si el destino es remoto, Visual Studio elige de forma predeterminada el primer sistema remoto que figura en la lista **Herramientas** > **Opciones** > **Multiplataforma** > **Administrador de conexiones**. Si no se encuentra ninguna conexión remota, se le pedirá que cree una. Para obtener más información, vea [Conectarse al equipo Linux remoto](connect-to-your-remote-linux-computer.md).

Después de especificar un destino de Linux remoto, el origen se copia en el sistema remoto.

Después de seleccionar un destino, CMake se ejecuta automáticamente en el sistema Linux para generar la memoria caché de CMake correspondiente al proyecto. 

![Generar la caché de CMake en Linux](media/cmake-linux-1.png "Generar la caché de CMake en Linux")

Para proporcionar compatibilidad con IntelliSense para los encabezados en sistemas Linux remotos, Visual Studio los copia de manera automática del equipo Linux en un directorio en el equipo Windows local. Para obtener más información, vea [IntelliSense para los encabezados remotos](configure-a-linux-project.md#remote_intellisense).

## <a name="debug_cmake_project"></a> Depuración del proyecto de CMake

Para depurar el código en el sistema de destino de depuración especificado, establezca un punto de interrupción, seleccione el destino CMake como el elemento de inicio en el menú de barra de herramientas situado junto a la configuración del proyecto y elija **&#x23f5; Iniciar** en la barra de herramientas (o presione F5).

Para personalizar los argumentos de línea de comandos del programa, pulse el botón **Switch Targets** (Cambiar destinos) situado en la parte superior del **Explorador de soluciones** y, a continuación, elija **Vista de destinos**. Haga clic con el botón derecho en el destino y seleccione **Configuración de depuración e inicio**. Esto abre o crea un archivo de configuración launch.vs.json que contiene información sobre el programa. Para especificar la ubicación de los archivos de origen, agregue una propiedad **sourceFileMap** al archivo, tal como se muestra en este ejemplo:

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Para especificar argumentos adicionales, agréguelos en la matriz de JSON `args`. Para obtener más información, vea [Open Folder projects for C++](../build/open-folder-projects-cpp.md) (Proyectos Abrir carpeta para C++) y [Configure CMake debugging sessions](../build/configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="configure_cmake_linux"></a> Configuración de CMake para Linux

Un archivo CMakeSettings.json en un proyecto de CMake para Linux puede especificar todas las propiedades enumeradas en [Customize CMake settings](../build/customize-cmake-settings.md) (Personalización de la configuración de CMake), así como las propiedades adicionales que controlan la configuración de compilación del equipo Linux remoto. 

::: moniker range="vs-2019"

Para cambiar la configuración predeterminada de CMake en Visual Studio 2019, en la barra de herramientas principal, abra el menú desplegable **Configuración** y seleccione **Administrar configuraciones**. 

![Administrar configuraciones de CMake](../build/media/vs2019-cmake-manage-configurations.png "Lista desplegable de configuraciones de CMake")

Se abrirá el **Editor de configuración de CMake**, que puede usar para modificar el archivo `CMakeSettings.json` de la carpeta raíz del proyecto. También puede abrir el archivo directamente haciendo clic en el botón **Editar JSON** del editor. Para más información, vea [Personalización de la configuración de CMake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Para cambiar la configuración predeterminada de CMake en Visual Studio 2017, elija **CMake | Cambiar configuración de CMake | CMakeLists.txt** en el menú principal, o haga clic con el botón derecho en CMakeSettings.txt en el **Explorador de soluciones** y elija **Cambiar configuración de CMake**. Después, Visual Studio crea un archivo `CMakeSettings.json` en la carpeta raíz del proyecto. Puede abrir el archivo mediante el editor de **configuración de CMake** o modificar el archivo directamente. Para obtener más información, vea [Personalización de la configuración de CMake](../build/customize-cmake-settings.md).

En el ejemplo siguiente se muestra la configuración predeterminada para Linux-Debug en Visual Studio 2017 (y en Visual Studio 2019 versión 16.0) basada en el ejemplo de código anterior:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range="vs-2019"

La configuración Linux-Debug predeterminada en Visual Studio 2019 versión 16.1 y posterior es como se muestra aquí:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```
::: moniker-end

Para obtener más información sobre estos valores, consulte la [referencia de CMakeSettings.json](../build/cmakesettings-reference.md).


## <a name="optional-settings"></a>Configuración opcional

Puede usar los siguientes valores opcionales para tener un mayor control:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Estas opciones permiten ejecutar comandos en el sistema Linux antes y después de compilar, y antes de la generación de CMake. Los valores pueden ser cualquier comando válido en el sistema remoto. La salida se canaliza de nuevo a Visual Studio.



## <a name="see-also"></a>Vea también

[Trabajar con configuraciones de proyecto](../build/working-with-project-properties.md)<br/>
[Proyectos de CMake en Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Conexión al equipo remoto de Linux](connect-to-your-remote-linux-computer.md)<br/>
[Personalización de la configuración de CMake](../build/customize-cmake-settings.md)<br/>
[Configuración de sesiones de depuración de CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](../build/cmake-predefined-configuration-reference.md)<br/>
