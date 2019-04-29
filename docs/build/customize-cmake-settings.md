---
title: Personalización de la configuración de compilación de CMake en Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 4864e094ab967a563b153fa79fd0bf5c375f40f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274632"
---
# <a name="customize-cmake-build-settings"></a>Personalización de la configuración de compilación de CMake

Visual Studio proporciona varias configuraciones de CMake que definen cómo se invoca CMake.exe para crear una caché de CMake para un proyecto determinado. Para agregar una configuración nueva, haga clic en el menú desplegable Configuración de la barra de herramientas y seleccione **Administrar configuraciones**:

   ![Administrar configuraciones de CMake](media/cmake-manage-configurations.png)

Puede elegir una de las opciones de la lista de configuraciones predefinidas:

   ![Configuraciones predefinidas de CMake](media/cmake-configurations.png)

La primera vez que seleccione una configuración, Visual Studio creará un archivo `CMakeSettings.json` en la carpeta raíz del proyecto. Este archivo se usa para volver a crear el archivo de caché de CMake, por ejemplo después de una operación **Limpiar**. 

Para agregar una configuración adicional, haga clic con el botón derecho en `CMakeSettings.json` y elija **Agregar configuración**. 

   ![Agregar configuración de CMake](media/cmake-add-configuration.png "CMake Add Configuration")

IntelliSense de JSON ayuda a editar el archivo `CMakeSettings.json`:

   ![IntelliSense de JSON para CMake](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

También puede editar el archivo mediante el **Editor de configuración de CMake**. Haga clic con el botón derecho en `CMakeSettings.json` en el **Explorador de soluciones** y seleccione **Editar configuración de CMake**. También puede seleccionar **Administrar configuraciones** en la lista desplegable de configuraciones en la parte superior de la ventana del editor. 

Además, puede editar `CMakeSettings.json` directamente para crear configuraciones personalizadas. En el ejemplo siguiente se muestra un ejemplo de configuración, que se puede usar como punto de partida:

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

- **name**: el nombre que aparece en la lista desplegable de configuración de C++. La macro `${name}` le permite usar este valor al crear otros valores de propiedad, como las rutas de acceso. Para obtener un ejemplo, vea la definición de **buildRoot** en `CMakeSettings.json`.

- **generator**: se asigna al modificador **-G** de CMake y especifica el generador que se va a usar. Esta propiedad también se puede usar como una macro, `${generator}`, al crear otros valores de propiedad. En la actualidad, Visual Studio admite los generadores de CMake siguientes:

  - "Ninja"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 ARM"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 15 2017 Win64"

  Como Ninja está diseñado para velocidades de compilación rápidas en lugar de flexibilidad y funcionamiento, se establece como el valor predeterminado. Pero es posible que algunos proyectos de CMake no se puedan generar correctamente mediante Ninja. Si esto ocurre, puede indicar a CMake que en su lugar genere un proyecto de Visual Studio.

  Para especificar un generador de Visual Studio, abra el archivo `CMakeSettings.json` en el menú principal mediante **CMake | Cambiar configuración de CMake**. Elimine "Ninja" y escriba "V". Esto activa IntelliSense, lo que permite elegir el generador que quiera.

  Cuando la configuración activa especifica un generador de Visual Studio, de forma predeterminada se invoca MSBuild.exe con argumentos `-m -v:minimal`. Para personalizar la compilación, en el archivo `CMakeSettings.json`, puede especificar [argumentos adicionales de la línea de comandos de MSBuild](../build/reference/msbuild-visual-cpp-overview.md) que se pasarán al sistema de compilación a través de la propiedad `buildCommandArgs`:
    
    ```json
    "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
    ```

- **buildRoot**: se asigna al modificador **DCMAKE_BINARY_DIR** y especifica dónde se va a crear la caché de CMake. Si la carpeta no existe, se creará.

- **variables**: contiene un par nombre-valor de variables de CMake que se pasan como **-D** *_nombre_=_valor_* a CMake. Si las instrucciones de compilación del proyecto de CMake especifican la adición de las variables directamente al archivo de caché de CMake, en su lugar se recomienda agregarlas aquí. En el siguiente ejemplo se muestra cómo especificar los pares nombre-valor para el conjunto de herramientas MSVC 14.14.26428:

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

Tenga en cuenta que si no se define la `"type"`, se asumirá que el tipo "STRING" de forma predeterminada.

- **cmakeCommandArgs**: especifica los modificadores adicionales que se quieren a pasar a CMake.exe.

- **configurationType**: define el tipo de configuración de compilación para el generador seleccionado. Los valores admitidos actualmente son "Debug", "MinSizeRel", "Release" y "RelWithDebInfo".

- **ctestCommandArgs**: especifica los modificadores adicionales para pasarlos a CTest al ejecutar pruebas.

- **ctestCommandArgs**: especifica los modificadores adicionales para pasarlos al sistema de compilación subyacente. Por ejemplo, pasar -v cuando se usa el generador Ninja obliga a Ninja a dar como resultado líneas de comandos.

Hay disponibles configuraciones adicionales para proyectos de Linux de CMake. Vea [Configuración de un proyecto de CMake de Linux](../linux/cmake-linux-project.md).

## <a name="environment-variables"></a>Variables de entorno

 `CMakeSettings.json` también admite el consumo de variables de entorno en cualquiera de las propiedades mencionadas anteriormente. La sintaxis que se usa es `${env.FOO}` para expandir la variable de entorno %FOO%.
También se puede acceder a las macros integradas dentro de este archivo:

- `${workspaceRoot}`: proporciona la ruta de acceso completa de la carpeta de área de trabajo.
- `${workspaceHash}`: hash de ubicación del área de trabajo; es útil para crear un identificador único para el área de trabajo actual (por ejemplo, para usarlo en las rutas de acceso de carpeta).
- `${projectFile}`: la ruta de acceso completa del archivo CMakeLists.txt raíz.
- `${projectDir}`: la ruta de acceso completa de la carpeta del archivo CMakeLists.txt raíz.
- `${thisFile}`: ruta de acceso completa del archivo `CMakeSettings.json`.
- `${name}`: el nombre de la configuración
- `${generator}`: el nombre del generador de CMake que se usa en esta configuración.

## <a name="ninja-command-line-arguments"></a>Argumentos de la línea de comandos de Ninja

Si no se especifican destinos, se compila el destino "default" (vea el manual).

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
|   -t TOOL  | Se ejecuta una herramienta secundaria (use -t list para enumerar las herramientas secundarias). finaliza las opciones de nivel superior; aún más las marcas se pasan a la herramienta|
|   -w FLAG  | Se ajustan las advertencias (use -w list para enumerar las advertencias).|

## <a name="inherited-environments"></a>Entornos heredados

 `CMakeSettings.json` admite entornos heredados. Esta característica permite (1) heredar los entornos predeterminados y (2) crear variables de entorno personalizadas que se pasan a CMake.exe cuando se ejecuta.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

El ejemplo anterior equivale a ejecutar el **Símbolo del sistema para desarrolladores de VS 2017** con los argumentos **-arch=amd64 -host_arch=amd64**.

En la tabla siguiente se muestran los valores predeterminados:

|Nombre del contexto|Descripción|
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

## <a name="see-also"></a>Vea también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/>
[Conexión al equipo remoto de Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)<br/>
