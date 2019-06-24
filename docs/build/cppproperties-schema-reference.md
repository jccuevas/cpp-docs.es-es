---
title: Referencia del esquema de CppProperties.json
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual Studio
ms.openlocfilehash: 8432b72deaef99ee20147505030cbc8a9a270869
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344400"
---
# <a name="cpppropertiesjson-schema-reference"></a>Referencia del esquema de CppProperties.json

Los proyectos Abrir carpeta que no usan CMake pueden almacenar valores de configuración del proyecto en un archivo `CppProperties.json`. (Los proyectos de CMake usan un archivo [CMakeSettings.json](customize-cmake-settings.md)). El IDE de Visual Studio usa `CppProperties.json` para IntelliSense y la navegación por el código. Una configuración consta de pares nombre-valor y define rutas de acceso #include, modificadores del compilador y otros parámetros. 


## <a name="default-configurations"></a>Configuraciones predeterminadas

Visual Studio proporciona configuraciones predefinidas para depuración y versión x86 y x64. De forma predeterminada, el proyecto tiene una configuración de depuración x86 en `CppProperties.json`. Para agregar una nueva configuración, haga doble clic en el `CppProperties.json` archivo **el Explorador de soluciones** y elija **Agregar configuración**:

![Abra la carpeta - agregar nueva configuración](media/open-folder-add-config.png "Abrir carpeta agregar nueva configuración")

Aquí se muestran las configuraciones predeterminadas:

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
Para las propiedades que tienen un conjunto de valores permitidos, el editor de código mostrará las opciones disponibles cuando empiece a escribir:

![Abrir la carpeta IntelliSense](media/open-folder-intellisense-mode.png "Open Folder IntelliSense")



## <a name="configuration-properties"></a>Propiedades de configuración

Una configuración puede tener cualquiera de las propiedades siguientes:

|||
|-|-|
|`name`|Nombre de configuración que aparece en la lista desplegable de configuración de C++.|
|`includePath`|Lista de carpetas que se deben especificar en la ruta de acceso de inclusión (se asigna a /I para la mayoría de los compiladores).|
|`defines`|Lista de macros que se deben definir (se asigna a /D para la mayoría de los compiladores).|
|`compilerSwitches`|Uno o varios modificadores adicionales que pueden influir en el comportamiento de IntelliSense.|
|`forcedInclude`|Encabezado que se va a incluir de forma automática en todas las unidades de compilación (se asigna a /FI para MSVC o -include para clang).|
|`undefines`|Lista de macros de las que se van a anular las definiciones (se asigna a /U para MSVC).|
|`intelliSenseMode`|Motor de IntelliSense que se va usar. Puede especificar las variantes específicas de la arquitectura de MSVC gcc y Clang:<br/><br/>- windows-msvc-x86 (valor predeterminado)<br/>- windows-msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>- windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>- Linux-arm<br/>- gccarm|

Nota: Los valores `msvc-x86` y `msvc-x64` solo se admiten por motivos de herencia. Use el `windows-msvc-*` variantes en su lugar.

## <a name="custom-configurations"></a>Configuraciones personalizadas


Puede personalizar cualquiera de las configuraciones predeterminadas de `CppProperties.json`, o bien crear configuraciones. Todas aparecerán en el menú desplegable de configuración:

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```

## <a name="system-environment-variables"></a>Variables de entorno del sistema 

 `CppProperties.json` admite la expansión de variables de entorno del sistema para incluir rutas de acceso de inclusión y otros valores de propiedad. La sintaxis es `${env.FOODIR}` para expandir una variable de entorno `%FOODIR%`. También se admiten las siguientes variables definidas por el sistema:

|Nombre de la variable|Descripción|
|-----------|-----------------|
|vsdev|El entorno de Visual Studio predeterminado.|
|msvc_x86|Compilar para x86 con herramientas de x86.|
|msvc_arm|Compilar para ARM con herramientas de x86.|
|msvc_arm64|Compilar para ARM64 con herramientas de x86.|
|msvc_x86_x64|Compilar para AMD64 con herramientas de x86.|
|msvc_x64_x64|Compilar para AMD64 con herramientas de 64 bits.|
|msvc_arm_x64|Compilar para ARM con herramientas de 64 bits.|
|msvc_arm64_x64|Compilar para ARM64 con herramientas de 64 bits.|

Cuando se instala la carga de trabajo de Linux, los entornos siguientes están disponibles para seleccionar como destino Linux y WSL de forma remota:

|Nombre de la variable|Descripción|
|-----------|-----------------|
|linux_x86|Se destina a Linux x86 de forma remota.|
|linux_x64|Se destina a Linux x64 de forma remota.|
|linux_arm|Se destina a Linux ARM de forma remota.|

## <a name="custom-environment-variables"></a>Variables de entorno personalizadas

Se pueden definir variables de entorno personalizadas en `CppProperties.json` de forma global o por cada configuración. En el ejemplo siguiente se muestra cómo declarar y usar las variables de entorno predeterminadas y personalizadas. La propiedad **environments** global declara una variable denominada **INCLUDE** que se puede usar en cualquier configuración:

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        // Inherit the MSVC 32-bit environment and toolchain.
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        // Inherit the MSVC 64-bit environment and toolchain.
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>Variables de entorno por configuración

También puede definir un **entornos** propiedad dentro de una configuración. Se aplica solo a esa configuración y reemplaza las variables globales del mismo nombre. En el ejemplo siguiente, la configuración x64 define una variable **INCLUDE** local que invalida el valor global:

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined in the global environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\src\includes64"
        }
      ],

      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined in the local environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

Todas las variables de entorno personalizadas y predeterminadas también están disponibles en `tasks.vs.json` y `launch.vs.json`.

#### <a name="build-in-macros"></a>Macros integradas

Dentro de `CppProperties.json` tiene acceso a las macros integradas siguientes:

|||
|-|-|
|`${workspaceRoot}`| la ruta de acceso completa a la carpeta del área de trabajo.|
|`${projectRoot}`| la ruta de acceso completa a la carpeta donde se coloca `CppProperties.json`.|
|`${vsInstallDir}`| la ruta de acceso completa a la carpeta donde está instalada la instancia en ejecución de Visual Studio.|

Por ejemplo, si el proyecto tiene una carpeta de inclusión y también incluye windows.h y otros encabezados comunes desde el SDK de Windows, es posible que desee actualizar su `CppProperties.json` incluye el archivo de configuración con lo siguiente:

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

Para solucionar problemas de errores de IntelliSense causados por la ausencia de rutas de acceso de inclusión, abra la **Lista de errores** y filtre los resultados por "Solo IntelliSense" y el código de error E1696 "no se puede abrir el archivo de código fuente...".
