---
title: "Configuración de un proyecto de CMake de Linux en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2107
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 67665f3271caf71d16788b2e102d0e756d9f702f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="configure-a-linux-cmake-project"></a>Configuración de un proyecto de CMake de Linux
  
**Visual Studio 2017 versión 15.4** Cuando se instala la carga de trabajo de C++ de Linux, se activa de forma predeterminada la compatibilidad de CMake con Linux. Ya puede trabajar en la base de código existente que utiliza CMake sin tener que convertirla en un proyecto de Visual Studio. Si la base de código es multiplataforma, puede tener como destino Windows y Linux desde dentro de Visual Studio. 

En este tema se da por supuesto que tiene conocimientos básicos de la compatibilidad de CMake en Visual Studio. Para obtener más información, consulte [Herramientas de CMake para Visual C++](../ide/cmake-tools-for-visual-cpp.md). Para obtener más información sobre el propio CMake, vea [Build, Test and Package Your Software With CMake](https://cmake.org/) (Compilar, probar y empaquetar con CMake).

> [!NOTE] 
> La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Si el administrador de paquetes proporciona una versión anterior de CMake, puede compilar CMake 3.8 a partir del origen.



## <a name="open-a-folder"></a>Abrir una carpeta
Para empezar, elija **Archivo | Abrir | Carpeta** en el menú principal, o bien escriba `devenv.exe <foldername>` en la línea de comandos. La carpeta que abra debe contener un archivo CMakeLists.txt, junto con el código fuente.
En el ejemplo siguiente se muestra un archivo CMakeLists.txt simple y un archivo .cpp:

```cpp
// Hello.cpp

#include <iostream>;
 
int main(int argc, char* argv[])
{
    std::cout << "Hello" << std::endl;
}
```

CMakeLists.txt: 
```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Elija un destino de Linux
En cuanto se abre la carpeta, Visual Studio analiza el archivo CMakeLists.txt y especifica un destino de Windows de x86-Debug. Para establecer Linux como destino, cambie la configuración del proyecto a Linux-Debug o Linux-Release.

De forma predeterminada, Visual Studio elige el primer sistema remoto de la lista (en **Herramientas | Opciones | Multiplataforma | Administrador de conexiones**). Si no se encuentra ninguna conexión remota, se le pedirá que cree una.

Después de especificar un destino de Linux, el origen se copia en su máquina Linux. A continuación, CMake se ejecuta en la máquina Linux para generar la caché de CMake del proyecto.  

![Generar la caché de CMake en Linux](media/cmake-linux-1.png "Generar la caché de CMake en Linux")  

## <a name="debug-the-project"></a>Depurar el proyecto  
Para depurar el código en el sistema remoto, establezca un punto de interrupción, seleccione el destino CMake como el elemento de inicio en el menú de barra de herramientas situado junto a la configuración del proyecto y haga clic en ejecutar (o presione F5).

## <a name="configure-cmake-settings-for-linux"></a>Configurar CMake para Linux
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
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```
El valor `name` puede ser el que quiera. El valor `remoteMachineName` especifica cuál será el sistema remoto de destino, si hay más de uno. IntelliSense está habilitado en este campo para que pueda seleccionar el sistema adecuado. El campo `remoteCMakeListsRoot` especifica donde se copiarán los orígenes del proyecto en el sistema remoto. El campo `remoteBuildRoot` es donde se generará la salida de la compilación en el sistema remoto. Esa salida también se copia en el sistema local en la ubicación especificada por `buildRoot`.

## <a name="building-a-supported-cmake-release-from-source"></a>Compilación de una versión compatible de CMake a partir del origen
La versión mínima de CMake necesaria en su máquina Linux es la 3.8. También debe admitir el modo servidor. Para comprobar esta condición, ejecute este comando:

```cmd
cmake --version
```

Para comprobar que el modo de servidor está habilitado, ejecute:

```cmd
cmake -E capabilities
```

En la salida, busque "serverMode":true. Tenga en cuenta que aunque compile CMake a partir del origen tal y como se describe a continuación, debe comprobar las capacidades cuando haya finalizado. El sistema Linux puede tener limitaciones que impidan la habilitación del modo servidor.

Para empezar a compilar desde el origen en el shell de su sistema Linux, asegúrese de que el administrador de paquetes está actualizado y que git y cmake están disponibles. En primer lugar, clone los orígenes de CMake:

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Kitware/CMake.git
cd CMake
```

A continuación, asegúrese de que se encuentra en una versión compatible de CMake para Visual Studio. Si bien realizamos un seguimiento activo del desarrollo de CMake, no es posible garantizar la compatibilidad con la versión más reciente. Para compilar CMake 3.9.0 (por ejemplo), primero ejecute:

```cmd
git checkout tags/v3.9.0
```

A continuación, ejecute los siguientes comandos:

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

Los comandos anteriores compilan e instalan la versión actual de CMake en /usr/local/bin. Ejecute este comando para comprobar que la versión es >=3.8 y que el modo servidor está habilitado:

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>Vea también
[Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)  
[Herramientas de CMake para Visual C++](../ide/cmake-tools-for-visual-cpp.md)