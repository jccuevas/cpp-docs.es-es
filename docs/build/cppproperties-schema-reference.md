---
title: Referencia CppProperties.json
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328718"
---
# <a name="cpppropertiesjson-reference"></a>Referencia CppProperties.json

Los proyectos de carpeta abierta que no usan CMake pueden almacenar la configuración del proyecto para IntelliSense en un archivo *CppProperties.json.* (Los proyectos DeC usan un archivo [CMakeSettings.json.)](customize-cmake-settings.md) Una configuración consta de pares nombre/valor y define rutas de acceso #include, modificadores del compilador y otros parámetros. Consulte Abrir proyectos de [carpeta spara C++](open-folder-projects-cpp.md) para obtener más información sobre cómo agregar configuraciones en un proyecto de carpeta abierta. En las secciones siguientes se resumen los distintos ajustes. Para obtener una descripción completa del esquema, vaya a *CppProperties_schema.json*, cuya ruta de acceso completa se indica en la parte superior del editor de código cuando *CppProperties.json* está abierto.

## <a name="configuration-properties"></a>Propiedades de configuración

Una configuración puede tener cualquiera de las propiedades siguientes:

|||
|-|-|
|`inheritEnvironments`| Especifica qué entornos se aplican a esta configuración.|
|`name`|El nombre de configuración que aparecerá en el menú desplegable de configuración de C++|
|`includePath`|Una lista separada por comas de carpetas que se deben especificar en la ruta de acceso include (se asigna a /I para la mayoría de los compiladores)|
|`defines`|Lista de macros que se deben definir (se asigna a /D para la mayoría de los compiladores).|
|`compilerSwitches`|Uno o varios modificadores adicionales que pueden influir en el comportamiento de IntelliSense.|
|`forcedInclude`|Encabezado que se va a incluir de forma automática en todas las unidades de compilación (se asigna a /FI para MSVC o -include para clang).|
|`undefines`|Lista de macros de las que se van a anular las definiciones (se asigna a /U para MSVC).|
|`intelliSenseMode`|Motor de IntelliSense que se va usar. Puede especificar una de las variantes específicas de la arquitectura predefinidas para MSVC, gcc o Clang.|
|`environments`|Conjuntos definidos por el usuario de variables que se comportan como variables\< de entorno en un símbolo del sistema y se accede a ellos con el valor de $ . Macro variable>.|

### <a name="intellisensemode-values"></a>valores intelliSenseMode

El editor de código muestra las opciones disponibles cuando comienza a escribir:

![Abrir carpeta IntelliSense](media/open-folder-intellisense-mode.png "Abrir carpeta IntelliSense")

Estos son los valores admitidos:

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

Nota: Los `msvc-x86` `msvc-x64` valores y se admiten solo por razones heredadas. Utilice `windows-msvc-*` las variantes en su lugar.

## <a name="pre-defined-environments"></a>Entornos predefinidos

Visual Studio proporciona los siguientes entornos predefinidos para Microsoft C++ que se asignan al símbolo del sistema para desarrolladores correspondiente. Cuando se hereda uno de estos entornos, se puede hacer `env` referencia a cualquiera de las\< variables de entorno mediante la propiedad global con esta sintaxis de macro: $-env.> VARIABLE.

|Nombre de la variable|Descripción|
|-----------|-----------------|
|vsdev|El entorno de Visual Studio predeterminado.|
|msvc_x86|Compilar para x86 con herramientas de x86.|
|msvc_x64|Compilar para AMD64 con herramientas de 64 bits.|
|msvc_arm|Compilar para ARM con herramientas de x86.|
|msvc_arm64|Compilar para ARM64 con herramientas de x86.|
|msvc_x86_x64|Compilar para AMD64 con herramientas de x86.|
|msvc_arm_x64|Compilar para ARM con herramientas de 64 bits.|
|msvc_arm64_x64|Compilar para ARM64 con herramientas de 64 bits.|

Cuando se instala la carga de trabajo de Linux, los entornos siguientes están disponibles para seleccionar como destino Linux y WSL de forma remota:

|Nombre de la variable|Descripción|
|-----------|-----------------|
|linux_x86|Se destina a Linux x86 de forma remota.|
|linux_x64|Se destina a Linux x64 de forma remota.|
|linux_arm|Se destina a Linux ARM de forma remota.|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>Entornos definidos por el usuario

Opcionalmente, puede `environments` utilizar la propiedad para definir conjuntos de variables en *CppProperties.json* globalmente o por configuración. Estas variables se comportan como variables de entorno en el contexto de un\< proyecto de carpeta abierta y se puede acceder a ellas con el valor $ . Variable> sintaxis de *tasks.vs.json* y *launch.vs.json* después de que se definan aquí. Sin embargo, no se establecen necesariamente como variables de entorno reales en cualquier símbolo del sistema que Visual Studio usa internamente.

**Visual Studio 2019 versión 16.4 y versiones posteriores:** Las variables específicas de configuración definidas en *CppProperties.json* se seleccionan `inheritEnvironments`automáticamente mediante destinos de depuración y tareas sin necesidad de establecer . Los destinos de depuración se inician automáticamente con el entorno especificado en *CppProperties.json*.

**Visual Studio 2019 versión 16.3 y versiones anteriores:** Cuando se consume un entorno, debe especificarlo en la `inheritsEnvironments` propiedad incluso si el entorno se define como parte de la misma configuración; la `environment` propiedad especifica el nombre del entorno. En el ejemplo siguiente se muestra una configuración de ejemplo para habilitar IntelliSense para GCC en una instalación MSYS2. Observe cómo la configuración define `mingw_64` y hereda `includePath` el entorno `INCLUDE` y cómo la propiedad puede tener acceso a la variable.

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

Cuando se define una propiedad **environments** dentro de una configuración, se reemplazan las variables globales del mismo nombre.

## <a name="built-in-macros"></a>Macros integradas

Tiene acceso a las siguientes macros integradas dentro de *CppProperties.json:*

|||
|-|-|
|`${workspaceRoot}`| La ruta de acceso completa a la carpeta del área de trabajo|
|`${projectRoot}`| La ruta de acceso completa a la carpeta donde se coloca *CppProperties.json*|
|`${env.vsInstallDir}`| La ruta de acceso completa a la carpeta donde está instalada la instancia en ejecución de Visual Studio|

### <a name="example"></a>Ejemplo

Si el proyecto tiene una carpeta include y también incluye *windows.h* y otros encabezados comunes del Windows SDK, es posible que desee actualizar el archivo de configuración *CppProperties.json* con lo siguiente incluye:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%` y `%VCToolsInstallDir%` no se establecen como variables de entorno globales, por lo que debe asegurarse de iniciar devenv.exe desde un Símbolo del sistema para desarrolladores que defina estas variables. (Escriba "desarrollador" en el menú de inicio de Windows).

## <a name="troubleshoot-intellisense-errors"></a>Solución de errores de IntelliSense

Si no ve el IntelliSense que espera, puede **Tools** > solucionar los problemas en**Opciones** > de herramientas**Editor** > de texto**C/C++** > **Advanced** y establecer **Habilitar registro** en **true**. Para empezar, intente establecer **el nivel** de registro en 5 y los **filtros** de registro en 8.

![Registro de diagnóstico](media/diagnostic-logging.png)

La salida se canaliza a la ventana de **salida** y es visible cuando se elige **Mostrar salida desde: Visual C++ Log**. La salida contiene, entre otras cosas, la lista de rutas de acceso de inclusión reales que IntelliSense está intentando utilizar. Si las rutas de acceso no coinciden con las de *CppProperties.json,* intente cerrar la carpeta y eliminar la subcarpeta *.vs* que contiene datos de exploración almacenados en caché.

Para solucionar problemas de errores de IntelliSense causados por la ausencia de rutas de acceso de inclusión, abra la **Lista de errores** y filtre los resultados por "Solo IntelliSense" y el código de error E1696 "no se puede abrir el archivo de código fuente...".
