---
title: Compatibilidad de la acción Abrir carpeta con sistemas de compilación de C++ en Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9264aa4bf77de406bdde9042ef9ec4251763f721
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320958"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Compatibilidad de la acción Abrir carpeta con sistemas de compilación de C++ en Visual Studio

::: moniker range="vs-2015"

La característica Abrir carpeta está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

En Visual Studio 2017 y versiones posteriores, la característica "Abrir carpeta" permite abrir carpetas de archivos de código fuente y comenzar a escribir código compatible con IntelliSense, la exploración, la refactorización, la depuración, etc. de inmediato. A medida que edita, crea, mueve o elimina archivos, Visual Studio hace seguimiento de manera automática de los cambios y actualiza de manera continua su indice de IntelliSense. No se carga ningún archivo .sln o .vcxproj; si es necesario, se pueden especificar tareas personalizadas así como parámetros de inicio y compilación a través de archivos .json simples. Esta característica le permite integrar cualquier sistema de compilación de terceros en Visual Studio. Para obtener información general sobre Abrir carpeta, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake y Qt

CMake está integrado en el IDE de Visual Studio como un componente de la carga de trabajo de escritorio C++. El flujo de trabajo de CMake no es idéntico al flujo de trabajo descrito en este artículo. Si usa CMake, vea [Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md). También puede usar CMake para compilar proyectos Qt o puede usar la [extensión Qt Visual Studio](https://download.qt.io/development_releases/vsaddin/) para Visual Studio 2015 o Visual Studio 2017.

## <a name="other-build-systems"></a>Otros sistemas de construcción

Para usar el IDE de Visual Studio con un sistema de compilación o un conjunto de herramientas del compilador que no se admite directamente desde el menú principal, seleccione **Archivo . Abiertos ? Carpeta** o pulse **Ctrl + Mayús + Alt + O**. Vaya a la carpeta que contiene los archivos de código fuente. Para compilar el proyecto, configure IntelliSense y establezca parámetros de depuración, agregue tres archivos JSON:

| | |
|-|-|
|CppProperties.json|Especifique la información de configuración personalizada para la exploración. Cree este archivo, si es necesario, en la carpeta raíz del proyecto. (No se usa en los proyectos de CMake).|
|tasks.vs.json|Especifique comandos de compilación personalizados. Se accede a través del elemento del menú contextual del **Explorador de soluciones****Configurar tareas**.|
|launch.vs.json|Especifique argumentos de la línea de comandos para el depurador. Se accede a través del elemento del menú contextual del **Explorador de soluciones****Configuración de depuración e inicio**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Configurar la navegación de código con CppProperties.json

Para que IntelliSense y el comportamiento de exploración, como **Ir a definición,** funcione correctamente, Visual Studio debe saber qué compilador está utilizando, dónde se encuentran los encabezados del sistema y dónde se encuentran los archivos de inclusión adicionales si no están directamente en la carpeta que ha abierto (la carpeta del área de trabajo). Para especificar una configuración, puede elegir **Administrar configuraciones** en la lista desplegable de la barra de herramientas principal:

![Administrar la lista desplegable de configuraciones](media/manage-configurations-dropdown.png)

Visual Studio ofrece las siguientes configuraciones predeterminadas:

![Configuraciones predeterminadas](media/default-configurations.png)

Si, por ejemplo, elige **x64-Debug**, Visual Studio crea un archivo denominado *CppProperties.json* en la carpeta del proyecto raíz:

```json
{
  "configurations": [
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
    }
  ]
}
```

Esta configuración hereda las variables de entorno del símbolo del sistema para desarrolladores de Visual Studio [x64](building-on-the-command-line.md). Una de esas `INCLUDE` variables es y puede hacer `${env.INCLUDE}` referencia a ella aquí mediante el uso de la macro. La `includePath` propiedad indica a Visual Studio dónde buscar todos los orígenes que necesita para IntelliSense. En este caso, dice "mira en todos los directorios especificados por la variable de entorno INCLUDE, y también todos los directorios en el árbol de carpetas de trabajo actual." La `name` propiedad es el nombre que aparecerá en la lista desplegable y puede ser cualquier cosa que desee. La `defines` propiedad proporciona sugerencias a IntelliSense cuando encuentra bloques de compilación condicionales. La `intelliSenseMode` propiedad proporciona algunas sugerencias adicionales basadas en el tipo del compilador. Hay varias opciones disponibles para MSVC, GCC y Clang.

> [!NOTE]
> Si Visual Studio parece ignorar la configuración de *CppProperties.json*, intente agregar una `!/CppProperties.json`excepción al archivo *.gitignore* de la siguiente manera: .

## <a name="default-configuration-for-mingw-w64"></a>Configuración predeterminada para MinGW-w64

Si usted agrega la configuración MinGW-W64, el JSON mira esto esto:

```json
{
  {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
}
```

Anote `environments` el bloque. Define las propiedades que se comportan como variables de entorno y están disponibles no solo en el archivo *CppProperties.json,* sino también en los otros archivos de configuración *task.vs.json* y *launch.vs.json*. La `Mingw64` configuración hereda el `mingw_w64` entorno `INCLUDE` y utiliza su `includePath`propiedad para especificar el valor de . Puede agregar otras rutas de acceso a esta propiedad de matriz según sea necesario.'

La `intelliSenseMode` propiedad se establece en un valor adecuado para GCC. Para obtener más información sobre todas estas propiedades, vea [CppProperties schema reference](cppproperties-schema-reference.md).

Cuando todo funciona correctamente, verá IntelliSense desde los encabezados GCC cuando pase el cursor sobre un tipo:

![IntelliSense del CCG](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Habilitar el diagnóstico de IntelliSense

Si no ve el IntelliSense que espera, puede **Tools** > solucionar los problemas en**Opciones** > de herramientas**Editor** > de texto**C/C++** > **Advanced** y establecer **Habilitar registro** en **true**. Para empezar, intente establecer **el nivel** de registro en 5 y los **filtros** de registro en 8.

![Registro de diagnóstico](media/diagnostic-logging.png)

La salida se canaliza a la ventana de **salida** y es visible cuando se elige **Mostrar salida desde: Visual C++ Log*. La salida contiene, entre otras cosas, la lista de rutas de acceso de inclusión reales que IntelliSense está intentando utilizar. Si las rutas de acceso no coinciden con las de *CppProperties.json,* intente cerrar la carpeta y eliminar la subcarpeta *.vs* que contiene datos de exploración almacenados en caché.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definición de tareas de compilación con tasks.vs.json

Puede automatizar los scripts de compilación o cualquier otra operación externa en los archivos que tiene en el área de trabajo actual al ejecutarlos directamente en el IDE. Para configurar una tarea nueva, haga clic con el botón derecho en un archivo o una carpeta y seleccione **Configurar tareas**.

![Configurar tareas de Abrir carpeta](media/configure-tasks.png)

Esto crea (o abre) el archivo *tasks.vs.json* en la carpeta .vs que Visual Studio crea en la carpeta raíz del proyecto. En este archivo puede definir cualquier tarea arbitraria y luego invocarla desde el menú contextual del **Explorador de soluciones**. Para continuar en el ejemplo de GCC, el siguiente fragmento de código muestra un archivo *tasks.vs.json* completo con como tarea única que invoca *g+++.exe* para compilar un proyecto. Supongamos que el proyecto contiene un único archivo denominado *hello.cpp*.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

El archivo JSON se coloca en la subcarpeta *.vs.* Para ver esa carpeta, haga clic en el botón **Mostrar todos los archivos** en la parte superior del Explorador de **soluciones**. Puede ejecutar esta tarea haciendo clic con el botón derecho en el nodo raíz en el **Explorador** de soluciones y eligiendo **build hello**. Cuando se complete la tarea, debería ver un nuevo archivo, *hello.exe* en el **Explorador**de soluciones .

Puede definir muchos tipos de tareas. En el ejemplo siguiente se muestra un *archivo tasks.vs.json* que define una sola tarea. `taskLabel` define el nombre que aparece en el menú contextual. `appliesTo` define los archivos en los que se puede ejecutar el comando. La `command` propiedad hace referencia a la variable de entorno COMSPEC, que identifica la ruta de acceso de la consola (*cmd.exe* en Windows). También se puede hacer referencia a variables de entorno que se declaran en CppProperties.json o CMakeSettings.json. La propiedad `args` especifica la línea de comandos que se va a invocar. La macro `${file}` recupera el archivo seleccionado en el **Explorador de soluciones**. En el ejemplo siguiente se muestra el nombre de archivo del archivo .cpp seleccionado actualmente.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

Después de guardar *tasks.vs.json*, puede hacer clic con el botón derecho en cualquier archivo *.cpp de* la carpeta, elegir Nombre de **archivo de eco** en el menú contextual y ver el nombre de archivo que se muestra en la ventana Salida.

Para obtener más información, vea la [referencia del esquema Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurar parámetros de depuración con launch.vs.json

Para personalizar los argumentos de línea de comandos y las instrucciones de depuración del programa, haga clic con el botón derecho en el ejecutable en el **Explorador** de soluciones y seleccione **Depurar e iniciar configuración**. Esto abrirá un archivo *launch.vs.json* existente, o si no existe ninguno, creará un nuevo archivo con un conjunto de configuraciones de lanzamiento mínimas. En primer lugar, se le da la opción de qué tipo de sesión de depuración desea configurar. Para depurar un proyecto MinGw-w64, elegimos **C/C++ Launch para MinGW/Cygwin (gdb)**. Esto crea una configuración de inicio para usar *gdb.exe* con algunas conjeturas educadas sobre los valores predeterminados. Uno de esos `MINGW_PREFIX`valores predeterminados es . Puede sustituir la ruta literal (como se muestra `MINGW_PREFIX` a continuación) o puede definir una propiedad en *CppProperties.json:*

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

Para iniciar la depuración, elija el ejecutable en el menú desplegable de depuración y, a continuación, haga clic en la flecha verde:

![Iniciar depurador](media/launch-debugger-gdb.png)

Debería ver el cuadro de diálogo **Inicializar depurador** y, a continuación, una ventana de consola externa que ejecuta el programa.

Para obtener más información, vea referencia de [esquema launch.vs.json](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Lanzamiento de otros ejecutables

Puede definir la configuración de inicio de cualquier ejecutable en el equipo. En el ejemplo siguiente se inicia *7za* y se `args` especifican argumentos adicionales, agregándolos a la matriz JSON:

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

::: moniker-end
