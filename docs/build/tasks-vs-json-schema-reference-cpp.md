---
title: Referencia del esquema Tasks. vs.C++JSON ()
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 1e533babafad554e8f7413d2bc1a88933a6eca42
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69975922"
---
# <a name="tasksvsjson-schema-reference-c"></a>Referencia del esquema Tasks. vs.C++JSON ()

Para indicar a Visual Studio cómo compilar el código fuente en un proyecto de carpeta abierta, agregue un archivo *Tasks. vs. JSON* . Puede definir cualquier tarea arbitraria aquí y, a continuación, invocarla en el menú contextual **Explorador de soluciones** . Los proyectos de CMake no usan este archivo porque todos los comandos de compilación se especifican en *archivo CMakeLists. txt*. En el caso de los sistemas de compilación distintos de CMake, *Tasks. vs. JSON* es donde puede especificar comandos de compilación e invocar scripts de compilación. Para obtener información general sobre el uso de *Tasks. vs. JSON*, consulte [Personalización de las tareas de compilación y depuración para el desarrollo de "Abrir carpeta"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

Una tarea tiene una `type` propiedad que puede tener uno de cuatro valores: `default`, `launch`, `remote`o `msbuild`. La mayoría de las `launch` tareas deben usar a menos que se requiera una conexión remota.

## <a name="default-properties"></a>Propiedades predeterminadas

Las propiedades predeterminadas están disponibles en todos los tipos de tareas:

||||
|-|-|-|
|**Propiedad**|**Type**|**Descripción**|
|`taskLabel`|string| (Requerido) Especifica la etiqueta de tarea usada en la interfaz de usuario.|
|`appliesTo`|string| (Requerido) Especifica los archivos en los que se puede realizar el comando. Se admite el uso de caracteres comodín, por ejemplo: " *", "* . cpp", "/*. txt"|
|`contextType`|string| Valores permitidos: "Custom", "Build", "Clean", "Rebuild". Determina dónde aparecerá la tarea en el menú contextual. El valor predeterminado es "Custom".|
|`output`|string| Especifica una etiqueta de salida para la tarea.|
|`inheritEnvironments`|array| Especifica un conjunto de variables de entorno heredadas de varios orígenes. Puede definir variables en archivos como *CMakeSettings. JSON* o *CppProperties. JSON* y hacer que estén disponibles para el contexto de la tarea.|
|`passEnvVars`|boolean| Especifica si se van a incluir o no variables de entorno adicionales en el contexto de la tarea. Estas variables son diferentes de las definidas mediante la `envVars` propiedad. El valor predeterminado es "true".|

## <a name="launch-properties"></a>Propiedades de inicio

Cuando el tipo de tarea `launch`es, estas propiedades están disponibles:

||||
|-|-|-|
|**Propiedad**|**Type**|**Descripción**|
|`command`|string| Especifica la ruta de acceso completa del proceso o script que se va a iniciar.|
|`args`|array| Especifica una lista separada por comas de argumentos pasados al comando.|
|`launchOption`|string| Valores permitidos: "None", "ContinueOnError", "IgnoreError". Especifica cómo continuar con el comando cuando hay errores.|
|`workingDirectory`|string| Especifica el directorio en el que se ejecutará el comando. Tiene como valor predeterminado el directorio de trabajo actual del proyecto.|
|`customLaunchCommand`|string| Especifica la personalización de ámbito global que se va a aplicar antes de ejecutar el comando. Resulta útil para establecer variables de entorno como% PATH%.|
|`customLaunchCommandArgs`|string| Especifica los argumentos de customLaunchCommand. (Requiere `customLaunchCommand`).|
 `env`| Especifica una lista de valores de clave de variables de entorno personalizadas. Por ejemplo, "myEnv": "myVal"|
|`commands`|array| Especifica una lista de comandos que se invocarán en orden.|

### <a name="example"></a>Ejemplo

Las siguientes tareas invocan a *make. exe* cuando se proporciona un archivo make en la `Mingw64` carpeta y el entorno se ha definido en *CppProperties. JSON*, tal y como se muestra en [referencia de esquema de CppProperties. JSON](cppproperties-schema-reference.md#user_defined_environments):

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

Estas tareas se pueden invocar desde el menú contextual al hacer clic con el botón secundario en un archivo *. cpp* en **Explorador de soluciones**.

## <a name="remote-properties"></a>Propiedades remotas

Las tareas remotas se habilitan cuando se instala el C++ desarrollo de Linux con carga de trabajo y se agrega una conexión a un equipo remoto mediante el administrador de conexiones de Visual Studio. Una tarea remota ejecuta comandos en un sistema remoto y también puede copiar archivos en ella.

Cuando el tipo de tarea `remote`es, estas propiedades están disponibles:

||||
|-|-|-|
|**Propiedad**|**Type**|**Descripción**|
|`remoteMachineName`|string|Nombre del equipo remoto. Debe coincidir con un nombre de equipo en el **Administrador de conexiones**.|
|`command`|string|Comando que se va a enviar a la máquina remota. De forma predeterminada, los comandos se ejecutan en el directorio $HOME del sistema remoto.|
|`remoteWorkingDirectory`|string|Directorio de trabajo actual en el equipo remoto.|
|`localCopyDirectory`|string|Directorio local que se va a copiar en la máquina remota. Tiene como valor predeterminado el directorio de trabajo actual.|
|`remoteCopyDirectory`|string|Directorio del equipo remoto en el que `localCopyDirectory` se copia.|
|`remoteCopyMethod`|string| Método que se va a usar para copiar. Valores permitidos: "none", "SFTP", "rsync". se recomienda la sincronización de directorios para proyectos grandes.|
|`remoteCopySourcesOutputVerbosity`|string| Valores permitidos: "Normal", "verbose", "Diagnostic".|
|`rsyncCommandArgs`|string|El valor predeterminado es "-t--delete".|
|`remoteCopyExclusionList`|array|Lista de archivos `localCopyDirectory` separados por comas de que se van a excluir de las operaciones de copia.|

### <a name="example"></a>Ejemplo

La siguiente tarea aparecerá en el menú contextual al hacer clic con el botón secundario en *Main. cpp* en **Explorador de soluciones**. Depende de un equipo remoto llamado `ubuntu` en el **Administrador de conexiones**. La tarea copia la carpeta abierta actual en Visual Studio en el `sample` directorio del equipo remoto y, a continuación, invoca g + + para compilar el programa.

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

Cuando el tipo de tarea `msbuild`es, estas propiedades están disponibles:

||||
|-|-|-|
|**Propiedad**|**Type**|**Descripción**|
|`verbosity`|string| Especifica los valores de verbosityAllowed de salida de compilación del proyecto de MSBuild: "Quiet", "minimal", "normal", "detailed", "Diagnostic".|
|`toolsVersion`|string| Especifica la versión del conjunto de herramientas para compilar el proyecto, por ejemplo "2,0", "3,5", "4,0", "actual". El valor predeterminado es "Current".|
|`globalProperties`|objeto|Especifica una lista de valores de clave de las propiedades globales que se van a pasar al proyecto, por ejemplo, "Configuration": "release"|
|`properties`|objeto| Especifica una lista de valores de clave de propiedades de solo proyecto adicionales.|
|`targets`|array| Especifica la lista de destinos que se invocarán, en orden, en el proyecto. Si no se especifica ninguno, se usa el destino predeterminado del proyecto.|
