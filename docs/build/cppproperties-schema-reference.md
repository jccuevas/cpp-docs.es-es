---
title: Referencia de CppProperties.json
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328718"
---
# <a name="cpppropertiesjson-reference"></a>Referencia de CppProperties.json

Los proyectos Abrir carpeta que no usan CMake pueden almacenar valores de configuración de IntelliSense del proyecto en un archivo *CppProperties.json*. (Los proyectos de CMake usan un archivo [CMakeSettings.json](customize-cmake-settings.md)). Una configuración consta de pares nombre-valor y define rutas de acceso #include, modificadores del compilador y otros parámetros. Consulte el artículo sobre los [proyectos Abrir carpeta para C++](open-folder-projects-cpp.md) para obtener más información sobre cómo agregar configuraciones en un proyecto de Abrir carpeta. En las secciones siguientes se resumen las diversas opciones de configuración. Para obtener una descripción completa del esquema, vaya a *CppProperties_schema.json*, cuya ruta de acceso completa se proporciona en la parte superior del editor de código cuando el archivo *CppProperties.json* está abierto.

## <a name="configuration-properties"></a>Propiedades de configuración

Una configuración puede tener cualquiera de las propiedades siguientes:

|||
|-|-|
|`inheritEnvironments`| Especifica qué entornos se aplican a esta configuración.|
|`name`|Nombre de configuración que aparecerá en la lista desplegable de configuración de C++.|
|`includePath`|Lista de carpetas separadas por comas que se deben especificar en la ruta de acceso de inclusión (se asigna a /I para la mayoría de los compiladores).|
|`defines`|Lista de macros que se deben definir (se asigna a /D para la mayoría de los compiladores).|
|`compilerSwitches`|Uno o varios modificadores adicionales que pueden influir en el comportamiento de IntelliSense.|
|`forcedInclude`|Encabezado que se va a incluir de forma automática en todas las unidades de compilación (se asigna a /FI para MSVC o -include para clang).|
|`undefines`|Lista de macros de las que se van a anular las definiciones (se asigna a /U para MSVC).|
|`intelliSenseMode`|Motor de IntelliSense que se va usar. Puede especificar una de las variantes predefinidas específicas de la arquitectura para MSVC, gcc o Clang.|
|`environments`|Conjuntos de variables definidos por el usuario que se comportan como variables de entorno en un símbolo del sistema y a los que se tiene acceso con la macro ${env.\<VARIABLE>}.|

### <a name="intellisensemode-values"></a>Valores de intelliSenseMode

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
- linux-gcc-arm

Nota: Los valores `msvc-x86` y `msvc-x64` solo se admiten por motivos de herencia. En su lugar, use las variantes `windows-msvc-*`.

## <a name="pre-defined-environments"></a>Entornos predefinidos

Visual Studio proporciona los siguientes entornos predefinidos para Microsoft C++ que se asignan al Símbolo del sistema para desarrolladores correspondiente. Al heredar uno de estos entornos, puede hacer referencia a cualquiera de las variables de entorno con la propiedad global `env` mediante la sintaxis de macro ${env.\<VARIABLE>}.

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

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a> Entornos definidos por el usuario

Opcionalmente, puede usar la propiedad `environments` para definir conjuntos de variables en *CppProperties.json* de forma global o por cada configuración. Estas variables se comportan como variables de entorno en el contexto de un proyecto Abrir carpeta y se puede tener acceso a ellas con la sintaxis ${env.\<VARIABLE>} desde *tasks.vs.json* y *launch.vs.json* después de que se hayan definido aquí. Sin embargo, no se establecen necesariamente como variables de entorno reales en los símbolos del sistema que usa Visual Studio internamente.

**Visual Studio 2019, versión 16.4 y posteriores:** Los destinos de depuración y las tareas seleccionan automáticamente las variables específicas de la configuración definidas en *CppProperties.json* sin necesidad de establecer `inheritEnvironments`. Los destinos de depuración se inician automáticamente con el entorno que especifica en *CppProperties.json*.

**Visual Studio 2019, versión 16.3 y anteriores:** Para usar un entorno, debe especificarlo en la propiedad `inheritsEnvironments` aunque el entorno esté definido como parte de la misma configuración. La propiedad `environment` especifica el nombre del entorno. En el ejemplo siguiente se muestra una configuración para habilitar IntelliSense para GCC en una instalación de MSYS2. Observe cómo la configuración define y hereda el entorno `mingw_64` y cómo la propiedad `includePath` puede acceder a la variable `INCLUDE`.

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

Al definir una propiedad **environments** dentro de una configuración, esta reemplaza todas las variables globales con el mismo nombre.

## <a name="built-in-macros"></a>Macros integradas

Dentro de *CppProperties.json*, tiene acceso a las macros integradas siguientes:

|||
|-|-|
|`${workspaceRoot}`| La ruta de acceso completa a la carpeta del área de trabajo.|
|`${projectRoot}`| La ruta de acceso completa a la carpeta donde se coloca *CppProperties.json*.|
|`${env.vsInstallDir}`| La ruta de acceso completa a la carpeta donde está instalada la instancia en ejecución de Visual Studio.|

### <a name="example"></a>Ejemplo

Si el proyecto tiene una carpeta de inclusión y también incluye *windows.h* y otros encabezados comunes de Windows SDK, es posible que le interese actualizar el archivo de configuración *CppProperties.json* con los siguientes archivos de inclusión:

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

Si no ve la característica IntelliSense que espera, puede solucionar el problema si va a **Herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **Avanzadas** y establece **Habilitar el registro** en **true**. Para empezar, pruebe a establecer **Nivel de registro** en 5 y **Filtro de registro** en 8.

![Registros de diagnóstico](media/diagnostic-logging.png)

La salida se canaliza a la **Ventana de salida** y está visible cuando se elige **Mostrar salida de: Registro de Visual C++** . La salida contiene, entre otras cosas, la lista de rutas de acceso de inclusión reales que IntelliSense está intentando usar. Si las rutas de acceso no coinciden con las de *CppProperties.json*, pruebe a cerrar la carpeta y eliminar la subcarpeta *.vs* que contiene los datos de navegación almacenados en caché.

Para solucionar problemas de errores de IntelliSense causados por la ausencia de rutas de acceso de inclusión, abra la **Lista de errores** y filtre los resultados por "Solo IntelliSense" y el código de error E1696 "no se puede abrir el archivo de código fuente...".
