---
title: Referencia de CppProperties. JSON
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: d59fca412a26d08f88ccbda20a2c0444cf33b1cb
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422845"
---
# <a name="cpppropertiesjson-reference"></a>Referencia de CppProperties. JSON

Los proyectos de carpeta abiertos que no usan CMake pueden almacenar los valores de configuración del proyecto de IntelliSense en un archivo *CppProperties. JSON* . (Los proyectos de CMake usan un archivo [CMakeSettings. JSON](customize-cmake-settings.md) ). Una configuración consta de pares de nombre/valor y define #include trazados, modificadores de compilador y otros parámetros. Consulte [Abrir proyectos de carpeta C++ para](open-folder-projects-cpp.md) obtener más información sobre cómo agregar configuraciones en un proyecto de carpeta abierta. En las secciones siguientes se resumen las diversas opciones de configuración. Para obtener una descripción completa del esquema, vaya a *CppProperties_schema. JSON*, cuya ruta de acceso completa se proporciona en la parte superior del editor de código cuando *CppProperties. JSON* está abierto.

## <a name="configuration-properties"></a>Propiedades de configuración

Una configuración puede tener cualquiera de las propiedades siguientes:

|||
|-|-|
|`inheritEnvironments`| Especifica qué entornos se aplican a esta configuración.|
|`name`|El nombre de configuración que aparecerá en la C++ lista desplegable configuración|
|`includePath`|Lista separada por comas de las carpetas que deben especificarse en la ruta de acceso de inclusión (se asigna a/I para la mayoría de los compiladores)|
|`defines`|Lista de macros que se deben definir (se asigna a /D para la mayoría de los compiladores).|
|`compilerSwitches`|Uno o varios modificadores adicionales que pueden influir en el comportamiento de IntelliSense.|
|`forcedInclude`|Encabezado que se va a incluir de forma automática en todas las unidades de compilación (se asigna a /FI para MSVC o -include para clang).|
|`undefines`|Lista de macros de las que se van a anular las definiciones (se asigna a /U para MSVC).|
|`intelliSenseMode`|Motor de IntelliSense que se va usar. Puede especificar una de las variantes predefinidas específicas de la arquitectura para MSVC, GCC o Clang.|
|`environments`|Conjuntos de variables definidos por el usuario que se comportan como variables de entorno en un símbolo del sistema y a los que se tiene acceso con $ {env.<VARIABLE>} macro.|

### <a name="intellisensemode-values"></a>valores de omiten

El editor de código muestra las opciones disponibles cuando empieza a escribir:

![Abrir carpeta de IntelliSense](media/open-folder-intellisense-mode.png "Abrir carpeta de IntelliSense")

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
- Linux-GCC-ARM

Nota: los valores `msvc-x86` y `msvc-x64` solo se admiten por motivos de herencia. En su lugar, use las variantes de `windows-msvc-*`.

## <a name="pre-defined-environments"></a>Entornos predefinidos

Visual Studio proporciona los siguientes entornos predefinidos para C++ Microsoft que se asignan al símbolo del sistema para desarrolladores correspondiente. Al heredar uno de estos entornos, puede hacer referencia a cualquiera de las variables de entorno con la propiedad global `env` con esta sintaxis de macro: $ {env.\<VARIABLE >}.

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

## <a name="user_defined_environments"></a>Entornos definidos por el usuario

Opcionalmente, puede usar la propiedad `environments` para definir conjuntos de variables en *CppProperties. JSON* , ya sea global o por configuración. Estas variables se comportan como variables de entorno en el contexto de un proyecto de carpeta abierta y se puede tener acceso a ella con la sintaxis $ {env.\<VARIABLE >} de *Tasks. vs. JSON* y *Launch. vs. JSON* después de que se hayan definido aquí. Sin embargo, no se establecen necesariamente como variables de entorno reales en cualquier símbolo del sistema que Visual Studio usa internamente.

**Visual Studio 2019 versión 16,4 y versiones posteriores:** Las variables específicas de la configuración definidas en *CppProperties. JSON* se seleccionan automáticamente por los destinos de depuración y las tareas sin necesidad de establecer `inheritEnvironments`. Los destinos de depuración se inician automáticamente con el entorno que especifique en *CppProperties. JSON*.

**Visual Studio 2019 versión 16,3 y versiones anteriores:** Cuando se utiliza un entorno, debe especificarlo en la propiedad `inheritsEnvironments` aunque el entorno se defina como parte de la misma configuración. la propiedad `environment` especifica el nombre del entorno. En el ejemplo siguiente se muestra una configuración de ejemplo para habilitar IntelliSense para GCC en una instalación de MSYS2. Observe cómo la configuración define y hereda el entorno de `mingw_64` y cómo la propiedad `includePath` puede tener acceso a la variable `INCLUDE`.

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

Cuando se define una propiedad **Environments** dentro de una configuración, reemplaza todas las variables globales del mismo nombre.

## <a name="built-in-macros"></a>Macros integradas

Tiene acceso a las siguientes macros integradas dentro de *CppProperties. JSON*:

|||
|-|-|
|`${workspaceRoot}`| La ruta de acceso completa a la carpeta del área de trabajo|
|`${projectRoot}`| La ruta de acceso completa a la carpeta donde se coloca *CppProperties. JSON*|
|`${env.vsInstallDir}`| La ruta de acceso completa a la carpeta donde está instalada la instancia en ejecución de Visual Studio|

### <a name="example"></a>Ejemplo

Si el proyecto tiene una carpeta include y también incluye *Windows. h* y otros encabezados comunes de la Windows SDK, puede que desee actualizar el archivo de configuración *CppProperties. JSON* con lo siguiente:

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

Si no ve el IntelliSense que espera, puede solucionar el problema en **herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **avanzadas** y establecer **Habilitar registro** en **true**. Para empezar, pruebe a establecer el **nivel de registro** en 5 y registre los **filtros** en 8.

![Registro de diagnóstico](media/diagnostic-logging.png)

La salida se canaliza al **ventana de salida** y está visible al elegir **Mostrar salida de: registro visual C++** . La salida contiene, entre otras cosas, la lista de rutas de acceso de inclusión reales que IntelliSense está intentando usar. Si las rutas de acceso no coinciden con las de *CppProperties. JSON*, intente cerrar la carpeta y eliminar la subcarpeta *. vs* que contiene los datos de exploración almacenados en caché.

Para solucionar problemas de errores de IntelliSense causados por la ausencia de rutas de acceso de inclusión, abra la **Lista de errores** y filtre los resultados por "Solo IntelliSense" y el código de error E1696 "no se puede abrir el archivo de código fuente...".
