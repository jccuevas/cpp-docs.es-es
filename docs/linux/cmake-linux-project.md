---
title: Configuración de un proyecto CMake de Linux en Visual Studio
description: Cómo configurar un proyecto CMake de Linux en Visual Studio
ms.date: 11/01/2018
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: f2186c14fbe2eb1273fceb4a378b359564eae327
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750603"
---
# <a name="configure-a-linux-cmake-project"></a>Configuración de un proyecto de CMake de Linux

Cuando se abre una carpeta que contiene un proyecto de CMake, Visual Studio usa los metadatos que CMake genera para configurar IntelliSense y las compilaciones automáticamente. La configuración local y los ajustes de depuración se almacenan en archivos JSON, que opcionalmente se pueden compartir con otras personas que usan Visual Studio. 

Visual Studio no modifica los archivos CMakeLists.txt ni la caché original de CMake, de manera que las personas que trabajen en el mismo proyecto puedan seguir usando las herramientas que ya estén empleando.  

## <a name="before-you-begin"></a>Antes de empezar

En primer lugar, asegúrese de que tiene instalada la carga de trabajo de **desarrollo de Linux con C++**, incluido el componente de CMake. Vea [Instalación de la carga de trabajo de Linux para C++ en Visual Studio](download-install-and-setup-the-linux-development-workload.md). 

La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

En este tema se da por supuesto que ha leído [CMake Tools for Visual Studio](../ide/cmake-tools-for-visual-cpp.md) (Herramientas de CMake para Visual Studio). 

> [!NOTE]
> La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases). En Visual Studio 2019, los binarios creados previamente pueden implementarse automáticamente (vea [Descarga de archivos binarios CMake creados previamente](#download-prebuilt-cmake-binaries)).

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

**Visual Studio 2017, versión 15.7 y posteriores:**<br/>
Para proporcionar compatibilidad con IntelliSense para los encabezados remotos, Visual Studio los copia de manera automática del equipo Linux en un directorio en el equipo Windows local. Para obtener más información, vea [IntelliSense para los encabezados remotos](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Depurar el proyecto

Para depurar el código en el sistema remoto, establezca un punto de interrupción, seleccione el destino CMake como el elemento de inicio en el menú de barra de herramientas situado junto a la configuración del proyecto y haga elija **&#x23f5; Iniciar** en la barra de herramientas o presione F5.

Para personalizar los argumentos de la línea de comandos del programa, haga clic con el botón derecho en el archivo ejecutable en el **Explorador de soluciones** y seleccione **Configuración de depuración e inicio**. Esto abre o crea un archivo de configuración launch.vs.json que contiene información sobre el programa. Para especificar argumentos adicionales, agréguelos en la matriz de JSON `args`. Para obtener más información, vea [Open Folder projects in Visual C++](../ide/non-msbuild-projects.md) (Proyectos Abrir carpeta en Visual C++) y [Configure CMake debugging sessions](../ide/configure-cmake-debugging-sessions.md) (Configuración de sesiones de depuración de CMake).

## <a name="configure-cmake-settings-for-linux"></a>Configuración de CMake para Linux

Un archivo CMakeSettings.json en un proyecto de CMake para Linux puede especificar todas las propiedades enumeradas en [Customize CMake settings](../ide/customize-cmake-settings.md) (Personalización de la configuración de CMake), así como las propiedades adicionales que controlan la configuración de compilación del equipo Linux remoto. Para cambiar la configuración predeterminada de CMake, elija **CMake | Cambiar configuración de CMake | CMakeLists.txt** en el menú principal, o haga clic con el botón derecho en CMakeSettings.txt en el **Explorador de soluciones** y elija **Cambiar configuración de CMake**. Después, Visual Studio crea un archivo `CMakeSettings.json` en la carpeta raíz del proyecto. Puede abrir el archivo mediante el editor de **configuración de CMake** o modificar el archivo directamente. 

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
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Estas opciones permiten ejecutar comandos en el sistema remoto antes y después de compilar, y antes de la generación de CMake. Los valores pueden ser cualquier comando válido en el sistema remoto. La salida se canaliza de nuevo a Visual Studio.

## <a name="download-prebuilt-cmake-binaries"></a>Descarga de archivos binarios CMake creados previamente

La distribución de Linux puede tener una versión anterior de CMake. La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

**Visual Studio 2019**<br/>
Si no se encuentra una versión válida de CMake en la máquina remota, se mostrará una barra de información y se proporcionará una opción para implementar automáticamente los binarios de CMake creados previamente. Estos se instalarán en `~/.vs/cmake`. Después de su implementación, el proyecto se volverá a generar automáticamente. Tenga en cuenta que, si la versión de CMake especificada en el campo `cmakeExecutable` de `CMakeSettings.json` no es válida (no existe o es una versión no compatible) y los binarios creados previamente están presentes, Visual Studio ignorará `cmakeExecutable` y usará los binarios creados previamente.

## <a name="see-also"></a>Vea también

[Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)<br/>
[Herramientas de CMake para Visual C++](../ide/cmake-tools-for-visual-cpp.md)<br/>
[Conexión al equipo remoto de Linux](connect-to-your-remote-linux-computer.md)<br/>
[Personalización de la configuración de CMake](../ide/customize-cmake-settings.md)<br/>
[Configuración de sesiones de depuración de CMake](../ide/configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](../ide/cmake-predefined-configuration-reference.md)<br/>
