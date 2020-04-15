---
title: Referencia del esquema de CMakeSettings.json
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: f9c864b66df86165090b7d6d6fc9c4fc51d65a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328893"
---
# <a name="cmakesettingsjson-schema-reference"></a>Referencia del esquema de CMakeSettings.json

::: moniker range="vs-2015"

Los proyectos de CMake se admiten en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

El archivo **CMakeSettings.json** contiene información que Visual Studio usa para IntelliSense y para construir los argumentos de línea de comandos que pasa a cmake.exe para una *configuración* y un *entorno*del compilador especificados. Una configuración especifica las propiedades que se aplican a una `x86-Debug` `Linux-Release`plataforma y tipo de compilación específicos, por ejemplo, o . Cada configuración especifica un entorno, que encapsula información sobre el conjunto de herramientas del compilador, por ejemplo MSVC, GCC o Clang. CMake utiliza los argumentos de línea de comandos para volver a generar el archivo *CMakeCache.txt* raíz y otros archivos de proyecto para el proyecto. Los valores se pueden invalidar en los archivos *CMakeLists.txt.*

Puede agregar o quitar configuraciones en el IDE y, a continuación, editarlas directamente en el archivo JSON o usar el editor de configuración de **CMake** (Visual Studio 2019 y versiones posteriores). Puede cambiar entre las configuraciones fácilmente en el IDE para generar los distintos archivos de proyecto. Consulte Personalizar la configuración de compilación de [CMake en Visual Studio](customize-cmake-settings.md) para obtener más información.

## <a name="configurations"></a>Configurations

La `configurations` matriz contiene todas las configuraciones para un proyecto CMake. Consulte Referencia de [configuración predefinida](cmake-predefined-configuration-reference.md) de CMake para obtener más información sobre las configuraciones predefinidas. Puede agregar cualquier número de configuraciones predefinidas o personalizadas al archivo.

Un elemento `configuration` tiene las siguientes propiedades:

- `addressSanitizerEnabled`: `true` si compila el programa con Address Sanitizer (Experimental en Windows). En Linux, compile con -fno-omit-frame-pointer y el nivel de optimización del compilador -Os o -Oo para obtener mejores resultados.
- `addressSanitizerRuntimeFlags`: los indicadores de tiempo de ejecución pasados a AddressSanitizer a través de la variable de entorno ASAN_OPTIONS. Formato: flag1-value:flag2-value2.
- `buildCommandArgs`: especifica los modificadores de compilación nativos que se pasan a CMake después de --build --. Por ejemplo, pasar -v cuando se usa el generador Ninja obliga a Ninja a dar como resultado líneas de comandos. Vea [Argumentos de la línea de comandos de Ninja](#ninja) para más información sobre los comandos de Ninja.
- `buildRoot`: especifica el directorio en el que CMake genera los scripts de compilación para el generador elegido.  Asigna a **-DCMAKE_BINARY_DIR** modificador y especifica dónde se creará *CMakeCache.txt.* Si la carpeta no existe, se creará. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `cacheGenerationCommand`: especifica una herramienta de línea de comandos y argumentos, por ejemplo *gencache.bat debug* para generar la memoria caché. El comando se ejecuta desde el shell en el entorno especificado para la configuración cuando el usuario solicita explícitamente la regeneración, o se modifica un archivo CMakeLists.txt o CMakeSettings.json.
- `cacheRoot`: especifica la ruta de acceso a una caché de CMake. Este directorio debe contener un archivo *CMakeCache.txt* existente.
- `clangTidyChecks`: lista separada por comas de advertencias que se pasarán a clang-tidy; se permiten comodines y el prefijo '-' eliminará las comprobaciones.
- `cmakeCommandArgs`: especifica opciones de línea de comandos adicionales pasadas a CMake cuando se invoca para generar los archivos de proyecto.
- `cmakeToolchain`: especifica el archivo de la cadena de herramientas. Para pasarlo a CMake se usa -DCMAKE_TOOLCHAIN_FILE.
- `codeAnalysisRuleset`: especifica el conjunto de reglas que se usa al ejecutar el análisis de código. Puede ser una ruta de acceso completa o el nombre de un archivo de conjunto de reglas que Visual Studio ha instalado.
- `configurationType`: especifica la configuración del tipo de compilación del generador seleccionado. Puede ser uno de los siguientes:

  - Depurar
  - Release
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs`: especifica opciones adicionales de la línea de comandos que se pasan a CTest al ejecutar las pruebas.
- `description`: descripción de esta configuración que aparecerá en los menús.
- `enableClangTidyCodeAnalysis`: utilice Clang-Tidy para el análisis de código.
- `enableMicrosoftCodeAnalysis`: utilice las herramientas de análisis de código de Microsoft para el análisis de código.
- `generator`: especifica el generador de CMake que se usará para esta configuración. Puede ser uno de los siguientes:
  
  **Solo Visual Studio 2019:**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 y versiones posteriores:**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Archivos Make Unix
  - Ninja

Como Ninja está diseñado para velocidades de compilación rápidas en lugar de flexibilidad y funcionamiento, se establece como el valor predeterminado. Pero es posible que algunos proyectos de CMake no se puedan generar correctamente mediante Ninja. Si esto ocurre, puede indicar a CMake que genere proyectos de Visual Studio en su lugar.

Para especificar un generador de Visual Studio en Visual Studio 2017, abra el desde el menú principal eligiendo **CMake . Cambiar configuración de CMake**. Eliminar "Ninja" y escriba "V". Esto activa IntelliSense, lo que permite elegir el generador que quiera.

Para especificar un generador de Visual Studio en Visual Studio 2019, haga clic con el botón derecho en el archivo *CMakeLists.txt* en **el Explorador** de soluciones y elija Configuración **de CMake para el proyecto** > **Mostrar configuración** > avanzada **CMake Generator**.

Cuando la configuración activa especifica un generador de Visual Studio, de forma predeterminada se invoca MSBuild.exe con argumentos `-m -v:minimal`. Para personalizar la compilación, dentro del archivo *CMakeSettings.json,* puede especificar argumentos de línea de `buildCommandArgs` comandos adicionales de [MSBuild](../build/reference/msbuild-visual-cpp-overview.md) que se pasarán al sistema de compilación a través de la propiedad:

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `installRoot`: especifica el directorio en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `inheritEnvironments`: especifica uno o más entornos de compilador de los que depende esta configuración. Puede ser cualquier entorno personalizado, o bien uno de los entornos predefinidos. Para obtener más información, vea [Entornos](#environments).
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

- `name`: nombres de la configuración.  Consulte Referencia de [configuración predefinida](cmake-predefined-configuration-reference.md) de CMake para obtener más información sobre las configuraciones predefinidas.
- `wslPath`: la ruta de acceso al iniciador de una instancia de Windows Subsystem para Linux.

### <a name="additional-settings-for-cmake-linux-projects"></a>Configuración adicional para proyectos de CMake Linux

- `remoteMachineName`: especifica el nombre del equipo Linux remoto que hospeda CMake, compilaciones y el depurador. Use el Administrador de conexiones para agregar nuevas máquinas Linux. Entre las macros admitidas se incluye `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity`: especifica el nivel de detalle de la operación de copia de origen en la máquina remota. Puede ser " Normal", "Detallado" o "Diagnóstico".
- `remoteCopySourcesConcurrentCopies`: especifica el número de copias simultáneas utilizadas durante la sincronización de los orígenes con el equipo remoto (solo sftp).
- `remoteCopySourcesMethod`: especifica el método para copiar los archivos en la máquina remota. Puede ser "rsync" o "sftp".
- `remoteCMakeListsRoot`: especifica el directorio del equipo remoto que contiene el proyecto de CMake. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `remoteBuildRoot`: especifica el directorio de la máquina remota en el que CMake genera los scripts de compilación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `remoteInstallRoot`: especifica el directorio de la máquina remota en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`, donde `VARIABLE` es una variable de entorno que se ha definido en el nivel de sistema, usuario o sesión.
- `remoteCopySources`: `boolean` un valor que especifica si Visual Studio debe copiar archivos de origen en el equipo remoto. El valor predeterminado es true. Establézcalo en false si administra usted mismo la sincronización de archivos.
- `remoteCopyBuildOutput`: `boolean` a que especifica si se van a copiar las salidas de compilación desde el sistema remoto.
- `remoteCopyAdditionalIncludeDirectories`: directorios de inclusión adicionales que se copiarán desde el equipo remoto para admitir IntelliSense. Formatee como "/path1;/path2...".
- `remoteCopyExcludeDirectories`: Incluya directorios NO copiar desde el equipo remoto. Formatee como "/path1;/path2...".
- `remoteCopyUseCompilerDefaults`: especifica si se debe utilizar las rutas de acceso predeterminadas del compilador e incluir para IntelliSense. Solo debe ser false si los compiladores en uso para no admitir argumentos de estilo gcc.
- `rsyncCommandArgs`: especifica un conjunto de opciones adicionales de la línea de comandos que se pasan a rsync.
- `remoteCopySourcesExclusionList`: `array` A que especifica una lista de rutas que se excluirán al copiar archivos de origen': una ruta de acceso puede ser el nombre de un archivo/directorio o una ruta relativa a la raíz de la copia. Los caracteres comodín \\\"*\\\" y \\\"?\\\" se pueden usar para la coincidencia de patrones globales.
- `cmakeExecutable`: especifica la ruta de acceso completa al ejecutable del programa CMake, incluidos el nombre y la extensión del archivo.
- `remotePreGenerateCommand`: especifica el comando que se ejecutará antes de ejecutar CMake para analizar el archivo *CMakeLists.txt.*
- `remotePrebuildCommand`: especifica el comando que debe ejecutarse en la máquina remota antes de compilar.
- `remotePostbuildCommand`: especifica el comando que debe ejecutarse en la máquina remota después de compilar.
- `variables`: contiene un par nombre-valor de variables de CMake que se pasan como **-D** *_nombre_=_valor_* a CMake. Si las instrucciones de compilación del proyecto CMake especifican la adición de variables directamente al archivo *CMakeCache.txt,* se recomienda agregarlas aquí en su lugar. En el siguiente ejemplo se muestra cómo especificar los pares nombre-valor para el conjunto de herramientas MSVC 14.14.26428:

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    }
  ]
```

Tenga en cuenta que `"type"`si `"STRING"` no define el , el tipo se asumirá de forma predeterminada.

- `remoteCopyOptimizations`: **Visual Studio 2019 versión 16.5 o posterior** propiedades para controlar la copia de origen en el destino remoto. Las optimizaciones están habilitadas de forma predeterminada. Incluye `remoteCopyUseOptimizations`, `rsyncSingleDirectoryCommandArgs` y `remoteCopySourcesMaxSmallChange`.

## <a name="environments"></a><a name="environments"></a>Entornos

Un *entorno* encapsula las variables de entorno que se establecen en el proceso que Visual Studio usa para invocar cmake.exe. Para los proyectos MSVC, las variables son aquellas que se establecen en un símbolo del sistema para [desarrolladores](building-on-the-command-line.md) para una plataforma específica. Por ejemplo, `msvc_x64_x64` el entorno es el mismo que ejecutar el símbolo del sistema para desarrolladores **para VS 2017** o el símbolo del sistema para desarrolladores **para VS 2019** con los argumentos **-arch-amd64 -host_arch-amd64.** Puede utilizar `env.{<variable_name>}` la sintaxis de *CMakeSettings.json* para hacer referencia a las variables de entorno individuales, por ejemplo, para construir rutas de acceso a carpetas.  Se proporcionan los siguientes entornos predefinidos:

- linux_arm: Destino ARM Linux de forma remota.
- linux_x64: Destino x64 Linux de forma remota.
- linux_x86: Destino x86 Linux de forma remota.
- msvc_arm: Tener como destino ARM Windows con el compilador MSVC.
- msvc_arm_x64: Tener como destino ARM Windows con el compilador MSVC de 64 bits.
- msvc_arm64: Destino ARM64 Windows con el compilador MSVC.
- msvc_arm64_x64: Destino ARM64 Windows con el compilador MSVC de 64 bits.
- msvc_x64: Destino x64 Windows con el compilador MSVC.
- msvc_x64_x64: Destino x64 Windows con el compilador MSVC de 64 bits.
- msvc_x86: Destino x86 Windows con el compilador MSVC.
- msvc_x86_x64: Destino x86 Windows con el compilador MSVC de 64 bits.

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>Acceso a variables de entorno desde CMakeLists.txt

Desde un archivo CMakeLists.txt, la sintaxis `$ENV{variable_name}`hace referencia a todas las variables de entorno. Para ver las variables disponibles para un entorno, abra el símbolo del sistema correspondiente y escriba `SET`. Parte de la información de las variables de entorno también está disponible a través de las variables de introspección del sistema CMake, pero puede resultar más conveniente utilizar la variable de entorno. Por ejemplo, la versión del compilador MSVC o la versión de Windows SDK se recuperan fácilmente a través de las variables de entorno.

### <a name="custom-environment-variables"></a>Variables de entorno personalizadas

En `CMakeSettings.json`, puede definir variables de entorno personalizadas globalmente o por configuración en la `environments` matriz. Un entorno personalizado es una forma cómoda de agrupar un conjunto de propiedades que puede usar en lugar de un entorno predefinido o de ampliar o modificar un entorno predefinido. Cada elemento de la matriz `environments` consta de lo siguiente:

- `namespace`: son los nombres de entorno, para que se pueda hacer referencia a sus variables desde una configuración con el formato `namespace.variable`. Se llama al `env` objeto de entorno predeterminado y se `%USERPROFILE%`rellena con ciertas variables de entorno del sistema, incluido .
- `environment`: identifica de forma única este grupo de variables. Permite que el grupo se herede más adelante en una entrada `inheritEnvironments`.
- `groupPriority`: un entero que especifica la prioridad de estas variables al evaluarlas. Los elementos con un número más alto se evalúan primero.
- `inheritEnvironments`: matriz de valores que especifican el conjunto de entornos heredados por este grupo. Esta característica permite heredar entornos predeterminados y crear variables de entorno personalizadas que se pasan a CMake.exe cuando se ejecuta.

**Visual Studio 2019 versión 16.4 y versiones posteriores:** Los destinos de depuración se inician automáticamente con el entorno especificado en *CMakeSettings.json*. Puede invalidar o agregar variables de entorno por destino o por tarea en [launch.vs.json](launch-vs-schema-reference-cpp.md) y [tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

En el ejemplo siguiente se define una variable global, **BuildDir**, que se hereda en las configuraciones x86-Debug y x64-Debug. En cada configuración se usa la variable para especificar el valor de la propiedad **buildRoot** para esa configuración. Tenga en cuenta también cómo se usa la propiedad **inheritEnvironments** en cada configuración para especificar una variable que solo se aplica a esa configuración.

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

En el ejemplo siguiente, la configuración de depuración x86 define su propio valor para la propiedad **BuildDir**. Este valor invalida el valor establecido por la propiedad global **BuildDir** para que **BuildRoot** se evalúe como `D:\custom-builddir\x86-Debug`.

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
          "BuildDir": "D:\\custom-builddir"
          // This environment does not specify a namespace, hence by default "env" will be assumed.
          // "namespace" : "name" would require that this variable be referenced with "${name.BuildDir}".
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
      // Since this configuration doesn't modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="macros"></a>Macros

Las siguientes macros se pueden utilizar en *CMakeSettings.json:*

- `${workspaceRoot}`– la ruta completa de la carpeta del espacio de trabajo
- `${workspaceHash}`: hash de ubicación del área de trabajo; es útil para crear un identificador único para el área de trabajo actual (por ejemplo, para usarlo en las rutas de acceso de carpeta).
- `${projectFile}`: la ruta de acceso completa del archivo CMakeLists.txt raíz.
- `${projectDir}`: la ruta de acceso completa de la carpeta del archivo CMakeLists.txt raíz.
- `${thisFile}`: ruta de acceso completa del archivo `CMakeSettings.json`.
- `${name}`: el nombre de la configuración
- `${generator}`: el nombre del generador de CMake que se usa en esta configuración.

Todas las referencias a macros y variables de entorno en *CMakeSettings.json* se expanden antes de pasarse a la línea de comandos cmake.exe.

## <a name="ninja-command-line-arguments"></a><a name="ninja"></a> Argumentos de la línea de comandos de Ninja

Si no se especifican destinos, se compila el destino "default".

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Opción|Descripción|
|--------------|------------|
| --version  | Se imprime la versión de Ninja ("1.7.1").|
|   -C DIR   | Se cambia a DIR antes de realizar cualquier otra acción.|
|   -f FILE  | Se especifica el archivo de compilación de entrada (valor predeterminado = build.ninja).|
|   -j N     | Se ejecutan N trabajos en paralelo (valor predeterminado = 14, se deriva de las CPU disponibles).|
|   -k N     | Se continúa hasta que se produzca un error en N trabajos (valor predeterminado = 1).|
|   -l N     | No se inician trabajos nuevos si el promedio de carga es mayor que N.|
|   -n       | Simulacro (no se ejecutan comandos pero se actúa como si fueran correctos).|
|   -v       | Se muestran todas las líneas de comandos durante la compilación.|
|   -d MODE  | Se habilita la depuración (use -d list para enumerar los modos).|
|   -t TOOL  | Se ejecuta una herramienta secundaria (use -t list para enumerar las herramientas secundarias). Finaliza las opciones de nivel superior; se pasan más marcas a la herramienta.|
|   -w FLAG  | Se ajustan las advertencias (use -w list para enumerar las advertencias).|

::: moniker-end
