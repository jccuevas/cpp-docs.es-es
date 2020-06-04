---
title: Referencia de esquema tasks.vs.json (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: cc6b2983d3cc3d40449357a554df5feee38c21d9
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556661"
---
# <a name="tasksvsjson-schema-reference-c"></a>Referencia de esquema tasks.vs.json (C++)

Para indicar a Visual Studio cómo compilar el código fuente en un proyecto de carpeta abierta, agregue un archivo *tasks.vs.json*. Aquí se puede definir cualquier tarea arbitraria y luego invocarla desde el menú contextual del **Explorador de soluciones**. Los proyectos de CMake no usan este archivo porque todos los comandos de compilación se especifican en *CMakeLists.txt*. Para los sistemas de compilación diferentes de CMake, *tasks.vs.json* es donde se pueden especificar los comandos de compilación e invocar los scripts de compilación. Para obtener información general sobre el uso de *tasks.vs.json*, vea [Personalización de las tareas de compilación y depuración para el desarrollo de "Abrir carpeta"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

Una tarea cuenta con una propiedad `type` que puede tener uno de estos cuatro valores: `default`, `launch`, `remote` o `msbuild`. La mayoría de las tareas deben usar `launch` a menos que se requiera una conexión remota.

## <a name="default-properties"></a>Propiedades predeterminadas

Las propiedades predeterminadas están disponibles en todos los tipos de tareas:

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`taskLabel`|cadena| (Requerido) Especifica la etiqueta de tarea que se usa en la interfaz de usuario.|
|`appliesTo`|cadena| (Requerido) Especifica los archivos en los que se puede realizar el comando. Se admite el uso de caracteres comodín como, por ejemplo: " *", "* .cpp" y "/*.txt"|
|`contextType`|cadena| Valores permitidos: "custom", "build", "clean" y "rebuild". Determina dónde aparecerá la tarea en el menú contextual. El valor predeterminado es "custom".|
|`output`|cadena| Especifica una etiqueta de salida para la tarea.|
|`inheritEnvironments`|array| Especifica un conjunto de variables de entorno heredado de varios orígenes. Se pueden definir variables en archivos como *CMakeSettings.json* o *CppProperties.json* y hacer que estén disponibles en el contexto de la tarea. **Visual Studio 16.4**: especifique las variables de entorno por tarea mediante la sintaxis `env.VARIABLE_NAME`. Para anular la configuración de una variable, establézcala en "NULL".|
|`passEnvVars`|booleano| Especifica si se van a incluir o no variables de entorno adicionales en el contexto de la tarea. Estas variables son diferentes de las definidas mediante la propiedad `envVars`. El valor predeterminado es "true".|

## <a name="launch-properties"></a>Propiedades de inicio

Cuando el tipo de tarea es `launch`, estas propiedades están disponibles:

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`command`|cadena| Especifica la ruta de acceso completa del proceso o script que se va a iniciar.|
|`args`|array| Especifica una lista separada por comas de argumentos que se pasan al comando.|
|`launchOption`|cadena| Valores permitidos: "None", "ContinueOnError" e "IgnoreError". Especifica cómo continuar con el comando cuando hay errores.|
|`workingDirectory`|cadena| Especifica el directorio en el que se ejecutará el comando. El valor predeterminado es el directorio de trabajo actual del proyecto.|
|`customLaunchCommand`|cadena| Especifica una personalización de ámbito global que se va a aplicar antes de ejecutar el comando. Resulta útil para establecer variables de entorno, como %PATH%.|
|`customLaunchCommandArgs`|cadena| Especifica los argumentos en customLaunchCommand. (Requiere `customLaunchCommand`).|
 `env`| Especifica una lista de pares clave-valor de variables de entorno personalizadas. Por ejemplo, "myEnv": "myVal".|
|`commands`|array| Especifica una lista de comandos que se invocarán en orden.|

### <a name="example"></a>Ejemplo

Las tareas siguientes invocan *make.exe* cuando se proporciona un archivo Make en la carpeta y el entorno de `Mingw64` se ha definido en *CppProperties.json*, tal como se muestra en la [referencia de esquema de CppProperties.json](cppproperties-schema-reference.md#user_defined_environments):

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

Estas tareas se pueden invocar desde el menú contextual al hacer clic con el botón derecho en un archivo *.cpp* en el **Explorador de soluciones**.

## <a name="remote-properties"></a>Propiedades remotas

Las tareas remotas se habilitan cuando se instala la carga de trabajo Desarrollo para Linux con C++ y se agrega una conexión a una máquina remota mediante el Administrador de conexiones de Visual Studio. Una tarea remota ejecuta comandos en un sistema remoto y también puede copiar archivos en este.

Cuando el tipo de tarea es `remote`, estas propiedades están disponibles:

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`remoteMachineName`|cadena|Nombre de la máquina remota. Debe coincidir con el nombre de una máquina en el **Administrador de conexiones**.|
|`command`|cadena|Comando que se va a enviar a la máquina remota. De forma predeterminada, los comandos se ejecutan en el directorio $HOME del sistema remoto.|
|`remoteWorkingDirectory`|cadena|Directorio de trabajo actual en la máquina remota.|
|`localCopyDirectory`|cadena|Directorio local que se va a copiar en la máquina remota. El valor predeterminado es el directorio de trabajo actual.|
|`remoteCopyDirectory`|cadena|Directorio de la máquina remota en el que se copia `localCopyDirectory`.|
|`remoteCopyMethod`|cadena| Método que se va a usar para copiar. Valores permitidos: "none", "sftp" y "rsync". Para proyectos de gran tamaño se recomienda rsync.|
|`remoteCopySourcesOutputVerbosity`|cadena| Valores permitidos: "Normal", "Verbose" y "Diagnostic".|
|`rsyncCommandArgs`|cadena|El valor predeterminado es "-t --delete".|
|`remoteCopyExclusionList`|array|Lista de archivos separados por comas en `localCopyDirectory` que se van a excluir de las operaciones de copia.|

### <a name="example"></a>Ejemplo

La tarea siguiente aparecerá en el menú contextual al hacer clic con el botón derecho en *main.cpp* en el **Explorador de soluciones**. Depende de una máquina remota llamada `ubuntu` en el **Administrador de conexiones**. La tarea copia la carpeta abierta actual en Visual Studio en el directorio `sample` de la máquina remota y, después, invoca g++ para compilar el programa.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>propiedades de MSBuild

Cuando el tipo de tarea es `msbuild`, estas propiedades están disponibles:

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`verbosity`|cadena| Especifica los valores de verbosityAllowed de la salida de la compilación del proyecto de MSBuild: "Quiet", "Minimal", "Normal", "Detailed" y "Diagnostic".|
|`toolsVersion`|cadena| Especifica la versión del conjunto de herramientas para compilar el proyecto, por ejemplo "2.0", "3.5", "4.0" y "Current". El valor predeterminado es "Current".|
|`globalProperties`|objeto|Especifica una lista de valores de clave de las propiedades globales que se van a pasar al proyecto como, por ejemplo, "Configuration":"Release".|
|`properties`|objeto| Especifica una lista de valores de clave de propiedades de solo proyecto adicionales.|
|`targets`|array| Especifica la lista de destinos que se van a invocar, en orden, en el proyecto. Si no se especifica ninguno, se usa el destino predeterminado del proyecto.|
