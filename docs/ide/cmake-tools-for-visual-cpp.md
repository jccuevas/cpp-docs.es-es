---
title: Proyectos de CMake en Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38bcd102e94ac98aba56a4eb98b69df6d3f16111
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238570"
---
# <a name="cmake-projects-in-visual-c"></a>Proyectos de CMake en Visual C++

En este artículo se da por supuesto que está familiarizado con CMake, una herramienta de código abierto multiplataforma para definir procesos de compilación que se ejecutan en varias plataformas.

In Visual Studio 2015, los usuarios de Visual Studio pueden usar un [generador CMake](https://cmake.org/cmake/help/v3.9/manual/cmake-generators.7.html) para generar archivos de proyecto de MSBuild que, después, el IDE usa para IntelliSense, exploración y compilación. 

A partir de Visual Studio 2017, en el componente **Herramientas de Visual C++ para CMake** se usa la característica **Abrir carpeta** para habilitar el IDE para el consumo de archivos de proyecto CMake (por ejemplo, CMakeLists.txt) directamente para los propósitos de IntelliSense y la exploración. Si usa un generador de Visual Studio, se genera un archivo de proyecto temporal y se pasa a msbuild.exe, pero nunca se carga para IntelliSense o con fines de exploración. 

**Visual Studio 2017 versión 15.3**: se incluye compatibilidad con los generadores de Ninja y Visual Studio.

**Visual Studio 2017 versión 15.4**: se ha agregado compatibilidad con CMake en Linux. Para obtener más información, vea [Configure a Linux CMake Project](../linux/cmake-linux-project.md) (Configuración de un proyecto CMake de Linux).

**Visual Studio 2017, versión 15.5**: se ha agregado compatibilidad para importar una caché de CMake existente. Visual Studio extrae las variables personalizadas de manera automática y crea un archivo CMakeSettings.json previamente rellenado.

**Visual Studio 2017 versión 15.7**: se ha agregado compatibilidad para deshabilitar la generación automática de caché, la vista de destinos en el **Explorador de soluciones**, opciones de generación de caché y la compilación de archivo único.

## <a name="installation"></a>Instalación

**Herramientas de Visual C++ para CMake** se instala de forma predeterminada como parte de la carga de trabajo **Desarrollo para el escritorio con C++**.

![Componente de CMake en la carga de trabajo Escritorio de C++](media/cmake-install.png)
 
## <a name="ide-integration"></a>Integración del IDE

Al seleccionar **Archivo | Abrir | Carpeta** para abrir una carpeta que contiene un archivo CMakeLists.txt, sucede lo siguiente:

- Visual Studio agrega un elemento de menú **CMake** al menú principal, con los comandos para ver y modificar scripts de CMake.
- En el **Explorador de soluciones** se muestra la estructura de carpetas y archivos.
- Visual Studio ejecuta CMake.exe y genera la caché de CMake para la *configuración* predeterminada, que es Debug x86. La línea de comandos de CMake se muestra en la **ventana de Salida**, junto con una salida adicional de CMake.  **Visual Studio 2017 versión 15.7 y versiones posteriores**: la generación automática de caché se puede deshabilitar en el cuadro de diálogo **Herramientas | Opciones | CMake | General**.
- En segundo plano, Visual Studio empieza a indexar los archivos de código fuente para habilitar IntelliSense, la información de exploración, la refactorización y así sucesivamente. Mientras trabaja, Visual Studio supervisa los cambios en el editor y también en el disco para mantener sincronizado su índice con los orígenes.
 
Puede abrir carpetas que contengan cualquier número de proyectos de CMake. Visual Studio detecta y configura todos los archivos CMakeLists.txt "raíz" en el área de trabajo. Las operaciones de CMake (configurar, compilar, depurar) así como IntelliSense y la exploración de C++ están disponibles para todos los proyectos de CMake del área de trabajo.

![Proyecto de CMake con varias raíces](media/cmake-multiple-roots.png)  

**Visual Studio 2017 versión 15.7 y versiones posteriores**: los proyectos también se pueden ver organizados lógicamente por destinos. Elija **Targets view** (Vista de destinos) en la lista desplegable de la barra de herramientas del **Explorador de soluciones**:

![Botón de vista de destinos de CMake](media/cmake-targets-view.png)

## <a name="import-an-existing-cache"></a>Importar una caché existente

Cuando se importa un archivo CMakeCache.txt existente, Visual Studio extrae las variables personalizadas de manera automática y crea un archivo CMakeSettings.json previamente rellenado basado en ellas. La caché original no se modifica de ninguna manera y se puede seguir usando desde la línea de comandos o con cualquier herramienta o IDE que se usara para generarla. El archivo CMakeSettings.json nuevo se coloca junto al archivo CMakeLists.txt raíz del proyecto. Visual Studio genera una caché nueva en función del archivo de configuración.  


**Visual Studio 2017 versión 15.7 y versiones posteriores**: la generación automática de caché se puede invalidar en el cuadro de diálogo **Herramientas | Opciones | CMake | General**.

No se importa todo el contenido de la caché.  Propiedades como el generador y la ubicación de los compiladores se reemplazan con valores predeterminados que se sabe que funcionan de manera correcta con el IDE.

### <a name="to-import-an-existing-cache"></a>Para importar una caché existente

1. En el menú principal, seleccione **Archivo | Abrir | CMake**:

   ![Abrir CMake](media/cmake-file-open.png "Archivo, Abrir, CMake") 

   Se abrirá el asistente **Importar proyecto CMake de la memoria caché**. 
   
2. Navegue hasta el archivo CMakeCache.txt que quiere importar y después haga clic en **Aceptar**. Se abrirá el asistente **Importar proyecto CMake de la memoria caché**:

   ![Importar una caché CMake](media/cmake-import-wizard.png "Abrir el Asistente para importar la caché de CMake") 

   Cuando se complete el asistente, verá el archivo CMakeCache.txt nuevo en el **Explorador de soluciones** junto al archivo CMakeLists.txt raíz del proyecto.


## <a name="building-cmake-projects"></a>Compilar proyectos de CMake

Para compilar un proyecto de CMake, tienes estas opciones:

1. Seleccione el destino en la lista desplegable **Depurar** y presione **F5**, o bien haga clic en el botón **Ejecutar** (el triángulo de color verde). Primero se compila el proyecto de manera automática, como una solución de Visual Studio.
1. Haga clic con el botón derecho en CMakeLists.txt y seleccione **Compilar** en el menú contextual. Si tiene varios destinos en la estructura de carpetas, puede elegir compilarlos todos o solo un destino específico, o bien,
1. en el menú principal, seleccione **Compilar | Compilar solución** (**F7** o **Ctrl+Mayús+B**). Asegúrese de que hay un destino de CMake seleccionado en la lista desplegable **Elemento de inicio** de la barra de herramientas **General**.

![Comando Compilar del menú de CMake](media/cmake-build-menu.png "Comando Compilar del menú de CMake") 

Cuando se selecciona un generador de Visual Studio para la configuración activa, se invoca MSBuild.exe con los argumentos `-m -v:minimal`. Para personalizar la compilación, en el archivo CMakeSettings.json, puede especificar argumentos de la línea de comandos adicionales que se pasarán al sistema de compilación a través de la propiedad `buildCommandArgs`:

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

Como cabría esperar, los resultados de la compilación se muestran en la **ventana de Salida** y en la **Lista de errores**.
 
![Errores de compilación de CMake](media/cmake-build-errors.png "CMake build errors")

En una carpeta con varios destinos de compilación, puede elegir el elemento **Generar** del menú **CMake** o el menú contextual de **CMakeLists.txt** para especificar qué destino de CMake se va a compilar. Al presionar **Ctrl+Mayús+B** en un proyecto de CMake se compila el documento activo actual.

## <a name="debug-the-project"></a>Depurar el proyecto

Para depurar un proyecto de CMake, elija la configuración deseada y presione **F5**, o bien presione el botón **Ejecutar** en la barra de herramientas. Si en el botón **Ejecutar** se indica "Seleccionar elemento de inicio", haga clic en la flecha desplegable y elija el destino que quiera ejecutar. (En un proyecto de CMake, la opción "Documento actual" solo es válida para los archivos .cpp). 

![Botón Ejecutar de CMake](media/cmake-run-button.png "Botón Ejecutar de CMake")

Los comandos **Ejecutar** o **F5** compilan primero el proyecto si se han realizado cambios desde la compilación anterior.

## <a name="configure-cmake-debugging-sessions"></a>Configurar sesiones de depuración de CMake

Todos los destinos de CMake ejecutables se muestran en la lista desplegable **Elemento de inicio** en la barra de herramientas **General**. Para empezar una sesión de depuración, seleccione una e inicie el depurador.

![Lista desplegable Elemento de inicio de CMake](media/cmake-startup-item-dropdown.png "CMake startup item dropdown")


También puede iniciar una sesión de depuración desde los menús de CMake.

Para personalizar la configuración del depurador para cualquier destino de CMake ejecutable en el proyecto, haga clic con el botón derecho en el archivo CMakeLists.txt específico y seleccione **Configuración de depuración e inicio**. Al seleccionar un destino de CMake en el submenú, se crea un archivo denominado launch.vs.json. Este archivo se ha rellenado previamente con información sobre el destino de CMake que ha seleccionado y permite especificar parámetros adicionales como argumentos de programa o el tipo de depurador. Para hacer referencia a cualquier clave en un archivo CMakeSettings.json, debe anteponer "CMake." en launch.vs.json. En el ejemplo siguiente se muestra un archivo launch.vs.json simple que extrae el valor de la clave "remoteCopySources" en el archivo CMakeSettings.json para la configuración seleccionada actualmente:

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

Al guardar el archivo launch.vs.json, se crea una entrada en la lista desplegable **Elemento de inicio** con el nombre nuevo. Si se modifica el archivo launch.vs.json, se pueden crear tantas configuraciones de depuración como sea necesario para cualquier número de destinos de CMake.

**Visual Studio 2017 versión 15.4**: launch.vs.json es compatible con las variables que se declaran en CMakeSettings.json (ver a continuación) y que se aplican a la configuración seleccionada actualmente. También tiene una clave denominada "currentDir", que establece el directorio actual de la aplicación de inicio:


```json
{
"type": "default",
"project": "CMakeLists.txt",
"projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Al ejecutar la aplicación, el valor de `currentDir` es similar al siguiente:

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

## <a name="editing-cmakeliststxt-files"></a>Edición de archivos CMakeLists.txt

Para editar un archivo CMakeLists.txt, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y seleccione **Abrir**. Si realiza cambios en el archivo, aparece una barra de estado de color amarillo y le informa de que IntelliSense se va a actualizar, y le da la oportunidad de cancelar la operación de actualización. Para obtener información sobre CMakeLists.txt, vea la [documentación de CMake](https://cmake.org/documentation/).

   ![Edición de archivos CMakeLists.txt](media/cmake-cmakelists.png "CMakeLists.txt file editing")


Tan pronto como se guarde el archivo, se vuelve a ejecutar el paso de configuración de manera automática y se muestra la información en la ventana **Salida**. Los errores y las advertencias se muestran en la **Lista de errores** o en la ventana **Salida**. Haga doble clic en un error en la **Lista de errores** para navegar a la línea incorrecta en CMakeLists.txt.

   ![Errores de archivos CMakeLists.txt](media/cmake-cmakelists-error.png "CMakeLists.txt file errors")

## <a name="cmake_settings"></a> Opciones y configuraciones personalizadas de CMake

De forma predeterminada, Visual Studio proporciona seis configuraciones de CMake predeterminadas ("x86-Debug", "x86-Release", "x64-Debug", "x64-Release", "Linux-Debug" y "Linux-Release"). Estas configuraciones definen cómo se invoca CMake.exe para crear una caché de CMake para un proyecto determinado. Para modificar estas configuraciones, o bien para crear una configuración personalizada, seleccione **CMake | Cambiar la configuración de CMake** y, después, elija el archivo CMakeLists.txt al que se aplica la configuración. El comando **Cambiar la configuración de CMake** también está disponible en el menú contextual del archivo en el **Explorador de soluciones**. Este comando crea un archivo CMakeSettings.json en la carpeta del proyecto. Este archivo se usa para volver a crear el archivo de caché de CMake, por ejemplo después de una operación **Limpiar**. 

   ![Comando de menú principal de CMake para cambiar la configuración](media/cmake-change-settings.png)

IntelliSense de JSON ayuda a editar el archivo CMakeSettings.json:

   ![IntelliSense de JSON para CMake](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

En el ejemplo siguiente se muestra un ejemplo de configuración, que se puede usar como punto de partida para crear la suya propia en CMakeSettings.json:

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

1. **name**: el nombre que aparece en la lista desplegable de configuración de C++. Este valor de propiedad también se puede usar como una macro, `${name}`, para especificar otros valores de propiedad. Para obtener un ejemplo, vea la definición de **buildRoot** en CMakeSettings.json.
1. **generator**: se asigna al modificador **-G** y especifica el generador que se va a usar. Esta propiedad también se puede usar como una macro, `${generator}`, para especificar otros valores de propiedad. En la actualidad, Visual Studio admite los generadores de CMake siguientes:

    - "Ninja"
    - "Visual Studio 14 2015"
    - "Visual Studio 14 2015 ARM"
    - "Visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017"
    - "Visual Studio 15 2017 ARM"
    - "Visual Studio 15 2017 Win64"

Como Ninja está diseñado para velocidades de compilación rápidas en lugar de flexibilidad y funcionamiento, se establece como el valor predeterminado. Pero es posible que algunos proyectos de CMake no se puedan generar correctamente mediante Ninja. Si esto ocurre, puede indicar a CMake que en su lugar genere un proyecto de Visual Studio.

Para especificar un generador de Visual Studio, abra el archivo CMakeSettings.json en el menú principal mediante **CMake | Cambiar la configuración de CMake**. Elimine "Ninja" y escriba "V". Esto activa IntelliSense, lo que permite elegir el generador que quiera.

1. **buildRoot**: se asigna al modificador **DCMAKE_BINARY_DIR** y especifica dónde se va a crear la caché de CMake. Si la carpeta no existe, se creará.
1. **variables**: contiene un par nombre-valor de variables de CMake que se pasan como **-D**_nombre_**=**_valor_ a CMake. Si las instrucciones de compilación del proyecto de CMake especifican la adición de las variables directamente al archivo de caché de CMake, en su lugar se recomienda agregarlas aquí.
1. **cmakeCommandArgs**: especifica los modificadores adicionales que se quieren a pasar a CMake.exe.
1. **configurationType**: define el tipo de configuración de compilación para el generador seleccionado. Los valores admitidos actualmente son "Debug", "MinSizeRel", "Release" y "RelWithDebInfo".

### <a name="environment-variables"></a>Variables de entorno

CMakeSettings.json también admite el consumo de variables de entorno en cualquiera de las propiedades mencionadas anteriormente. La sintaxis que se usa es `${env.FOO}` para expandir la variable de entorno %FOO%.
También se puede acceder a las macros integradas dentro de este archivo:

- `${workspaceRoot}`: proporciona la ruta de acceso completa de la carpeta de área de trabajo.
- `${workspaceHash}`: hash de ubicación del área de trabajo; es útil para crear un identificador único para el área de trabajo actual (por ejemplo, para usarlo en las rutas de acceso de carpeta).
- `${projectFile}`: la ruta de acceso completa del archivo CMakeLists.txt raíz.
- `${projectDir}`: la ruta de acceso completa de la carpeta del archivo CMakeLists.txt raíz.
- `${thisFile}`: la ruta de acceso completa del archivo CMakeSettings.json.
- `${name}`: el nombre de la configuración
- `${generator}`: el nombre del generador de CMake que se usa en esta configuración.

### <a name="ninja-command-line-arguments"></a>Argumentos de la línea de comandos de Ninja

Si no se especifican destinos, se compila el destino "default" (vea el manual).

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Opción|Description|
|--------------|------------|
| --version  | Se imprime la versión de Ninja ("1.7.1").|
|   -C DIR   | Se cambia a DIR antes de realizar cualquier otra acción.|
|   -f FILE  | Se especifica el archivo de compilación de entrada (valor predeterminado = build.ninja).|
|   -j N     | Se ejecutan N trabajos en paralelo (valor predeterminado = 14, se deriva de las CPU disponibles).|
|   -k N     | Se continúa hasta que se produzca un error en N trabajos (valor predeterminado = 1).|
|   -l N     | No se inician trabajos nuevos si el promedio de carga es mayor que N.|
|   -n      | Simulacro (no se ejecutan comandos pero se actúa como si fueran correctos).|
|   -v       | Se muestran todas las líneas de comandos durante la compilación.|
|   -d MODE  | Se habilita la depuración (use -d list para enumerar los modos).|
|   -t TOOL  | Se ejecuta una herramienta secundaria (use -t list para enumerar las herramientas secundarias). Finaliza las opciones de nivel superior; se pasan más marcas a la herramienta.| 
|   -w FLAG  | Se ajustan las advertencias (use -w list para enumerar las advertencias).|

### <a name="inherited-environments-visual-studio-2017-version-155"></a>Entornos heredados (Visual Studio 2017, versión 15.5)
Ahora CMakeSettings.json es compatible con los entornos heredados. Esta característica permite (1) heredar los entornos predeterminados y (2) crear variables de entorno personalizadas que se pasan a CMake.exe cuando se ejecuta.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

El ejemplo anterior equivale a ejecutar el **Símbolo del sistema para desarrolladores de VS 2017** con los argumentos **-arch=amd64 -host_arch=amd64**.

En la tabla siguiente se muestran los valores predeterminados y sus equivalentes de la línea de comandos:

|Nombre del contexto|Description|
|-----------|-----------------|
|vsdev|El entorno de Visual Studio predeterminado.|
|msvc_x86|Compilar para x86 con herramientas de x86.|
|msvc_arm| Compilar para ARM con herramientas de x86.|
|msvc_arm64|Compilar para ARM64 con herramientas de x86.|
|msvc_x86_x64|Compilar para AMD64 con herramientas de x86.|
|msvc_x64_x64|Compilar para AMD64 con herramientas de 64 bits.|
|msvc_arm_x64|Compilar para ARM con herramientas de 64 bits.|
|msvc_arm64_x64|Compilar para ARM64 con herramientas de 64 bits.|

### <a name="custom-environment-variables"></a>Variables de entorno personalizadas
En CMakeSettings.json, se pueden definir variables de entorno personalizadas de manera global o por cada configuración en la propiedad **environments**. En el ejemplo siguiente se define una variable global, **BuildDir**, que se hereda en las configuraciones x86-Debug y x64-Debug. En cada configuración se usa la variable para especificar el valor de la propiedad **buildRoot** para esa configuración. Tenga en cuenta también cómo se usa la propiedad **inheritEnvironments** en cada configuración para especificar una variable que solo se aplica a esa configuración.

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

En el ejemplo siguiente, la configuración x86-Debug define su propio valor para la propiedad **BuildDir** y este valor invalida el que establece la propiedad **BuildDir** global de modo que **BuildRoot** se evalúe como `D:\custom-builddir\x86-Debug`.

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir",
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ], 
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="cmake-configure-step"></a>Paso de configuración de CMake

Cuando se realizan cambios importantes en los archivos CMakeSettings.json o CMakeLists.txt, Visual Studio vuelve a ejecutar de manera automática el paso de configuración de CMake. Si el paso de configuración finaliza sin errores, la información que se recopila está disponible en IntelliSense de C++ y los servicios de lenguaje, y también en las operaciones de compilación y depuración.

Cuando varios proyectos de CMake usan el mismo nombre de configuración de CMake (por ejemplo, x86-Debug), todos se configuran y compilan (en su propia carpeta raíz de compilación) al seleccionar esa configuración. Puede depurar los destinos de todos los proyectos de CMake que participan en esa configuración de CMake.

   ![Elemento de menú Solo compilación de CMake](media/cmake-build-only.png "CMake Build Only menu item")

Para limitar las compilaciones y las sesiones de depuración a un subconjunto de los proyectos en el área de trabajo, cree una configuración con un nombre único en el archivo CMakeSettings.json y aplíquela solamente a esos proyectos. Al seleccionar esa configuración, los comandos de IntelliSense y de compilación y depuración se habilitan solo para los proyectos especificados.

## <a name="troubleshooting-cmake-cache-errors"></a>Solución de problemas de errores de caché de CMake

Si necesita más información sobre el estado de caché de CMake para diagnosticar un problema, abra el menú principal de **CMake** o el menú contextual de **CMakeLists.txt** en el **Explorador de soluciones** para ejecutar uno de estos comandos:

- **Ver caché** abre el archivo CMakeCache.txt desde la carpeta raíz de compilación en el editor. (Cualquier modificación que realice aquí para CMakeCache.txt se borra si limpia la caché. Para realizar cambios que se conserven después de limpiar la caché, vea [Opciones y configuraciones personalizadas de CMake](#cmake_settings) anteriormente en este artículo).
- **Abrir carpeta de caché** abre una ventana del explorador por la carpeta raíz de compilación.  
- **Limpiar caché** elimina la carpeta raíz de compilación para que el siguiente paso de configuración de CMake se inicie desde una caché limpia.
- **Generar caché** fuerza la ejecución del paso de generación aunque Visual Studio considere que el entorno está actualizado.
 
**Visual Studio 2017 versión 15.7 y versiones posteriores**: la generación automática de caché se puede deshabilitar en el cuadro de diálogo **Herramientas | Opciones | CMake | General**.

## <a name="single-file-compilation"></a>Compilación de archivo único

**Visual Studio 2017 versión 15.7 y versiones posteriores**: para compilar un único archivo en un proyecto de CMake, haga clic con el botón derecho en el archivo en el **Explorador de soluciones** y elija **Compilar**. También puede compilar el archivo que esté actualmente abierto en el editor, usando para ello el menú principal de CMake:

![Compilación de archivo único de CMake](media/cmake-single-file-compile.png)