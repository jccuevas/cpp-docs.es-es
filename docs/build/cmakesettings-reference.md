---
title: Referencia del esquema de CMakeSettings.json
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: cc9b9a788f17e9257bed628024e3f65dfc89fb23
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67516383"
---
# <a name="cmakesettingsjson-schema-reference"></a>Referencia del esquema de CMakeSettings.json

El **cmakesettings.json** archivo contiene información que especifica cómo Visual Studio debe interactuar con CMake para compilar un proyecto para una plataforma específica. El archivo almacena información como variables de entorno o argumentos para el entorno cmake.exe. Puede editarlo de forma directa o usar el **Editor de configuración de CMake** (Visual Studio 2019 y versiones posteriores). Para más información sobre el editor, vea [Personalización de la configuración de compilación de CMake en Visual Studio](customize-cmake-settings.md).

## <a name="environments"></a>Entornos

La matriz `environments` contiene una lista de `items` de tipo `object` que definen un "entorno" de conjunto de herramientas del compilador. Un entorno puede usarse para aplicar un conjunto de variables a un elemento `configuration`. Cada elemento de la matriz `environments` consta de lo siguiente:

- `namespace`: son los nombres de entorno, para que se pueda hacer referencia a sus variables desde una configuración con el formato `namespace.variable`. El objeto de entorno predeterminado se denomina `env` y se rellena con ciertas variables de entorno del sistema, entre las que se incluye `%USERPROFILE%`.
- `environment`: identifica de forma única este grupo de variables. Permite que el grupo se herede más adelante en una entrada `inheritEnvironments`.
- `groupPriority`: entero que especifica la prioridad de estas variables al evaluarlas. Los elementos con un número más alto se evalúan primero.
- `inheritEnvironments`: matriz de valores que especifican el conjunto de entornos que este grupo hereda. Esta característica permite heredar entornos predeterminados y crear variables de entorno personalizadas que se pasan a CMake.exe cuando se ejecuta.

   ```json
   "inheritEnvironments": [ "msvc_x64_x64" ]
   ```

   El ejemplo anterior equivale a ejecutar el **Símbolo del sistema para desarrolladores de VS 2017** o el **Símbolo del sistema para desarrolladores de VS 2019** con los argumentos **-arch=amd64 -host_arch=amd64**. Se puede usar cualquier entorno personalizado, o bien los siguientes entornos predefinidos:
 
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

Como Ninja está diseñado para velocidades de compilación rápidas en lugar de flexibilidad y funcionamiento, se establece como el valor predeterminado. Pero es posible que algunos proyectos de CMake no se puedan generar correctamente mediante Ninja. Si esto ocurre, puede indicar a CMake que en su lugar genere un proyecto de Visual Studio.

Para especificar un generador de Visual Studio en Visual Studio 2017, abra el archivo `CMakeSettings.json` en el menú principal mediante **CMake | Cambiar configuración de CMake**. Elimine "Ninja" y escriba "V". Esto activa IntelliSense, lo que permite elegir el generador que quiera.

Para especificar un generador de Visual Studio en Visual Studio 2019, haga clic con el botón derecho en el archivo CMakeLists.txt en el **Explorador de soluciones** y seleccione **Configuración de CMake para el proyecto** > **Mostrar la configuración avanzada** > **Generador de CMake**.

Cuando la configuración activa especifica un generador de Visual Studio, de forma predeterminada se invoca MSBuild.exe con argumentos `-m -v:minimal`. Para personalizar la compilación, en el archivo `CMakeSettings.json`, puede especificar [argumentos adicionales de la línea de comandos de MSBuild](../build/reference/msbuild-visual-cpp-overview.md) que se pasarán al sistema de compilación a través de la propiedad `buildCommandArgs`:

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType`: especifica la configuración del tipo de compilación del generador seleccionado. Puede ser uno de los siguientes:
 
  - Depuración
  - Release
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`: especifica uno o más entornos de compilador de los que depende esta configuración. Puede ser cualquier entorno personalizado, o bien uno de los entornos predefinidos.
- `buildRoot`: especifica el directorio en el que CMake genera los scripts de compilación para el generador elegido.  Se asigna al modificador **-DCMAKE_BINARY_DIR** y especifica dónde se va a crear la caché de CMake. Si la carpeta no existe, se crea. Las macros admitidas son `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `installRoot`: especifica el directorio en el que CMake genera los destinos de instalación para el generador elegido. Entre las macros admitidas se incluyen `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}` y `${env.VARIABLE}`.
- `cmakeCommandArgs`: especifica las opciones adicionales de la línea de comandos que se pasan a CMake cuando se invoca para generar la caché.
- `cmakeToolchain`: especifica el archivo de la cadena de herramientas. Para pasarlo a CMake se usa -DCMAKE_TOOLCHAIN_FILE.
- `buildCommandArgs`: especifica los modificadores de compilación nativos que se pasan a CMake después de --build --. Por ejemplo, pasar -v cuando se usa el generador Ninja obliga a Ninja a dar como resultado líneas de comandos. Vea [Argumentos de la línea de comandos de Ninja](#ninja) para más información sobre los comandos de Ninja.
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

### <a name="additional-settings-for-cmake-linux-projects"></a>Configuraciones adicionales para proyectos CMake de Linux. 

- `remoteMachineName`: especifica el nombre del equipo Linux remoto que hospeda CMake, compilaciones y el depurador. Use el Administrador de conexiones para agregar nuevas máquinas Linux. Entre las macros admitidas se incluye `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity`: especifica el nivel de detalle de la operación de copia de origen en la máquina remota. Puede ser " Normal", "Detallado" o "Diagnóstico".
- `remoteCopySourcesConcurrentCopies`: especifica el número de copias simultáneas que se usan durante la sincronización de los orígenes en el equipo remoto (sólo sftp).
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
- `variables`: contiene un par nombre-valor de variables de CMake que se pasan como **-D** *_nombre_=_valor_* a CMake. Si las instrucciones de compilación del proyecto de CMake especifican la adición de las variables directamente al archivo de caché de CMake, en su lugar se recomienda agregarlas aquí. En el siguiente ejemplo se muestra cómo especificar los pares nombre-valor para el conjunto de herramientas MSVC 14.14.26428:

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

Tenga en cuenta que si no se define `"type"`, se asumirá el tipo "STRING" de forma predeterminada.

## <a name="environment-variables"></a>Variables de entorno

`CMakeSettings.json` también admite el consumo de variables de entorno en cualquiera de sus propiedades mencionadas anteriormente. La sintaxis que se usa es `${env.FOO}` para expandir la variable de entorno %FOO%.

También se puede acceder a las macros integradas dentro de este archivo:

- `${workspaceRoot}`: proporciona la ruta de acceso completa de la carpeta de área de trabajo.
- `${workspaceHash}`: hash de ubicación del área de trabajo; es útil para crear un identificador único para el área de trabajo actual (por ejemplo, para usarlo en las rutas de acceso de carpeta).
- `${projectFile}`: la ruta de acceso completa del archivo CMakeLists.txt raíz.
- `${projectDir}`: la ruta de acceso completa de la carpeta del archivo CMakeLists.txt raíz.
- `${thisFile}`: ruta de acceso completa del archivo `CMakeSettings.json`.
- `${name}`: el nombre de la configuración
- `${generator}`: el nombre del generador de CMake que se usa en esta configuración.


### <a name="custom-environment-variables"></a>Variables de entorno personalizadas

En `CMakeSettings.json`, se pueden definir variables de entorno personalizadas de manera global o por cada configuración en la propiedad **environments**. En el ejemplo siguiente se define una variable global, **BuildDir**, que se hereda en las configuraciones x86-Debug y x64-Debug. En cada configuración se usa la variable para especificar el valor de la propiedad **buildRoot** para esa configuración. Tenga en cuenta también cómo se usa la propiedad **inheritEnvironments** en cada configuración para especificar una variable que solo se aplica a esa configuración.

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
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

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




