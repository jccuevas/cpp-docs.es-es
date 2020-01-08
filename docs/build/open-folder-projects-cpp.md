---
title: Compatibilidad de la acción Abrir carpeta con sistemas de compilación de C++ en Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 8342060e7286c1089312874199bf341ec36bed62
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556710"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Compatibilidad de la acción Abrir carpeta con sistemas de compilación de C++ en Visual Studio

::: moniker range="vs-2015"

La característica abrir carpeta está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

En Visual Studio 2017 y versiones posteriores, la característica "Abrir carpeta" permite abrir carpetas de archivos de código fuente y comenzar a escribir código compatible con IntelliSense, la exploración, la refactorización, la depuración, etc. de inmediato. A medida que edita, crea, mueve o elimina archivos, Visual Studio hace seguimiento de manera automática de los cambios y actualiza de manera continua su indice de IntelliSense. No se carga ningún archivo .sln o .vcxproj; si es necesario, se pueden especificar tareas personalizadas así como parámetros de inicio y compilación a través de archivos .json simples. Esta característica permite integrar cualquier sistema de compilación de terceros en Visual Studio. Para obtener información general sobre Abrir carpeta, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake y QT

CMake se integra en el IDE de Visual Studio como un componente de C++ la carga de trabajo del escritorio. El flujo de trabajo de CMake no es idéntico al flujo de trabajo que se describe en este artículo. Si usa CMake, consulte [proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md). También puede usar CMake para compilar proyectos de QT, o bien puede usar la [extensión de Visual Studio QT](https://download.qt.io/development_releases/vsaddin/) para visual Studio 2015 o visual Studio 2017.

## <a name="other-build-systems"></a>Otros sistemas de compilación

Para usar el IDE de Visual Studio con un conjunto de herramientas del compilador o del compilador que no se admite directamente desde el menú principal, seleccione **archivo | Abrir | O presione** **Ctrl + Mayús + Alt + O**. Navegue hasta la carpeta que contiene los archivos de código fuente. Para compilar el proyecto, configurar IntelliSense y establecer parámetros de depuración, se agregan tres archivos JSON:

| | |
|-|-|
|CppProperties.json|Especifique la información de configuración personalizada para la exploración. Cree este archivo, si es necesario, en la carpeta raíz del proyecto. (No se usa en los proyectos de CMake).|
|tasks.vs.json|Especifique los comandos de compilación personalizados. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configurar tareas**.|
|launch.vs.json|Especifique argumentos de la línea de comandos para el depurador. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configuración de depuración e inicio**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Configuración de la navegación por el código con CppProperties. JSON

Para que IntelliSense y el comportamiento de exploración, como **ir a definición** funcionen correctamente, Visual Studio debe saber qué compilador está usando, dónde están los encabezados del sistema y dónde se encuentran los archivos de inclusión adicionales si no están directamente en la carpeta que ha abierto (la carpeta del área de trabajo). Para especificar una configuración, puede elegir **administrar configuraciones** en la lista desplegable de la barra de herramientas principal:

![Lista desplegable administrar configuraciones](media/manage-configurations-dropdown.png)

Visual Studio ofrece las siguientes configuraciones predeterminadas:

![Configuraciones predeterminadas](media/default-configurations.png)

Por ejemplo, si elige **x64-Debug**, Visual Studio crea un archivo denominado *CppProperties. JSON* en la carpeta de proyecto raíz:

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

Esta configuración hereda las variables de entorno de Visual Studio [x64 símbolo del sistema para desarrolladores](building-on-the-command-line.md). Una de esas variables es `INCLUDE` y puede hacer referencia a ella aquí mediante la macro `${env.INCLUDE}`. La propiedad `includePath` indica a Visual Studio dónde buscar todos los orígenes que necesita para IntelliSense. En este caso, dice "Buscar en todos los directorios especificados por la variable de entorno INCLUDE y también todos los directorios del árbol de carpetas de trabajo actual". La propiedad `name` es el nombre que aparecerá en la lista desplegable y puede ser cualquier cosa que desee. La propiedad `defines` proporciona sugerencias a IntelliSense cuando encuentra bloques de compilación condicionales. La propiedad `intelliSenseMode` proporciona algunas sugerencias adicionales basadas en el tipo de compilador. Hay varias opciones disponibles para MSVC, GCC y Clang.

> [!NOTE]
> Si parece que Visual Studio está omitiendo la configuración en *CppProperties. JSON*, intente agregar una excepción al archivo *. gitignore* como este: `!/CppProperties.json`.

## <a name="default-configuration-for-mingw-w64"></a>Configuración predeterminada de MinGW-W64

Si agrega la configuración MinGW-W64, el código JSON tiene este aspecto:

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

Tenga en cuenta el bloque `environments`. Define propiedades que se comportan como variables de entorno y que están disponibles no solo en el archivo *CppProperties. JSON* , sino también en los otros archivos de configuración *Task. vs. JSON* y *Launch. vs. JSON*. La configuración de `Mingw64` hereda el entorno de `mingw_w64` y utiliza su propiedad `INCLUDE` para especificar el valor de `includePath`. Puede agregar otras rutas de acceso a esta propiedad de matriz según sea necesario.

La propiedad `intelliSenseMode` está establecida en un valor adecuado para GCC. Para obtener más información sobre todas estas propiedades, vea [referencia de esquemas de CppProperties](cppproperties-schema-reference.md).

Cuando todo funcione correctamente, verá IntelliSense desde los encabezados GCC al mantener el mouse sobre un tipo:

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Habilitar diagnósticos de IntelliSense

Si no ve el IntelliSense que espera, puede solucionar el problema en **herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **avanzadas** y establecer **Habilitar registro** en **true**. Para empezar, pruebe a establecer el **nivel de registro** en 5 y registre los **filtros** en 8.

![Registros de diagnóstico](media/diagnostic-logging.png)

La salida se canaliza al **ventana de salida** y está visible cuando se elige **Mostrar salida de: Registro C++ visual*. La salida contiene, entre otras cosas, la lista de rutas de acceso de inclusión reales que IntelliSense está intentando usar. Si las rutas de acceso no coinciden con las de *CppProperties. JSON*, intente cerrar la carpeta y eliminar la subcarpeta *. vs* que contiene los datos de exploración almacenados en caché.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definición de tareas de compilación con tasks.vs.json

Puede automatizar los scripts de compilación o cualquier otra operación externa en los archivos que tiene en el área de trabajo actual al ejecutarlos directamente en el IDE. Para configurar una tarea nueva, haga clic con el botón derecho en un archivo o una carpeta y seleccione **Configurar tareas**.

![Configurar tareas de Abrir carpeta](media/configure-tasks.png)

Esto crea (o abre) el archivo *Tasks. vs. JSON* en la carpeta. vs que Visual Studio crea en la carpeta raíz del proyecto. En este archivo puede definir cualquier tarea arbitraria y luego invocarla desde el menú contextual del **Explorador de soluciones**. Para continuar el ejemplo de GCC, el fragmento de código siguiente muestra un archivo *Tasks. vs. JSON* completo con como una única tarea que invoca *g + +. exe* para compilar un proyecto. Suponga que el proyecto contiene un solo archivo denominado *Hello. cpp*.

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

El archivo JSON se coloca en la subcarpeta *. vs* . Para ver esa carpeta, haga clic en el botón **Mostrar todos los archivos** situado en la parte superior de **Explorador de soluciones**. Puede ejecutar esta tarea haciendo clic con el botón secundario en el nodo raíz en **Explorador de soluciones** y eligiendo **compilar Hola**. Cuando se complete la tarea, debería ver un nuevo archivo *Hello. exe* en **Explorador de soluciones**.

Puede definir muchos tipos de tareas. En el ejemplo siguiente se muestra un *archivo Tasks. vs. JSON* que define una sola tarea. `taskLabel` define el nombre que aparece en el menú contextual. `appliesTo` define los archivos en los que se puede ejecutar el comando. La propiedad `command` hace referencia a la variable de entorno comspec, que identifica la ruta de acceso de la consola (*cmd. exe* en Windows). También se puede hacer referencia a variables de entorno que se declaran en CppProperties.json o CMakeSettings.json. La propiedad `args` especifica la línea de comandos que se va a invocar. La macro `${file}` recupera el archivo seleccionado en el **Explorador de soluciones**. En el ejemplo siguiente se muestra el nombre de archivo del archivo .cpp seleccionado actualmente.

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

Después de guardar *Tasks. vs. JSON*, puede hacer clic con el botón secundario en cualquier archivo *. cpp* de la carpeta, elegir **echo FILENAME** en el menú contextual y ver el nombre de archivo que se muestra en la ventana de salida.

Para obtener más información, vea la [referencia del esquema Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurar parámetros de depuración con launch.vs.json

Para personalizar los argumentos de la línea de comandos del programa y las instrucciones de depuración, haga clic con el botón derecho en el ejecutable en **Explorador de soluciones** y seleccione **configuración de depuración e inicio**. Se abrirá un archivo *Launch. vs. JSON* existente o, si no existe ninguno, se creará un nuevo archivo con un conjunto de valores de inicio mínimos. En primer lugar, tiene la opción de elegir el tipo de sesión de depuración que desea configurar. Para depurar un proyecto MinGw-W64, elegimos **CC++ /Launch para MinGw/Cygwin (GDB)** . Esto crea una configuración de inicio para usar *gdb. exe* con algunas conjeturas proporcionadas sobre los valores predeterminados. Uno de estos valores predeterminados es `MINGW_PREFIX`. Puede sustituir la ruta de acceso literal (como se muestra a continuación) o puede definir una propiedad `MINGW_PREFIX` en *CppProperties. JSON*:

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

Para iniciar la depuración, elija el ejecutable en la lista desplegable depurar y, a continuación, haga clic en la flecha verde:

![Iniciar el depurador](media/launch-debugger-gdb.png)

Debería ver el cuadro de diálogo **inicializando el depurador** y, a continuación, una ventana de consola externa que ejecuta el programa.

Para obtener más información, vea [referencia de esquemas Launch. vs. JSON](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Iniciar otros ejecutables

Puede definir la configuración de inicio de cualquier archivo ejecutable en el equipo. En el ejemplo siguiente se inicia *7za* y se especifican argumentos adicionales, agregándolos al `args` matriz JSON:

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
