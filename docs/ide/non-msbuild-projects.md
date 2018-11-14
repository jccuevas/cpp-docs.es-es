---
title: Proyectos Abrir carpeta en Visual C++
ms.date: 06/01/2018
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 6354cc656d501d1611219378f72831cc2fa94389
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524006"
---
# <a name="open-folder-projects-in-visual-c"></a>Proyectos Abrir carpeta en Visual C++

En Visual Studio 2017 y versiones posteriores, la característica "Abrir carpeta" permite abrir carpetas de archivos de código fuente y comenzar a escribir código compatible con IntelliSense, la exploración, la refactorización, la depuración, etc. de inmediato. No se carga ningún archivo .sln o .vcxproj; si es necesario, se pueden especificar tareas personalizadas así como parámetros de inicio y compilación a través de archivos .json simples.
Con la tecnología de Carpeta abierta, ahora Visual C++ no solo puede admitir colecciones flexibles de archivos, sino también prácticamente cualquier sistema de compilación, incluidos CMake, Ninja, QMake (para proyectos de Qt), gyp, SCons, Gradle, Buck, make y muchos más.

Para usar Abrir carpeta, en el menú principal seleccione *Archivo | Abrir | Carpeta* o presione *Ctrl + Mayús + Alt + O*. En el Explorador de soluciones se muestran inmediatamente todos los archivos de la carpeta. Puede hacer clic en cualquier archivo para comenzar a editarlo. En segundo plano, Visual Studio comienza a indexar los archivos para habilitar las características de refactorización, navegación e IntelliSense. A medida que edita, crea, mueve o elimina archivos, Visual Studio hace seguimiento de manera automática de los cambios y actualiza de manera continua su indice de IntelliSense.

## <a name="cmake-projects"></a>Proyectos de CMake

CMake está integrado en el IDE de Visual Studio como Herramientas de Visual C++ para CMake, un componente de la carga de trabajo Escritorio de C++. Para obtener más información, consulte [Herramientas de CMake para Visual C++](cmake-tools-for-visual-cpp.md).

## <a name="qmake-projects-that-target-the-qt-framework"></a>Proyectos de QMake que tienen como destino el marco de trabajo de Qt

Puede usar las herramientas de Visual C++ para CMake para establecer Qt como destino para compilar proyectos de Qt, o bien puede usar la [extensión Qt de Visual Studio](https://download.qt.io/development_releases/vsaddin/) para Visual Studio 2015 o Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp, Cons, SCons, Buck, etc.

Puede usar cualquier sistema de compilación en Visual C++ y seguir disfrutando de las ventajas del IDE y el depurador de Visual C++. Cuando se abre la carpeta raíz del proyecto, Visual C++ usa la heurística para indexar los archivos de código fuente para IntelliSense y la exploración. Puede proporcionar indicaciones sobre la estructura del código si modifica el archivo CppProperties.json. De forma similar, puede configurar el programa de compilación si modifica el archivo launch.vs.json.

## <a name="configuring-open-folder-projects"></a>Configuración de proyectos Abrir carpeta

Puede personalizar un proyecto Abrir carpeta a través de tres archivos JSON:

| | |
|-|-|
|CppProperties.json|Especifique la información de configuración personalizada para la exploración. Cree este archivo, si es necesario, en la carpeta raíz del proyecto.|
|launch.vs.json|Especifique argumentos de la línea de comandos. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configuración de depuración e inicio**.|
|tasks.vs.json|Especifique comandos de compilación personalizada y modificadores del compilador. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configurar tareas**.|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>Configurar IntelliSense con CppProperties.json

IntelliSense y el comportamiento de exploración dependen en parte de la configuración de compilación activa, que define las rutas de acceso #include, los modificadores del compilador y otros parámetros. De forma predeterminada, Visual Studio proporciona configuraciones Debug y Release. Para algunos proyectos, debe crear una configuración personalizada para que IntelliSense y las características de exploración comprendan el código en su totalidad. Para definir una configuración nueva, cree un archivo denominado CppProperties.json en la carpeta raíz. A continuación se muestra un ejemplo:

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```

Una configuración puede tener cualquiera de las propiedades siguientes:

|||
|-|-|
|`name`|el nombre de configuración que aparece en la lista desplegable de configuración de C++.|
|`includePath`|la lista de carpetas que se deben especificar en la ruta de acceso de inclusión (se asigna a /I para la mayoría de los compiladores).|
|`defines`|la lista de macros que se deben definir (se asigna a /D para la mayoría de los compiladores).|
|`compilerSwitches`|uno o varios modificadores adicionales que pueden influir en el comportamiento de IntelliSense.|
|`forcedInclude`|encabezado que se va a incluir de forma automática en todas las unidades de compilación (se asigna a /FI para MSVC o -include para clang).|
|`undefines`|la lista de macros de las que se van a anular las definiciones (se asigna a /U para MSVC).|
|`intelliSenseMode`|el motor de IntelliSense que se va usar. Puede especificar variantes específicas de la arquitectura para MSVC, gcc o Clang:<br/><br/>- msvc-x86 (valor predeterminado)<br/>- msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>- windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>- Linux-arm<br/>- gccarm|

#### <a name="environment-variables"></a>Variables de entorno

CppProperties.json admite la expansión de variables de entorno del sistema para incluir rutas de acceso de inclusión y otros valores de propiedad. La sintaxis es `${env.FOODIR}` para expandir una variable de entorno `%FOODIR%`. También se admiten las siguientes variables definidas por el sistema:

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

Se pueden definir variables de entorno personalizadas en CppProperties.json de forma global o por cada configuración. En el ejemplo siguiente se muestra cómo declarar y usar las variables de entorno predeterminadas y personalizadas. La propiedad **environments** global declara una variable denominada **INCLUDE** que se puede usar en cualquier configuración:

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
      "intelliSenseMode": "msvc-x86"
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
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```

También se puede definir una propiedad **environments** dentro de una configuración, para que solo se aplique a esa configuración y reemplace las variables globales del mismo nombre. En el ejemplo siguiente, la configuración x64 define una variable **INCLUDE** local que invalida el valor global:

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
      "intelliSenseMode": "msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\\src\\includes64"
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
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```

Todas las variables de entorno personalizadas y predeterminadas también están disponibles en tasks.vs.json y launch.vs.json.

#### <a name="macros"></a>Macros

Dentro de CppProperties.json tiene acceso a las macros integradas siguientes:

|||
|-|-|
|`${workspaceRoot}`| la ruta de acceso completa a la carpeta del área de trabajo.|
|`${projectRoot}`| la ruta de acceso completa a la carpeta donde se coloca CppProperties.json.|
|`${vsInstallDir}`| la ruta de acceso completa a la carpeta donde está instalada la instancia en ejecución de VS 2017.|

Por ejemplo, si el proyecto tiene una carpeta de inclusión y también incluye windows.h y otros encabezados comunes de Windows SDK, es posible que le interese actualizar el archivo de configuración CppProperties.json con estos archivos de inclusión:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\ucrt",
        "${env.NETFXSDKDir}\\include\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\shared",
        "${env.VCToolsInstallDir}include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%` y `%VCToolsInstallDir%` no se establecen como variables de entorno globales, por lo que debe asegurarse de iniciar devenv.exe desde un "Símbolo del sistema para desarrolladores para VS 2017" que defina estas variables.

Para solucionar problemas de errores de IntelliSense causados por la ausencia de rutas de acceso de inclusión, abra la **Lista de errores** y filtre los resultados por "Solo IntelliSense" y el código de error E1696 "no se puede abrir el archivo de código fuente...".

Puede crear cualquier número de configuraciones en CppProperties.json. Todas aparecerán en el menú desplegable de configuración:

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

### <a name="define-tasks-with-tasksvsjson"></a>Definición de tareas con tasks.vs.json

Puede automatizar los scripts de compilación o cualquier otra operación externa en los archivos que tiene en el área de trabajo actual al ejecutarlos directamente en el IDE. Para configurar una tarea nueva, haga clic con el botón derecho en un archivo o una carpeta y seleccione **Configurar tareas**.

![Configurar tareas de Abrir carpeta](media/open-folder-config-tasks.png)

Esto crea (o abre) el archivo `tasks.vs.json` en la carpeta .vs que Visual Studio crea en la carpeta raíz del proyecto. En este archivo puede definir cualquier tarea arbitraria y luego invocarla desde el menú contextual del **Explorador de soluciones**. En el ejemplo siguiente se muestra un archivo tasks.vs.json que define una sola tarea. `taskName` define el nombre que aparece en el menú contextual. `appliesTo` define los archivos en los que se puede ejecutar el comando. La propiedad `command` hace referencia a la variable de entorno COMSPEC, que identifica la ruta de acceso de la consola (cmd.exe en Windows). También se puede hacer referencia a variables de entorno que se declaran en CppProperties.json o CMakeSettings.json. La propiedad `args` especifica la línea de comandos que se va a invocar. La macro `${file}` recupera el archivo seleccionado en el **Explorador de soluciones**. En el ejemplo siguiente se muestra el nombre de archivo del archivo .cpp seleccionado actualmente.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

Después de guardar tasks.vs.json, puede hacer clic con el botón derecho en cualquier archivo .cpp de la carpeta, seleccionar **Mostrar nombre de archivo** en el menú contextual y ver el nombre de archivo mostrado en la ventana Salida.

#### <a name="appliesto"></a>appliesTo

Puede crear tareas para cualquier archivo o carpeta si especifica su nombre en el campo `appliesTo`, por ejemplo `"appliesTo" : "hello.cpp"`. Las máscaras de archivo siguientes se pueden usar como valores:

|||
|-|-|
|`"*"`| tarea disponible para todos los archivos y carpetas del área de trabajo|
|`"*/"`| tarea disponible para todas las carpetas del área de trabajo|
|`"*.cpp"`| tarea disponible para todos los archivos con la extensión .cpp del área de trabajo|
|`"/*.cpp"`| tarea disponible para todos los archivos con extensión .cpp de la raíz del área de trabajo|
|`"src/*/"`| tarea disponible para todas las subcarpetas de la carpeta "src"|
|`"makefile"`| tarea disponible para todos los archivos Make del área de trabajo|
|`"/makefile"`| tarea disponible solo para el archivo Make que se encuentra en la raíz del área de trabajo|

#### <a name="output"></a>salida

Use la propiedad `output` para especificar el archivo ejecutable que se iniciará cuando se presione **F5**. Por ejemplo:

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe"
```

#### <a name="macros-for-tasksvsjson"></a>Macros de tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Especifica cualquier variable de entorno (por ejemplo, ${env.PATH}, ${env.COMSPEC}, etc.) que esté establecida para el símbolo del sistema para desarrolladores. Para más información, consulte [Símbolo del sistema para desarrolladores de Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| La ruta de acceso completa a la carpeta del área de trabajo (por ejemplo, "C:\sources\hello").|
|`${file}`| La ruta de acceso completa del archivo o la carpeta seleccionados para la ejecución de esta tarea (por ejemplo, "C:\sources\hello\src\hello.js").|
|`${relativeFile}`| La ruta de acceso relativa al archivo o la carpeta (por ejemplo, "src\hello.js").|
|`${fileBasename}`| El nombre del archivo sin la ruta de acceso ni la extensión (por ejemplo, "hello").|
|`${fileDirname}`| La ruta de acceso completa al archivo, sin el nombre de archivo (por ejemplo, "C:\sources\hello\src").|
|`${fileExtname}`| La extensión del archivo seleccionado (por ejemplo, ".cpp").|

#### <a name="custom-macros"></a>Macros personalizadas

Para definir una macro personalizada en tasks.vs.json, agregue un par nombre:valor antes de los bloques de tarea. En el ejemplo siguiente se define una macro denominada `outDir` que se consume en la propiedad `args`:

```json
{
"version": "0.2.1",
  "outDir": "${workspaceRoot}\\bin",
  "tasks": [
    {
      "taskName": "List outputs",
      "*",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": [
        "dir ${outDir}"
      ]
    }
  ]
```

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurar parámetros de depuración con launch.vs.json

Para personalizar los argumentos de la línea de comandos del programa, haga clic con el botón derecho en el archivo ejecutable en el **Explorador de soluciones** y seleccione **Configuración de depuración e inicio**. Se abrirá un archivo `launch.vs.json` existente, o si no existe ninguno, creará un archivo rellenado previamente con la información sobre el programa que se ha seleccionado.

Para especificar argumentos adicionales, simplemente agréguelos en la matriz de JSON `args` como se muestra en el ejemplo siguiente:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

Al guardar este archivo, el nombre de la configuración nueva aparece en la lista desplegable Destino de depuración y puede seleccionarlo para iniciar el depurador. Puede crear tantas configuraciones de depuración como quiera, para cualquier número de archivos ejecutables. Si ahora presiona **F5**, se iniciará el depurador y se alcanzará cualquier punto de interrupción que se haya establecido. Todas las ventanas del depurador conocidas y su funcionalidad estarán ahora disponibles.

## <a name="see-also"></a>Vea también

[IDE y herramientas para desarrollo de Visual C++](ide-and-tools-for-visual-cpp-development.md)
