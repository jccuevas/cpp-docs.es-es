---
title: CMake proyectos en Visual C++ | Documentos de Microsoft
ms.custom: 
ms.date: 08/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 770b7f70e52859b1489b984d8aef3c3876a9ca83
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="cmake-projects-in-visual-c"></a>CMake proyectos en Visual C++
En este artículo se da por supuesto que está familiarizado con CMake, una herramienta multiplataforma de código abierto para definir procesos de compilación que se ejecutan en varias plataformas.  

Hasta hace poco, los usuarios de Visual Studio pudieron utilizar CMake para generar archivos de proyecto de MSBuild, que, a continuación, usar el IDE para que IntelliSense, exploración y compilación. A partir de Visual Studio 2017 el **herramientas de Visual C++ para CMake** componente usa la característica de "Abrir carpeta" para habilitar el IDE consumir archivos de proyecto de CMake (por ejemplo, CMakeLists.txt) directamente para los fines de IntelliSense y la exploración. Si utiliza un generador de Visual Studio, un archivo de proyecto temporal se genera y se pasa a msbuild.exe, pero nunca está cargado para IntelliSense o con fines de exploración. 

**Visual Studio 2017 versión 15.3**: se admiten para los generadores de Ninja y Visual Studio.

**Visual Studio 2017 versión 15.4**: se agregó compatibilidad con CMake en Linux. Para obtener más información, consulte [configurar un proyecto de CMake Linux](../linux/cmake-linux-project.md).

## <a name="installing"></a>Instalación
Herramientas de Visual C++ para CMake se instala de forma predeterminada como parte del desarrollo de escritorio con cargas de trabajo de C++.

![Componente de CMake de carga de trabajo de escritorio de C++](media/cmake-install.png)
 
## <a name="ide-integration"></a>Integración de IDE
Cuando eliges **archivo | Abra | Carpeta** para abrir una carpeta que contiene un archivo CMakeLists.txt, sucede lo siguiente:
- Visual Studio agrega un **CMake** elemento de menú al menú principal, con los comandos para ver y editar scripts CMake. 
- **El Explorador de soluciones** muestra la estructura de carpetas y archivos. 
- Visual Studio se ejecuta CMake.exe y genera la caché de CMake para el valor predeterminado *configuración*, que es x86 depurar. La línea de comandos de CMake se muestra en el **ventana de salida**, junto con una salida adicional de CMake.
- En segundo plano, Visual Studio inicia para indiza los archivos de origen para habilitar IntelliSense, información de exploración, refactorización y así sucesivamente. Mientras trabaja, Visual Studio controla los cambios en el editor y también en el disco para mantener sincronizados con los orígenes de su índice. Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos de CMakeLists.txt "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar, depurar) así como IntelliSense de C++ y exploración están disponibles para todos los proyectos de CMake en el área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png) 

## <a name="building-cmake-projects"></a>Compilar proyectos de CMake
Para compilar un proyecto CMake, tienes estas opciones:
1. Seleccione el destino en la lista desplegable de depuración y presione **F5** o haga clic en el botón "Ejecutar". Configurará automáticamente y el proyecto de compilación en primer lugar, al igual que con las soluciones de Visual Studio.
2.  Haga clic con el botón secundario en el CMakeLists.txt y seleccione la compilación en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilar todos o sólo un destino específico, o
  
3. En el menú principal, seleccione **compilar | Compilar solución** (**F7** o **Ctrl + Mayús + B**) (asegúrese de que un destino CMake ya está seleccionado en el **elemento de inicio** lista desplegable en el **General** barra de herramientas).

![Comando de menú de compilación CMake](media/cmake-build-menu.png) 
 
Cuando se selecciona un generador de Visual Studio para la configuración activa, se invoca MSBuild.exe con `-m -v:minimal` argumentos. Para personalizar la compilación, en el archivo CMakeSettings.json, puede especificar argumentos de línea de comandos adicionales que se pasarán al sistema de compilación a través de la `buildCommandArgs` propiedad:

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```
Como cabría esperar, los resultados de la compilación se muestran en la **ventana de salida** y **lista de errores**.
 
![Errores de compilación CMake](media/cmake-build-errors.png)

En una carpeta con varios destinos de compilación, puede elegir el elemento de compilación en el menú CMake o el menú contextual de CMakeLists.txt para especificar qué destino CMake para compilar. Al presionar **Ctrl + Mayús + B** en un CMake las compilaciones de proyecto del documento activo actual. 

## <a name="debugging-the-project"></a>Depurar el proyecto
Para depurar un proyecto de CMake, elija la configuración deseada y presione **F5**, o bien presione el botón ejecutar en la barra de herramientas. Si el botón ejecutar dice "Seleccionar elemento de inicio", haga clic en la flecha hacia abajo y seleccione el destino que se va a ejecutar. (En un proyecto de CMake, el "documento actual" opción solo es válida para los archivos .cpp.) 

 ![Botón CMake ejecutar](media/cmake-run-button.png)

 Al presionar **F5** generará primero el proyecto si se han realizado cambios desde la compilación anterior.

## <a name="configuring-cmake-debugging-sessions"></a>Configurar CMake las sesiones de depuración
Todos los destinos CMake ejecutables se muestran en la lista desplegable de elemento de inicio en la barra de herramientas General. Para iniciar una sesión de depuración, seleccione uno e iniciar al depurador.

 ![Lista desplegable de elemento de inicio de CMake](media/cmake-startup-item-dropdown.png)

También puede iniciar una sesión de depuración de los menús de CMake.

Para personalizar la configuración del depurador para cualquier destino CMake ejecutable en el proyecto, haga doble clic en el archivo específico que CMakeLists.txt y seleccione **iniciar configuración y depuración**, cuando se selecciona un destino de CMake en el submenú, un archivo denominado se crea Launch.VS.JSON. Este archivo se ha rellenado previamente con información acerca del destino de CMake que ha seleccionado y le permite especificar parámetros adicionales como argumentos de programa o el tipo de depurador. Para hacer referencia a cualquier clave en un archivo CMakeSettings.json, comenzar con "cmake." en launch.vs.json. En el ejemplo siguiente se muestra un archivo de launch.vs.json simple que extrae el valor de la clave "remoteCopySources" en el archivo CMakeSettings.json para la configuración seleccionada actualmente:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
   {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```
Tan pronto como guardar el archivo launch.vs.json, se crea una entrada en la lista desplegable de elemento de inicio con el nuevo nombre. Al editar el archivo launch.vs.json, puede crear como muchas configuraciones de depuración como sea necesario para cualquier número de destinos de CMake.

**Visual Studio 2017 versión 15.4**: Launch.vs.json admite las variables que se declaran en CMakeSettings.json (ver abajo). También tiene un concepto de la "currentDir," que se establecerá como el directorio actual de la aplicación inicial:

```json
{
"type": "default",
"project": "CMakeLists.txt",
"projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```
Al ejecutar la aplicación, el valor de `currentDir` es 

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```
 

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos de CMakeLists.txt
Para editar un archivo CMakeLists.txt, haga clic en el archivo en **el Explorador de soluciones** y elija **abiertos**. Si realiza cambios en el archivo, una barra de estado amarillo aparece y le informa que IntelliSense actualizará y le da una oportunidad para cancelar la operación de actualización. Para obtener información sobre CMakeLists.txt, consulte el [CMake documentación](https://cmake.org/documentation/).

  ![Edición de archivos de CMakeLists.txt](media/cmake-cmakelists.png)

Tan pronto como se guarda el archivo, el paso de configuración automáticamente se vuelva a ejecutar y mostrar información en la ventana de salida. Errores y advertencias se muestran en la lista de errores o la ventana de salida. Haga doble clic en un error en la lista de errores para navegar a la línea incorrecta en CMakeLists.txt.

  ![Errores de archivo CMakeLists.txt](media/cmake-cmakelists-error.png)
 
## <a name="cmake_settings"></a>Configuración de CMake y las configuraciones personalizadas
De forma predeterminada, Visual Studio proporciona seis configuraciones de CMake predeterminado ("x86-Debug", "x86-Release", "x64-Debug", "x64-Release", "Linux-Debug" y "Versión de Linux"). Estas configuraciones definen cómo se invoca CMake.exe para crear una caché CMake para un proyecto determinado. Para modificar estas configuraciones, o crear una nueva configuración personalizada, elija **CMake | Cambiar configuración de CMake**y, a continuación, elija el archivo CMakeLists.txt que se aplicará la configuración. Cambiar la configuración de CMake también está disponible en el menú contextual del archivo en **el Explorador de soluciones**. Este comando crea un archivo CMakeSettings.json en la carpeta del proyecto. Este archivo se usa para volver a crear el archivo de caché CMake, por ejemplo después de una operación "Limpia". 

  ![Comando de menú principal de CMake para cambiar la configuración](media/cmake-change-settings.png)
 
JSON IntelliSense le ayuda a editar el archivo CMakeSettings.json:

   ![IntelliSense CMake JSON](media/cmake-json-intellisense.png)

En el ejemplo siguiente se muestra un ejemplo de configuración, que puede usar como punto de partida para crear sus propios en CMakeSettings.json:
```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```
1.  nombre: el nombre que aparecerá en la lista desplegable de configuración de C++. Valor de esta propiedad también puede utilizarse como una macro `${name}` para especificar otros valores de propiedad. Para obtener un ejemplo, vea la definición de "buildRoot" en CMakeSettings.json.
2.  Generador: asigna al conmutador -G y se especifica el generador que se usará. Esta propiedad también puede utilizarse como una macro `${generator}` para ayudar a especificar otros valores de propiedad. Visual Studio admite actualmente los generadores de CMake siguientes:
    - "Ninja"
    - "Visual Studio 14/2015."
    - "Visual Studio 2015 14 ARM"
    - "Visual Studio 2015 14 Win64"
    - "Visual Studio de 2017 15"
    - "Visual Studio 15 2017 ARM"
    - "Visual Studio 15 2017 Win64"
    - 
Como Ninja está diseñado para las velocidades de compilaciones rápidas en lugar de flexibilidad y la función, se establece como valor predeterminado. Sin embargo, algunos proyectos CMake podrán que no puedas generar correctamente mediante Ninja. Si esto ocurre, puede indicar a CMake para generar un proyecto de Visual Studio en su lugar. 

Para especificar un generador de Visual Studio, abra el CMakeSettings.json en el menú principal, elija **CMake | Cambiar la configuración de CMake**. Elimine "Ninja" y escriba "V". Esto activa IntelliSense, lo que le permite elegir el generador que desee.
3.  buildRoot: se asigna a - conmutador DCMAKE_BINARY_DIR y especifica dónde se creará la caché CMake. Si la carpeta no existe, se creará.
4.  variables: contiene un par de nombre + valor de las variables de CMake obtener pasará como - Dname = valor a CMake. Si las instrucciones de compilación del proyecto CMake especifican agregar variables directamente en el archivo de caché de CMake, se recomienda que lo agregue aquí en su lugar.
5.  cmakeCommandArgs: especifica las opciones adicionales que se van a pasar al CMake.exe.
6.  configurationType: define el tipo de configuración de compilación para el generador de seleccionado. Valores admitidos actualmente son "Debug", "MinSizeRel", "Versión" y "RelWithDebInfo".

### <a name="environment-variables"></a>Variables de entorno
CMakeSettings.json también admite variables de entorno mucho en cualquiera de las propiedades mencionadas anteriormente. La sintaxis para usar es `${env.FOO}` para expandir la variable % FOO % de entorno.
También tienen acceso a las macros integradas dentro de este archivo:
- `${workspaceRoot}`: proporciona la ruta de acceso completa de la carpeta de área de trabajo
- `${workspaceHash}`– hash de ubicación de área de trabajo; útil para crear un identificador único para el área de trabajo actual (por ejemplo, para utilizar en las rutas de acceso de carpeta)
- `${projectFile}`: la ruta de acceso completa del archivo de CMakeLists.txt raíz
- `${projectDir}`: la ruta de acceso completa de la carpeta de la raíz del archivo de CMakeLists.txt
- `${thisFile}`: la ruta de acceso completa del archivo CMakeSettings.json
- `${name}`: el nombre de la configuración
- `${generator}`: el nombre del generador de CMake utilizado en esta configuración de

### <a name="ninja-command-line-arguments"></a>Argumentos de línea de comandos ninja

Si no se especifican destinos, genera el destino de 'default' (consulte el manual).

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Opción|Descripción|  
|--------------|------------|  
| --versión  | versión de impresión ninja ("1.7.1")| 
|   -C DIR   | Cambie al directorio antes de realizar cualquier otra cosa| 
|   -f archivo  | Especifique el archivo de entrada de compilación [default=build.ninja]| 
|   -j N     | ejecutar trabajos de N en paralelo [valor predeterminado = 14, derivado de CPU disponibles]| 
|   -k N     | Para continuar hasta que N trabajos por error [valor predeterminado = 1]| 
|   -l N     | no se inician nuevos trabajos si el promedio de carga es mayor que N| 
|   -n      | ejecutar seca (no se ejecutan comandos pero actúan como lo correctamente)| 
|   -v       | Mostrar todas las líneas de comandos durante la compilación| 
|   -d modo  | habilitar la depuración (uso de modos de una lista a -d)| 
|   -t herramienta  | ejecutar un subtool (Utilice herramientas secundarias de lista a la lista de -t). finaliza toplevel opciones; más marcas se pasan a la herramienta| 
|   -w marca  | Ajustar advertencias (uso de advertencias de una lista a -w)| 


### <a name="inherited-environments-visual-studio-2017-version-155"></a>Entornos heredados (Visual Studio 2017 versión 15,5)

CmakeSettings.json ahora es compatible con entornos de inherted. Esta característica le permite crear una variable personalizada que:

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

Este campo se establece las variables que se pasan automáticamente a CMake.exe cuando se ejecuta. El ejemplo anterior es la misma que ejecutar el "símbolo para VS 2017" con el `-arch=amd64 -host_arch=amd64` argumentos.

En la siguiente tabla muestra los valores admitidos y sus equivalentes de línea de comandos:

|Nombre de contexto|Descripción|  
|-----------|-----------------|
|vsdev|El entorno de Visual Studio de forma predeterminada|
|msvc_x86|Compilar para x86 con x86 herramientas|
|msvc_arm| Compilar para ARM mediante x86 herramientas|
|msvc_arm64|Compilación para ARM64 con x86 herramientas|
|msvc_x86_x64|Compilación para AMD64 con x86 herramientas|
|msvc_x64_x64|Compilación para AMD64 con herramientas de 64 bits|
|msvc_arm_x64|Compilar para ARM mediante las herramientas de 64 bits|
|msvc_arm64_x64|Compilación para ARM64 con herramientas de 64 bits|


Cuando se realizan cambios significativos para el CMakeSettings.json o CMakeLists.txt archivos, Visual Studio automáticamente vuelve a ejecutar la CMake configura paso. Si el paso de configuración finaliza sin errores, la información que se recopila se estén disponibles en los servicios de IntelliSense de C++ y el idioma y también en la compilación y las operaciones de depuración.

Cuando varios proyectos de CMake utilizan el mismo nombre de configuración de CMake (por ejemplo, x86-Debug), todas ellas se configuran y construyen (en su propia carpeta de raíz de la compilación) cuando se selecciona esa configuración. Puede depurar los destinos de todos los proyectos de CMake que participan en la que la configuración de CMake.

   ![CMake generar solo el elemento de menú](media/cmake-build-only.png)

Para limitar las compilaciones y depurar las sesiones para un subconjunto de los proyectos en el área de trabajo, cree una nueva configuración con un nombre único en el archivo CMakeSettings.json y aplicarla a solo aquellos proyectos. Una vez que la configuración seleccionada, IntelliSense, compilar, y la depuración estará habilitada únicamente para los proyectos de especificados.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake
Si necesita más información sobre el estado de la memoria caché de CMake para diagnosticar un problema, abra el menú principal de CMake o el menú contextual de CMakeLists.txt en **el Explorador de soluciones** para ejecutar uno de estos comandos:
- **Ver la memoria caché** abre el archivo CMakeCache.txt de la carpeta raíz de compilación en el editor. (Cualquier modificación que realice aquí para CMakeCache.txt se borra si limpia la memoria caché. Para realizar cambios que se conservarán después de que se limpia la memoria caché, vea [CMake configuración y las configuraciones personalizadas](#cmake_settings) anteriormente en este artículo.)
- **Abra la carpeta de caché** abre una ventana del explorador a la carpeta raíz de compilación.  
- **Limpiar la memoria caché** elimina la carpeta raíz de compilación para que el siguiente CMake configurar paso se inicia desde una memoria caché limpia.
- **Generar la caché** fuerza el paso de generar ejecutándose aunque Visual Studio considera que el entorno actualizado.

