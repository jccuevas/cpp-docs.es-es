---
title: Referencia del esquema de CMakeSettings.json
ms.date: 10/31/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 2233c0767fb7fac2fe496e744750f380e1c3b698
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303234"
---
# <a name="cmakesettingsjson-schema-reference"></a>Referencia del esquema de CMakeSettings.json

::: moniker range="vs-2015"

Los proyectos de CMake se admiten en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

El archivo **CMakeSettings. JSON** contiene información que Visual Studio usa para IntelliSense y para construir los argumentos de línea de comandos que pasa a CMake. exe para un *entorno*de *configuración* y de compilador especificado. Una configuración especifica las propiedades que se aplican a una plataforma específica y a un tipo de compilación, por ejemplo, `x86-Debug` o `Linux-Release`. Cada configuración especifica un entorno, que encapsula información sobre el conjunto de herramientas del compilador, por ejemplo, MSVC, GCC o Clang. CMake usa los argumentos de línea de comandos para regenerar el archivo *CMakeCache. txt* raíz y otros archivos de proyecto para el proyecto. Los valores se pueden invalidar en los archivos *archivo CMakeLists. txt* . 

Puede Agregar o quitar configuraciones en el IDE y editarlas directamente en el archivo JSON o usar el editor de **configuración de CMake** (Visual Studio 2019 y versiones posteriores). Puede cambiar fácilmente entre las configuraciones en el IDE para generar los distintos archivos del proyecto. Consulte [personalizar la configuración de compilación de CMake en Visual Studio](customize-cmake-settings.md) para obtener más información.

## <a name="configurations"></a>Configuraciones

La matriz `configurations` contiene todas las configuraciones de un proyecto CMake. Consulte [referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md) para obtener más información sobre las configuraciones predefinidas. Puede agregar cualquier número de configuraciones predefinidas o personalizadas al archivo. 

Un elemento `configuration` tiene las siguientes propiedades:

- `addressSDanitizerEnabled`: si `true` compila el programa con el saneado de direcciones (experimental en Windows). En Linux, compile con-fno-ignore-Frame-Pointer y el nivel de optimización del compilador-os o-OO para obtener los mejores resultados.
- `addressSanitizerRuntimeFlags`: marcas en tiempo de ejecución pasadas a AddressSanitizer a través de la variable de entorno ASAN_OPTIONS. Formato: indicador1 = valor: dedador = valor2.
- `buildCommandArgs`: especifica los modificadores de compilación nativos que se pasan a CMake después de --build --. Por ejemplo, pasar -v cuando se usa el generador Ninja obliga a Ninja a dar como resultado líneas de comandos. Vea [Argumentos de la línea de comandos de Ninja](#ninja) para más información sobre los comandos de Ninja.
- `buildRoot`: especifica el directorio en el que CMake genera los scripts de compilación para el generador elegido.  Se asigna al modificador **-DCMAKE_BINARY_DIR** y especifica dónde se va a crear la caché de CMake. Si la carpeta no existe, se creará. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`y `${env.VARIABLE}`.
- `cacheGenerationCommand`: especifica una herramienta de línea de comandos y argumentos, por ejemplo, *gencache. bat Debug* para generar la memoria caché. El comando se ejecuta desde el Shell en el entorno especificado para la configuración cuando el usuario solicita la regeneración explícitamente, o se modifica un archivo archivo CMakeLists. txt o CMakeSettings. JSON.
- `cacheRoot`: especifica la ruta de acceso a una caché de CMake. El directorio debe contener un archivo CMakeCache.txt existente.
- `clangTidyChecks`: lista separada por comas de warnigns que se pasará a Clang-ordenado; se permiten caracteres comodín y el prefijo '-' quitará las comprobaciones.
- `cmakeCommandArgs`: especifica las opciones adicionales de la línea de comandos que se pasan a CMake cuando se invoca para generar la caché.
- `cmakeToolchain`: especifica el archivo de la cadena de herramientas. Para pasarlo a CMake se usa -DCMAKE_TOOLCHAIN_FILE.
- `codeAnalysisRuleset`: especifica el conjunto de reglas que se usa al ejecutar el análisis de código. Puede ser una ruta de acceso completa o el nombre de un archivo de conjunto de reglas que Visual Studio ha instalado.
- `configurationType`: especifica la configuración del tipo de compilación del generador seleccionado. Puede ser uno de los siguientes:

  - Depurar
  - Versión
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs`: especifica opciones adicionales de la línea de comandos que se pasan a CTest al ejecutar las pruebas.
- `description`: descripción de esta configuración que aparecerá en los menús.
- `enableClangTidyCodeAnalysis`: Use Clang para el análisis de código.
- `enableMicrosoftCodeAnalysis`: usar herramientas de análisis de código de Microsoft para el análisis de código.
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

Para especificar un generador de Visual Studio en Visual Studio 2017, abra el desde el menú principal eligiendo **CMake | Cambie la configuración de CMake**. Elimine "Ninja" y escriba "V". Esto activa IntelliSense, lo que permite elegir el generador que quiera.

Para especificar un generador de Visual Studio en Visual Studio 2019, haga clic con el botón derecho en el archivo *archivo CMakeLists. txt* en **Explorador de soluciones** y elija **CMake Settings for Project** > **Show Advanced Settings** > **CMake generator**.

Cuando la configuración activa especifica un generador de Visual Studio, de forma predeterminada se invoca MSBuild.exe con argumentos `-m -v:minimal`. Para personalizar la compilación, en el archivo *CMakeSettings. JSON* , puede especificar argumentos de [línea de comandos de MSBuild](../build/reference/msbuild-visual-cpp-overview.md) adicionales para pasarlos al sistema de compilación a través de la propiedad `buildCommandArgs`:

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType`: especifica la configuración del tipo de compilación del generador seleccionado. Puede ser uno de los siguientes:

  - Depurar
  - Versión
  - MinSizeRel
  - RelWithDebInfo
 
- `buildRoot`: especifica el directorio en el que CMake genera los scripts de compilación para el generador elegido.  Asigna al modificador **-DCMAKE_BINARY_DIR** y especifica dónde se creará *CMakeCache. txt* . Si la carpeta no existe, se crea. Las macros admitidas son `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `installRoot`: especifica el directorio en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `cmakeCommandArgs`: especifica las opciones de línea de comandos adicionales que se pasan a CMake cuando se invoca para generar los archivos de proyecto.
- `cmakeToolchain`: especifica el archivo de la cadena de herramientas. Para pasarlo a CMake se usa -DCMAKE_TOOLCHAIN_FILE.
- `buildCommandArgs`: especifica los modificadores de compilación nativos que se pasan a CMake después de --build --. Por ejemplo, pasar -v cuando se usa el generador Ninja obliga a Ninja a dar como resultado líneas de comandos. Vea [Argumentos de la línea de comandos de Ninja](#ninja) para más información sobre los comandos de Ninja.
- `ctestCommandArgs`: especifica opciones adicionales de la línea de comandos que se pasan a CTest al ejecutar las pruebas.
- `codeAnalysisRuleset`: especifica el conjunto de reglas que se usa al ejecutar el análisis de código. Puede ser una ruta de acceso completa o el nombre de un archivo de conjunto de reglas que Visual Studio ha instalado.
- `inheritEnvironments`: especifica uno o más entornos de compilador de los que depende esta configuración. Puede ser cualquier entorno personalizado, o bien uno de los entornos predefinidos. Para obtener más información, vea [Entornos](#environments).
- `installRoot`: especifica el directorio en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
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

- `cacheRoot`: especifica la ruta de acceso a una caché de CMake. Este directorio debe contener un archivo *CMakeCache. txt* existente.
- `name`: nombres de la configuración.  Consulte [referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md) para obtener más información sobre las configuraciones predefinidas.
- `wslPath`: ruta de acceso al iniciador de una instancia del subsistema de Windows para Linux.

### <a name="additional-settings-for-cmake-linux-projects"></a>Configuraciones adicionales para proyectos CMake de Linux. 

- `remoteMachineName`: especifica el nombre del equipo Linux remoto que hospeda CMake, compilaciones y el depurador. Use el Administrador de conexiones para agregar nuevas máquinas Linux. Entre las macros admitidas se incluye `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity`: especifica el nivel de detalle de la operación de copia de origen en la máquina remota. Puede ser " Normal", "Detallado" o "Diagnóstico".
- `remoteCopySourcesConcurrentCopies`: especifica el número de copias simultáneas que se usan durante la sincronización de los orígenes en el equipo remoto (solo SFTP).
- `remoteCopySourcesMethod`: especifica el método para copiar los archivos en la máquina remota. Puede ser "rsync" o "sftp".
- `remoteCMakeListsRoot`: especifica el directorio del equipo remoto que contiene el proyecto de CMake. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `remoteBuildRoot`: especifica el directorio de la máquina remota en el que CMake genera los scripts de compilación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `remoteInstallRoot`: especifica el directorio de la máquina remota en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`, donde `VARIABLE` es una variable de entorno que se ha definido en el nivel de sistema, usuario o sesión.
- `remoteCopySources`: un `boolean` que especifica si Visual Studio debe copiar los archivos de código fuente en el equipo remoto. El valor predeterminado es true. Establézcalo en false si administra usted mismo la sincronización de archivos.
- `remoteCopyBuildOutput`: un `boolean` que especifica si se deben copiar los resultados de la compilación del sistema remoto.
- `rsyncCommandArgs`: especifica un conjunto de opciones adicionales de la línea de comandos que se pasan a rsync.
- `remoteCopySourcesExclusionList`: un `array` que especifica una lista de rutas de acceso que se van a excluir al copiar archivos de código fuente ': una ruta de acceso puede ser el nombre de un archivo o un directorio, o una ruta de acceso relativa a la raíz de la copia. Los caracteres comodín \\\"*\\\" y \\\"?\\\" se pueden usar para la coincidencia de patrones globales.
- `cmakeExecutable`: especifica la ruta de acceso completa al ejecutable del programa CMake, incluidos el nombre y la extensión del archivo.
- `remotePreGenerateCommand`: especifica el comando que se ejecutará antes de ejecutar CMake para analizar el archivo *archivo CMakeLists. txt* .
- `remotePrebuildCommand`: especifica el comando que debe ejecutarse en la máquina remota antes de compilar.
- `remotePostbuildCommand`: especifica el comando que debe ejecutarse en la máquina remota después de compilar.
- `variables`: contiene un par nombre-valor de variables de CMake que se pasan como **-D** *_nombre_=_valor_* a CMake. Si las instrucciones de compilación del proyecto CMake especifican la adición de las variables directamente al archivo *CMakeCache. txt* , se recomienda agregarlas aquí en su lugar. En el siguiente ejemplo se muestra cómo especificar los pares nombre-valor para el conjunto de herramientas MSVC 14.14.26428:

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

Tenga en cuenta que si no define el `"type"`, se asumirá el tipo de `"STRING"` de forma predeterminada.

## <a name="environments"></a>Entorno

Un *entorno* encapsula las variables de entorno que se establecen en el proceso que Visual Studio usa para invocar CMake. exe. En el caso de los proyectos de MSVC, las variables son las que se establecen en un [símbolo del sistema para desarrolladores](building-on-the-command-line.md) para una plataforma específica. Por ejemplo, el entorno de `msvc_x64_x64` es igual que ejecutar el **símbolo del sistema para desarrolladores para vs 2017** o **Símbolo del sistema para desarrolladores para vs 2019** con los argumentos **-Arch = AMD64-host_arch = AMD64** . Puede usar la sintaxis de `env.{<variable_name>}` en *CMakeSettings. JSON* para hacer referencia a las variables de entorno individuales, por ejemplo, para construir rutas de acceso a carpetas.  Se proporcionan los siguientes entornos predefinidos:

- linux_arm: se dirige a ARM Linux de forma remota.
- linux_x64: de destino x64 Linux de forma remota.
- linux_x86: tener como destino linux x86 de forma remota.
- msvc_arm: destinar ventanas de ARM con el compilador MSVC.
- msvc_arm_x64: destinar ventanas de ARM con el compilador MSVC de 64 bits.
- msvc_arm64: ARM64 de destino de Windows con el compilador de MSVC.
- msvc_arm64_x64: ARM64 de destino de Windows con el compilador de MSVC de 64 bits.
- msvc_x64: destinar Windows x64 con el compilador MSVC.
- msvc_x64_x64: destinar Windows x64 con el compilador MSVC de 64 bits.
- msvc_x86: se destina a Windows x86 con el compilador MSVC.
- msvc_x86_x64: se dirige a Windows x86 con el compilador MSVC de 64 bits.

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>Acceso a las variables de entorno desde archivo CMakeLists. txt

En un archivo archivo CMakeLists. txt, la sintaxis `$ENV{variable_name}`hace referencia a todas las variables de entorno. Para ver las variables disponibles para un entorno, abra el símbolo del sistema correspondiente y escriba `SET`. Parte de la información de las variables de entorno también está disponible a través de las variables CMake del sistema introspección, pero puede que le resulte más cómodo usar la variable de entorno. Por ejemplo, la versión del compilador MSVC o la versión Windows SDK se recuperan fácilmente a través de las variables de entorno.

### <a name="custom-environment-variables"></a>Variables de entorno personalizadas

En `CMakeSettings.json`, puede definir variables de entorno personalizadas globalmente o por configuración en la matriz de `environments`. Un entorno personalizado es una manera cómoda de agrupar un conjunto de propiedades que se pueden usar en lugar de un entorno predefinido, o para extender o modificar un entorno predefinido. Cada elemento de la matriz `environments` consta de lo siguiente:

- `namespace`: son los nombres de entorno, para que se pueda hacer referencia a sus variables desde una configuración con el formato `namespace.variable`. El objeto de entorno predeterminado se denomina `env` y se rellena con ciertas variables de entorno del sistema, incluidas `%USERPROFILE%`.
- `environment`: identifica de forma única este grupo de variables. Permite que el grupo se herede más adelante en una entrada `inheritEnvironments`.
- `groupPriority`: un entero que especifica la prioridad de estas variables cuando se evalúan. Los elementos con un número más alto se evalúan primero.
- `inheritEnvironments`: matriz de valores que especifican el conjunto de entornos que este grupo hereda. Esta característica permite heredar entornos predeterminados y crear variables de entorno personalizadas que se pasan a CMake.exe cuando se ejecuta.

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

Las siguientes macros se pueden usar en *CMakeSettings. JSON*:

- `${workspaceRoot}`: ruta de acceso completa de la carpeta del área de trabajo
- `${workspaceHash}`: hash de ubicación del área de trabajo; es útil para crear un identificador único para el área de trabajo actual (por ejemplo, para usarlo en las rutas de acceso de carpeta).
- `${projectFile}`: la ruta de acceso completa del archivo CMakeLists.txt raíz.
- `${projectDir}`: la ruta de acceso completa de la carpeta del archivo CMakeLists.txt raíz.
- `${thisFile}`: ruta de acceso completa del archivo `CMakeSettings.json`.
- `${name}`: el nombre de la configuración
- `${generator}`: el nombre del generador de CMake que se usa en esta configuración.

Todas las referencias a las variables de entorno y macros de *CMakeSettings. JSON* se expanden antes de que se pasen a la línea de comandos de CMake. exe.

## <a name="ninja"></a> Argumentos de la línea de comandos de Ninja

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
