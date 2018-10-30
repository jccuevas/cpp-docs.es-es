---
title: Configuración de un proyecto de CMake de Linux en Visual Studio | Microsoft Docs
description: Cómo configurar un proyecto CMake de Linux en Visual Studio
ms.custom: ''
ms.date: 07/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: b7c28a8e67ef2731d26071262383e93d32be9583
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064113"
---
# <a name="configure-a-linux-cmake-project"></a>Configuración de un proyecto de CMake de Linux

**Visual Studio 2017, versión 15.4 y posteriores**<br/>
Al instalar la carga de trabajo C++ de Linux para Visual Studio, se activa de forma predeterminada la compatibilidad de CMake con Linux. Ya puede trabajar en la base de código existente que utiliza CMake sin tener que convertirla en un proyecto de Visual Studio. Si la base de código es multiplataforma, puede tener como destino Windows y Linux desde dentro de Visual Studio.

En este tema se da por supuesto que tiene conocimientos básicos de la compatibilidad de CMake en Visual Studio. Para obtener más información, consulte [Herramientas de CMake para Visual C++](../ide/cmake-tools-for-visual-cpp.md). Para obtener más información sobre el propio CMake, vea [Build, Test and Package Your Software With CMake](https://cmake.org/) (Compilar, probar y empaquetar con CMake).

> [!NOTE]
> La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

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

De forma predeterminada, Visual Studio elige el primer sistema remoto de la lista **Herramientas** > **Opciones** > **Multiplataforma** > **Administrador de conexiones**. Si no se encuentra ninguna conexión remota, se le pedirá que cree una.

Después de especificar un destino de Linux, el origen se copia en su máquina Linux. A continuación, CMake se ejecuta en la máquina Linux para generar la caché de CMake del proyecto.

![Generar la caché de CMake en Linux](media/cmake-linux-1.png "Generar la caché de CMake en Linux")

**Visual Studio 2017, versión 15.7 y posteriores:**<br/>
Para proporcionar compatibilidad con IntelliSense para los encabezados remotos, Visual Studio los copia de manera automática en un directorio en el equipo Windows local. Para obtener más información, vea [IntelliSense para los encabezados remotos](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-project"></a>Depurar el proyecto

Para depurar el código en el sistema remoto, establezca un punto de interrupción, seleccione el destino CMake como el elemento de inicio en el menú de barra de herramientas situado junto a la configuración del proyecto y haga elija **&#x23f5; Iniciar** en la barra de herramientas o presione F5.

Para personalizar los argumentos de la línea de comandos del programa, haga clic con el botón derecho en el archivo ejecutable en el **Explorador de soluciones** y seleccione **Configuración de depuración e inicio**. Esto abre o crea un archivo de configuración launch.vs.json que contiene información sobre el programa. Para especificar argumentos adicionales, agréguelos en la matriz de JSON `args`. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](../ide/non-msbuild-projects.md).

## <a name="configure-cmake-settings-for-linux"></a>Configuración de CMake para Linux

Para cambiar la configuración predeterminada de CMake, elija **CMake | Cambiar configuración de CMake | CMakeLists.txt** en el menú principal, o haga clic con el botón derecho en CMakeSettings.txt en el **Explorador de soluciones** y elija **Cambiar configuración de CMake**. A continuación, Visual Studio crea un archivo en la carpeta denominado `CMakeSettings.json` que se rellena con las configuraciones predeterminadas que se muestran en el elemento de menú de configuración de proyecto. En el ejemplo siguiente se muestra la configuración predeterminada para Linux-Debug basada en el ejemplo de código anterior:

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

El valor `name` puede ser el que quiera. El valor `remoteMachineName` especifica cuál será el sistema remoto de destino, si hay más de uno. IntelliSense está habilitado en este campo para que pueda seleccionar el sistema adecuado. El campo `remoteCMakeListsRoot` especifica donde se copiarán los orígenes del proyecto en el sistema remoto. El campo `remoteBuildRoot` es donde se generará la salida de la compilación en el sistema remoto. Esa salida también se copia en el sistema local en la ubicación especificada por `buildRoot`. Los campos `remoteInstallRoot` y `installRoot` son similares a `remoteBuildRoot` y `buildRoot`, excepto que se aplican al realizar una instalación de cmake. La entrada `remoteCopySources` controla si se copian los orígenes locales en la máquina remota. Puede establecerlo en false si tiene una gran cantidad de archivos y ya está sincronizando los orígenes. El valor `remoteCopyOutputVerbosity` controla el nivel de detalle del paso de copia en caso de que necesite diagnosticar errores. La entrada `remoteCopySourcesConcurrentCopies` controla el número de procesos que se generan para realizar la copia. El valor `remoteCopySourcesMethod` puede ser rsync o sftp. El campo `remoteCopySourcesExclusionList` permite controlar lo que debe copiarse en la máquina remota. El valor `rsyncCommandArgs` permite controlar el método rsync para copiar. El campo `remoteCopyBuildOutput` controla si se copia la salida de compilación remota en la carpeta de compilación local.

También hay algunos valores de configuración opcionales que puede usar para tener más control:

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

Estas opciones permiten ejecutar comandos en el cuadro de diálogo remoto antes y después de compilar, y antes de la generación de CMake. Puede ser cualquier comando válido en el cuadro de diálogo remoto. El resultado se canaliza de nuevo a Visual Studio.

## <a name="download-prebuilt-cmake-binaries"></a>Descarga de archivos binarios CMake creados previamente

La distribución de Linux puede tener una versión anterior de CMake. La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).

## <a name="see-also"></a>Vea también

[Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)<br/>
[Herramientas de CMake para Visual C++](../ide/cmake-tools-for-visual-cpp.md)
