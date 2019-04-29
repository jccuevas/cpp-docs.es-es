---
title: Compatibilidad de la acción Abrir carpeta con sistemas de compilación de C++ en Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 380a96bcb1a119b2b6d4104d60936217d1350fbb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274198"
---
# <a name="open-folder-projects-for-c"></a>Proyectos Abrir carpeta para C++

En Visual Studio 2017 y versiones posteriores, la característica "Abrir carpeta" permite abrir carpetas de archivos de código fuente y comenzar a escribir código compatible con IntelliSense, la exploración, la refactorización, la depuración, etc. de inmediato. No se carga ningún archivo .sln o .vcxproj; si es necesario, se pueden especificar tareas personalizadas así como parámetros de inicio y compilación a través de archivos .json simples. Para obtener información general sobre Abrir carpeta, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

CMake está integrado en el IDE de Visual Studio como Herramientas de CMake para Visual Studio, un componente de la carga de trabajo de escritorio de C++. Para más información, vea el artículo sobre [proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md). Para cualquier otro sistema de compilación, puede usar la característica Abrir carpeta. Esta función desacopla eficazmente el editor de código, el depurador y los analizadores del sistema de compilación y el conjunto de herramientas del compilador. Puede usar el editor de código de C++ con sus características enriquecidas de IntelliSense, los analizadores de código y el depurador de Visual Studio con prácticamente cualquier sistema de compilación, incluidos CMake, Ninja, QMake (para proyectos de Qt), gyp, SCons, Gradle, Buck, Make y muchos más. Funciona incluso con un solo archivo o una colección flexible de archivos sin ningún sistema de compilación.

Para usar Abrir carpeta, en el menú principal seleccione **Archivo | Abrir | Carpeta** o presione **Ctrl + Mayús + Alt + O**. En el Explorador de soluciones se muestran inmediatamente todos los archivos de la carpeta. Puede hacer clic en cualquier archivo para comenzar a editarlo. En segundo plano, Visual Studio comienza a indexar los archivos para habilitar las características de refactorización, navegación e IntelliSense. A medida que edita, crea, mueve o elimina archivos, Visual Studio hace seguimiento de manera automática de los cambios y actualiza de manera continua su indice de IntelliSense. 

## <a name="qmake-projects-that-target-the-qt-framework"></a>Proyectos de QMake que tienen como destino el marco de trabajo de Qt

Puede usar Herramientas de CMake para Visual Studio para establecer Qt como destino para compilar proyectos de Qt, o bien puede usar la [extensión Qt de Visual Studio](https://download.qt.io/development_releases/vsaddin/) para Visual Studio 2015 o Visual Studio 2017.

## <a name="gyp-cons-scons-buck-etc"></a>gyp, Cons, SCons, Buck, etc.

Puede usar cualquier sistema de compilación en Visual Studio y seguir disfrutando de las ventajas del IDE y el depurador de C++. Cuando se abre la carpeta raíz del proyecto, el editor de código de C++ usa la heurística para indexar los archivos de código fuente para IntelliSense y la exploración. Puede proporcionar indicaciones sobre la estructura del código si modifica el archivo CppProperties.json. De forma similar, puede configurar e invocar el programa de compilación si modifica el archivo launch.vs.json.

## <a name="configuring-open-folder-projects"></a>Configuración de proyectos Abrir carpeta

Puede personalizar un proyecto Abrir carpeta a través de tres archivos JSON:

| | |
|-|-|
|CppProperties.json|Especifique la información de configuración personalizada para la exploración. Cree este archivo, si es necesario, en la carpeta raíz del proyecto. (No se usa en los proyectos de CMake).|
|tasks.vs.json|Especifique comandos de compilación personalizada y modificadores del compilador. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configurar tareas**.|
|launch.vs.json|Especifique argumentos de la línea de comandos para el depurador. Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configuración de depuración e inicio**.|

### <a name="configure-intellisense-and-browsing-hints-with-cpppropertiesjson"></a>Configurar IntelliSense y explorar sugerencias con CppProperties.json

IntelliSense y el comportamiento de exploración dependen en parte de la configuración de compilación activa, que define las rutas de acceso #include, los modificadores del compilador y otros parámetros. De forma predeterminada, Visual Studio proporciona configuraciones Debug y Release. Los proyectos de CMake usan el archivo CMakeSettings.json y archivos CMakeLists.txt para este propósito. Para otros tipos de proyectos Abrir carpeta, podría tener que crear una configuración personalizada para que IntelliSense y las características de exploración comprendan el código en su totalidad. Para definir una configuración nueva, cree un archivo denominado CppProperties.json en la carpeta raíz. A continuación, se muestra un ejemplo:

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "windows-msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
Para obtener más información, vea la [referencia del esquema CppProperties](cppproperties-schema-reference.md).

### <a name="define-build-tasks-with-tasksvsjson"></a>Definición de tareas de compilación con tasks.vs.json

Puede automatizar los scripts de compilación o cualquier otra operación externa en los archivos que tiene en el área de trabajo actual al ejecutarlos directamente en el IDE. Para configurar una tarea nueva, haga clic con el botón derecho en un archivo o una carpeta y seleccione **Configurar tareas**.

![Configurar tareas de Abrir carpeta](media/open-folder-config-tasks.png)

Esto crea (o abre) el **tasks.vs.json** archivo en la carpeta .vs que Visual Studio crea en la carpeta raíz del proyecto. En este archivo puede definir cualquier tarea arbitraria y luego invocarla desde el menú contextual del **Explorador de soluciones**. En el ejemplo siguiente se muestra un archivo tasks.vs.json que define una sola tarea. `taskName` define el nombre que aparece en el menú contextual. `appliesTo` define los archivos en los que se puede ejecutar el comando. La propiedad `command` hace referencia a la variable de entorno COMSPEC, que identifica la ruta de acceso de la consola (cmd.exe en Windows). También se puede hacer referencia a variables de entorno que se declaran en CppProperties.json o CMakeSettings.json. La propiedad `args` especifica la línea de comandos que se va a invocar. La macro `${file}` recupera el archivo seleccionado en el **Explorador de soluciones**. En el ejemplo siguiente se muestra el nombre de archivo del archivo .cpp seleccionado actualmente.

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

Para obtener más información, vea la [referencia del esquema Tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Configurar parámetros de depuración con launch.vs.json

Para personalizar los argumentos de la línea de comandos del programa, haga clic con el botón derecho en el archivo ejecutable en el **Explorador de soluciones** y seleccione **Configuración de depuración e inicio**. Se abrirá una existente **launch.vs.json** archivo, o si no existe ninguno, creará un nuevo archivo que se rellena previamente con la información sobre el programa que ha seleccionado.

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
