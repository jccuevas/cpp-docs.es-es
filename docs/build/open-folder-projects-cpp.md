---
title: Compatibilidad de la acción Abrir carpeta con sistemas de compilación de C++ en Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9264aa4bf77de406bdde9042ef9ec4251763f721
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320958"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Compatibilidad de la acción Abrir carpeta con sistemas de compilación de C++ en Visual Studio

::: moniker range="vs-2015"

La característica "Abrir carpeta" está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

En Visual Studio 2017 y versiones posteriores, la característica "Abrir carpeta" permite abrir carpetas de archivos de código fuente y comenzar a escribir código compatible con IntelliSense, la exploración, la refactorización, la depuración, etc. de inmediato. A medida que edita, crea, mueve o elimina archivos, Visual Studio hace seguimiento de manera automática de los cambios y actualiza de manera continua su indice de IntelliSense. No se carga ningún archivo .sln o .vcxproj; si es necesario, se pueden especificar tareas personalizadas así como parámetros de inicio y compilación a través de archivos .json simples. Esta característica permite integrar cualquier sistema de compilación de terceros en Visual Studio. Para obtener información general sobre Abrir carpeta, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake y Qt

CMake está integrado en el IDE de Visual Studio como un componente de la carga de trabajo de escritorio de C++. El flujo de trabajo de CMake no es idéntico al flujo descrito en este artículo. Si usa CMake, vea el artículo sobre [proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md). También puede usar CMake para compilar proyectos de Qt, o bien puede usar la [extensión de Qt de Visual Studio](https://download.qt.io/development_releases/vsaddin/) para Visual Studio 2015 o Visual Studio 2017.

## <a name="other-build-systems"></a>Otros sistemas de compilación

Para usar el IDE de Visual Studio con un conjunto de herramientas de compilador o un sistema de compilación que no se admite directamente desde el menú principal, seleccione **Archivo | Abrir | Carpeta** o presione **Ctrl+Mayús+Alt+O**. Navegue hasta la carpeta que contiene los archivos de código fuente. Para compilar el proyecto, configurar IntelliSense y establecer parámetros de depuración, debe agregar tres archivos JSON:

| | |
|-|-|
|CppProperties.json|Especifique la información de configuración personalizada para la exploración. Cree este archivo, si es necesario, en la carpeta raíz del proyecto. (No se usa en los proyectos de CMake).|
|tasks.vs.json|Especifique los comandos de compilación personalizados. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configurar tareas**.|
|launch.vs.json|Especifique argumentos de la línea de comandos para el depurador. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configuración de depuración e inicio**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Configuración de la navegación por código con CppProperties.json

Para que IntelliSense y el comportamiento de navegación, como **Ir a definición**, funcionen correctamente, Visual Studio debe saber qué compilador está usando, dónde están los encabezados del sistema y dónde se encuentran los archivos de inclusión adicionales si no están directamente en la carpeta que ha abierto (la carpeta del área de trabajo). Para especificar una configuración, puede elegir **Administrar configuraciones** en el menú desplegable de la barra de herramientas principal:

![Menú desplegable Administrar configuraciones](media/manage-configurations-dropdown.png)

Visual Studio ofrece las siguientes configuraciones predeterminadas:

![Configuraciones predeterminadas](media/default-configurations.png)

Por ejemplo, si elige **x64-Debug**, Visual Studio crea un archivo denominado *CppProperties.json* en la carpeta raíz el proyecto:

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

Esta configuración hereda las variables de entorno del [Símbolo del sistema para desarrolladores x64](building-on-the-command-line.md) de Visual Studio. Una de esas variables es `INCLUDE` y puede hacer referencia a ella aquí mediante la macro `${env.INCLUDE}`. La propiedad `includePath` indica a Visual Studio dónde buscar todos los orígenes que necesita para IntelliSense. En este caso, dice "Buscar en todos los directorios especificados por la variable de entorno INCLUDE y también en todos los directorios del árbol de la carpeta de trabajo actual". La propiedad `name` es el nombre que aparecerá en la lista desplegable y puede ser cualquier cosa que quiera. La propiedad `defines` proporciona sugerencias a IntelliSense cuando encuentra bloques de compilación condicionales. La propiedad `intelliSenseMode` proporciona algunas sugerencias adicionales basadas en el tipo de compilador. Hay varias opciones disponibles para MSVC, GCC y Clang.

> [!NOTE]
> Si parece que Visual Studio está omitiendo opciones de configuración en *CppProperties.json*, intente agregar una excepción al archivo *.gitignore* como esta: `!/CppProperties.json`.

## <a name="default-configuration-for-mingw-w64"></a>Configuración predeterminada para MinGW-w64

Si agrega la configuración MinGW-w64, el código JSON tiene este aspecto:

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

Fíjese en el bloque `environments`. Define propiedades que se comportan como variables de entorno y que están disponibles no solo en el archivo *CppProperties.json*, sino también en los otros archivos de configuración *task.vs.json* y *launch.vs.json*. La configuración de `Mingw64` hereda el entorno de `mingw_w64` y usa su propiedad `INCLUDE` para especificar el valor de `includePath`. Puede agregar otras rutas de acceso a esta propiedad de matriz según sea necesario.

La propiedad `intelliSenseMode` se establece en un valor adecuado para GCC. Para obtener más información sobre estas propiedades, vea la [referencia de esquema CppProperties](cppproperties-schema-reference.md).

Cuando todo funcione correctamente, verá IntelliSense desde los encabezados de GCC al pasar el mouse sobre un tipo:

![IntelliSense en GCC](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Habilitación de los diagnósticos de IntelliSense

Si no ve la característica IntelliSense que espera, puede solucionar el problema si va a **Herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **Avanzadas** y establece **Habilitar el registro** en **true**. Para empezar, pruebe a establecer **Nivel de registro** en 5 y **Filtro de registro** en 8.

![Registros de diagnóstico](media/diagnostic-logging.png)

La salida se canaliza a la **Ventana de salida** y está visible cuando se elige **Mostrar salida de: Registro de Visual C++* . La salida contiene, entre otras cosas, la lista de rutas de acceso de inclusión reales que IntelliSense está intentando usar. Si las rutas de acceso no coinciden con las de *CppProperties.json*, pruebe a cerrar la carpeta y eliminar la subcarpeta *.vs* que contiene los datos de navegación almacenados en caché.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definición de tareas de compilación con tasks.vs.json

Puede automatizar los scripts de compilación o cualquier otra operación externa en los archivos que tiene en el área de trabajo actual al ejecutarlos directamente en el IDE. Para configurar una tarea nueva, haga clic con el botón derecho en un archivo o una carpeta y seleccione **Configurar tareas**.

![Configurar tareas de Abrir carpeta](media/configure-tasks.png)

Esto crea (o abre) el archivo *tasks.vs.json* en la carpeta .vs que Visual Studio crea en la carpeta raíz del proyecto. En este archivo puede definir cualquier tarea arbitraria y luego invocarla desde el menú contextual del **Explorador de soluciones**. Para continuar el ejemplo de GCC, el fragmento de código siguiente muestra un archivo *tasks.vs.json* completo con una única tarea que invoca a *g++.exe* para compilar un proyecto. Imagine que el proyecto contiene un solo archivo llamado *hello.cpp*.

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

El archivo JSON se coloca en la subcarpeta *.vs*. Para ver esa carpeta, haga clic en el botón **Mostrar todos los archivos** en la parte superior del **Explorador de soluciones**. Puede ejecutar esta tarea haciendo clic con el botón derecho en el nodo raíz en el **Explorador de soluciones** y eligiendo **compilar hello**. Cuando se complete la tarea, debería ver un nuevo archivo *hello.exe* en el **Explorador de soluciones**.

Puede definir muchos tipos de tareas. En el ejemplo siguiente se muestra un archivo *tasks.vs.json* que define una sola tarea. `taskLabel` define el nombre que aparece en el menú contextual. `appliesTo` define los archivos en los que se puede ejecutar el comando. La propiedad `command` hace referencia a la variable de entorno COMSPEC, que identifica la ruta de acceso de la consola (*cmd.exe* en Windows). También se puede hacer referencia a variables de entorno que se declaran en CppProperties.json o CMakeSettings.json. La propiedad `args` especifica la línea de comandos que se va a invocar. La macro `${file}` recupera el archivo seleccionado en el **Explorador de soluciones**. En el ejemplo siguiente se muestra el nombre de archivo del archivo .cpp seleccionado actualmente.

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

Después de guardar *tasks.vs.json*, puede hacer clic con el botón derecho en cualquier archivo *.cpp* de la carpeta, seleccionar **Mostrar nombre de archivo** en el menú contextual y ver el nombre de archivo mostrado en la ventana de salida.

Para obtener más información, vea la [referencia del esquema Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurar parámetros de depuración con launch.vs.json

Para personalizar los argumentos de la línea de comandos y las instrucciones de depuración del programa, haga clic con el botón derecho en el archivo ejecutable en el **Explorador de soluciones** y seleccione **Configuración de depuración e inicio**. Se abrirá un archivo *launch.vs.json* existente o, si no existe ninguno, se creará un nuevo archivo con un conjunto de valores de inicio mínimos. En primer lugar, tiene la opción de elegir el tipo de sesión de depuración que quiere configurar. Para depurar un proyecto MinGW-w64, elegimos **Inicio de C/C++ para MinGW/Cygwin (gdb)** . Esto crea una configuración de inicio para usar *gdb.exe* con algunas suposiciones razonadas sobre los valores predeterminados. Uno de estos valores predeterminados es `MINGW_PREFIX`. Puede sustituir la ruta de acceso literal (como se muestra a continuación) o definir una propiedad `MINGW_PREFIX` en *CppProperties.json*:

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

Para iniciar la depuración, elija el ejecutable en la lista desplegable de depuración y, después, haga clic en la flecha verde:

![Inicio del depurador](media/launch-debugger-gdb.png)

Debería ver el cuadro de diálogo **Initializing Debugger** (Inicializando el depurador) y, luego, una ventana de consola externa que ejecuta el programa.

Para obtener más información, consulte el artículo [Referencia del esquema launch.vs.json](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Inicio de otros ejecutables

Puede definir la configuración de inicio de cualquier archivo ejecutable del equipo. En el ejemplo siguiente se inicia *7za* y se especifican argumentos adicionales al agregarlos a la matriz JSON `args`:

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
