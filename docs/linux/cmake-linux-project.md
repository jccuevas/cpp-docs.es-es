---
title: Configuración de un proyecto CMake de Linux en Visual Studio
description: Cómo configurar, editar y compilar un proyecto CMake de Linux en Visual Studio
ms.date: 05/21/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: e2cda5e9b942342cca035c48054aadb5425b69cf
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182895"
---
# <a name="configure-a-linux-cmake-project"></a>Configuración de un proyecto de CMake de Linux

Cuando se abre una carpeta que contiene un proyecto de CMake, Visual Studio usa los metadatos que CMake genera para configurar IntelliSense y las compilaciones automáticamente. La configuración local y los ajustes de depuración se almacenan en archivos JSON, que opcionalmente se pueden compartir con otras personas que usan Visual Studio. 

Visual Studio no modifica los archivos CMakeLists.txt ni la caché original de CMake, de manera que las personas que trabajen en el mismo proyecto puedan seguir usando las herramientas que ya estén empleando.

Para obtener información general sobre la compatibilidad de CMake en Visual Studio, vea el artículo sobre las [herramientas de CMake para Visual Studio](../build/cmake-projects-in-visual-studio.md). Léalo antes de continuar aquí.

## <a name="before-you-begin"></a>Antes de empezar

En primer lugar, asegúrese de que tiene instalada la carga de trabajo de **desarrollo de Linux con C++**, incluido el componente de CMake. Vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

En el equipo Linux, asegúrese de tener instalado lo siguiente: 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

La compatibilidad de Linux con proyectos de CMake requiere tener instalada una versión reciente de CMake en el equipo de destino. A menudo, la versión ofrecida por el Administrador de paquetes predeterminado de distribución no es lo suficientemente reciente como para admitir todas las características del IDE. Visual Studio 2019 puede instalar automáticamente una copia local del usuario de CMake en equipos Linux remotos que no tienen instalada una versión reciente de CMake. Si no se detecta una versión compatible de CMake la primera vez que compile el proyecto, aparecerá una barra de información que le ofrece la posibilidad de instalar CMake.

Estos se instalarán en `~/.vs/cmake`. Después de su implementación, el proyecto se volverá a generar automáticamente. Tenga en cuenta que, si la versión de CMake especificada en el campo `cmakeExecutable` de `CMakeSettings.json` no es válida (no existe o es una versión no compatible) y los binarios creados previamente están presentes, Visual Studio ignorará `cmakeExecutable` y usará los binarios creados previamente.

::: moniker-end

::: moniker range="vs-2017"

La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

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
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Elija un destino de Linux

En cuanto se abre la carpeta, Visual Studio analiza el archivo CMakeLists.txt y especifica un destino de Windows de **x86-Debug**. Para establecer Linux como destino, cambie la configuración del proyecto a **Linux-Debug** o **Linux-Release**.

De forma predeterminada, Visual Studio elige el primer sistema remoto de la lista **Herramientas** > **Opciones** > **Multiplataforma** > **Administrador de conexiones**. Si no se encuentra ninguna conexión remota, se le pedirá que cree una. Para obtener más información, vea [Conectarse al equipo Linux remoto](connect-to-your-remote-linux-computer.md).

Después de especificar un destino de Linux, el origen se copia en su máquina Linux. A continuación, CMake se ejecuta en la máquina Linux para generar la caché de CMake del proyecto.

![Generar la caché de CMake en Linux](media/cmake-linux-1.png "Generar la caché de CMake en Linux")

Para proporcionar compatibilidad con IntelliSense para los encabezados remotos, Visual Studio los copia de manera automática del equipo Linux en un directorio en el equipo Windows local. Para obtener más información, vea [IntelliSense para los encabezados remotos](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Depurar el proyecto

Para depurar el código en el sistema remoto, establezca un punto de interrupción, seleccione el destino CMake como el elemento de inicio en el menú de barra de herramientas situado junto a la configuración del proyecto y haga elija **&#x23f5; Iniciar** en la barra de herramientas o presione F5.

Para personalizar los argumentos de la línea de comandos del programa, haga clic con el botón derecho en el archivo ejecutable en el **Explorador de soluciones** y seleccione **Configuración de depuración e inicio**. Esto abre o crea un archivo de configuración launch.vs.json que contiene información sobre el programa. Para especificar argumentos adicionales, agréguelos en la matriz de JSON `args`. Para obtener más información, vea [Open Folder projects for C++](../build/open-folder-projects-cpp.md) (Proyectos Abrir carpeta para C++) y [Configure CMake debugging sessions](../build/configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="configure-cmake-settings-for-linux"></a>Configuración de CMake para Linux

Un archivo CMakeSettings.json en un proyecto de CMake para Linux puede especificar todas las propiedades enumeradas en [Customize CMake settings](../build/customize-cmake-settings.md) (Personalización de la configuración de CMake), así como las propiedades adicionales que controlan la configuración de compilación del equipo Linux remoto. 

::: moniker range="vs-2019"

Para cambiar la configuración predeterminada de CMake en Visual Studio 2019, en la barra de herramientas principal, abra el menú desplegable **Configuración** y seleccione **Administrar configuraciones**. 

   ![Administrar configuraciones de CMake](../build/media/vs2019-cmake-manage-configurations.png "Menú desplegable de configuraciones de CMake")

Se abrirá el **Editor de configuración de CMake**, que puede usar para modificar el archivo `CMakeSettings.json` de la carpeta raíz del proyecto. También puede abrir el archivo directamente haciendo clic en el botón **Editar JSON** del editor. Para más información, vea [Personalización de la configuración de CMake](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Para cambiar la configuración predeterminada de CMake en Visual Studio 2017, elija **CMake | Cambiar configuración de CMake | CMakeLists.txt** en el menú principal, o haga clic con el botón derecho en CMakeSettings.txt en el **Explorador de soluciones** y elija **Cambiar configuración de CMake**. Después, Visual Studio crea un archivo `CMakeSettings.json` en la carpeta raíz del proyecto. Puede abrir el archivo mediante el editor de **configuración de CMake** o modificar el archivo directamente. Para obtener más información, vea [Personalización de la configuración de CMake](../build/customize-cmake-settings.md).

::: moniker-end

En el ejemplo siguiente se muestra la configuración predeterminada para Linux-Debug basada en el ejemplo de código anterior:

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
En la tabla siguiente se resumen los valores de configuración:

|Parámetro|Descripción|
|-----------|-----------------|
|`name`|Este valor puede ser el que quiera.|
|`remoteMachineName`|Especifica cuál será el sistema remoto de destino, si hay más de uno. IntelliSense está habilitado en este campo para que pueda seleccionar el sistema adecuado.|
|`remoteCMakeListsRoot`|Especifica dónde se copiarán los orígenes del proyecto en el sistema remoto.|
|`remoteBuildRoot`|Especifica dónde se generará la salida de la compilación en el sistema remoto. Esa salida también se copia en el sistema local en la ubicación especificada por `buildRoot`.|
|`remoteInstallRoot` y `installRoot`| Son similares a `remoteBuildRoot` y `buildRoot`, excepto que se aplican al realizar una instalación de CMake.|
|`remoteCopySources`|Especifica si se copian los orígenes locales en la máquina remota. Puede establecerlo en false si tiene muchos archivos y ya está sincronizando los orígenes.|
|`remoteCopyOutputVerbosity`| Especifica el nivel de detalle del paso de copia en caso de que necesite diagnosticar errores.|
|`remoteCopySourcesConcurrentCopies`| Especifica el número de procesos que se generan para realizar la copia.|
|`remoteCopySourcesMethod`| Puede ser `rsync` o `sftp`.|
|`remoteCopySourcesExclusionList`| Especifica los archivos que no quiere que se copien en el equipo remoto.|
|`rsyncCommandArgs`|Controla el método rsync para copiar.|
|`remoteCopyBuildOutput`| Controla si se copia la salida de compilación remota en la carpeta de compilación local.|

Puede usar estos valores opcionales para tener un mayor control:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Estas opciones permiten ejecutar comandos en el sistema remoto antes y después de compilar, y antes de la generación de CMake. Los valores pueden ser cualquier comando válido en el sistema remoto. La salida se canaliza de nuevo a Visual Studio.

::: moniker range="vs-2019"

En Visual Studio de 2019 puede editar todas estas configuraciones en el **Editor de configuración de CMake**.

::: moniker-end

## <a name="see-also"></a>Vea también

[Trabajar con configuraciones de proyecto](../build/working-with-project-properties.md)<br/>
[Proyectos de CMake en Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
[Conexión al equipo remoto de Linux](connect-to-your-remote-linux-computer.md)<br/>
[Personalización de la configuración de CMake](../build/customize-cmake-settings.md)<br/>
[Configuración de sesiones de depuración de CMake](../build/configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](../build/cmake-predefined-configuration-reference.md)<br/>
