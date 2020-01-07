---
title: Referencia del esquema Tasks. vs.C++JSON ()
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: cc6b2983d3cc3d40449357a554df5feee38c21d9
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556661"
---
# <a name="tasksvsjson-schema-reference-c"></a>Referencia del esquema Tasks. vs.C++JSON ()

Para indicar a Visual Studio cómo compilar el código fuente en un proyecto de carpeta abierta, agregue un archivo *Tasks. vs. JSON* . Puede definir cualquier tarea arbitraria aquí y, a continuación, invocarla en el menú contextual **Explorador de soluciones** . Los proyectos de CMake no usan este archivo porque todos los comandos de compilación se especifican en *archivo CMakeLists. txt*. En el caso de los sistemas de compilación distintos de CMake, *Tasks. vs. JSON* es donde puede especificar comandos de compilación e invocar scripts de compilación. Para obtener información general sobre el uso de *Tasks. vs. JSON*, consulte [Personalización de las tareas de compilación y depuración para el desarrollo de "Abrir carpeta"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

Una tarea tiene una propiedad `type` que puede tener uno de cuatro valores: `default`, `launch`, `remote`o `msbuild`. La mayoría de las tareas deben usar `launch` a menos que se requiera una conexión remota.

## <a name="default-properties"></a>Propiedades predeterminadas

Las propiedades predeterminadas están disponibles en todos los tipos de tareas:

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`taskLabel`|cadena| (Obligatorio). Especifica la etiqueta de tarea usada en la interfaz de usuario.|
|`appliesTo`|cadena| (Obligatorio). Especifica los archivos en los que se puede realizar el comando. Se admite el uso de caracteres comodín, por ejemplo: " *", "* . cpp", "/*. txt"|
|`contextType`|cadena| Valores permitidos: "Custom", "Build", "Clean", "Rebuild". Determina dónde aparecerá la tarea en el menú contextual. El valor predeterminado es "Custom".|
|`output`|cadena| Especifica una etiqueta de salida para la tarea.|
|`inheritEnvironments`|matriz| Especifica un conjunto de variables de entorno heredadas de varios orígenes. Puede definir variables en archivos como *CMakeSettings. JSON* o *CppProperties. JSON* y hacer que estén disponibles para el contexto de la tarea. **Visual Studio 16,4:** : especifique las variables de entorno por tarea mediante la sintaxis de `env.VARIABLE_NAME`. Para anular la definición de una variable, establézcala en "null".|
|`passEnvVars`|booleano| Especifica si se van a incluir o no variables de entorno adicionales en el contexto de la tarea. Estas variables son diferentes de las definidas mediante la propiedad `envVars`. El valor predeterminado es "true".|

## <a name="launch-properties"></a>Propiedades de inicio

Cuando el tipo de tarea es `launch`, estas propiedades están disponibles:

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`command`|cadena| Especifica la ruta de acceso completa del proceso o script que se va a iniciar.|
|`args`|matriz| Especifica una lista separada por comas de argumentos pasados al comando.|
|`launchOption`|cadena| Valores permitidos: "none", "ContinueOnError", "IgnoreError". Especifica cómo continuar con el comando cuando hay errores.|
|`workingDirectory`|cadena| Especifica el directorio en el que se ejecutará el comando. Tiene como valor predeterminado el directorio de trabajo actual del proyecto.|
|`customLaunchCommand`|cadena| Especifica la personalización de ámbito global que se va a aplicar antes de ejecutar el comando. Resulta útil para establecer variables de entorno como% PATH%.|
|`customLaunchCommandArgs`|cadena| Especifica los argumentos de customLaunchCommand. (Requiere `customLaunchCommand`).|
 `env`| Especifica una lista de valores de clave de variables de entorno personalizadas. Por ejemplo, "myEnv": "myVal"|
|`commands`|matriz| Especifica una lista de comandos que se invocarán en orden.|

### <a name="example"></a>Ejemplo

Las siguientes tareas invocan a *make. exe* cuando se proporciona un archivo make en la carpeta y el entorno de `Mingw64` se ha definido en *CppProperties. JSON*, tal y como se muestra en [referencia de esquema de CppProperties. JSON](cppproperties-schema-reference.md#user_defined_environments):

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

Cuando el tipo de tarea es `remote`, estas propiedades están disponibles:

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`remoteMachineName`|cadena|Nombre del equipo remoto. Debe coincidir con un nombre de equipo en el **Administrador de conexiones**.|
|`command`|cadena|Comando que se va a enviar a la máquina remota. De forma predeterminada, los comandos se ejecutan en el directorio $HOME del sistema remoto.|
|`remoteWorkingDirectory`|cadena|Directorio de trabajo actual en el equipo remoto.|
|`localCopyDirectory`|cadena|Directorio local que se va a copiar en la máquina remota. Tiene como valor predeterminado el directorio de trabajo actual.|
|`remoteCopyDirectory`|cadena|Directorio del equipo remoto en el que se copia `localCopyDirectory`.|
|`remoteCopyMethod`|cadena| Método que se va a usar para copiar. Valores permitidos: "none", "SFTP", "rsync". se recomienda la sincronización de directorios para proyectos grandes.|
|`remoteCopySourcesOutputVerbosity`|cadena| Valores permitidos: "normal", "verbose", "Diagnostic".|
|`rsyncCommandArgs`|cadena|El valor predeterminado es "-t--delete".|
|`remoteCopyExclusionList`|matriz|Lista de archivos separados por comas en `localCopyDirectory` que se van a excluir de las operaciones de copia.|

### <a name="example"></a>Ejemplo

La siguiente tarea aparecerá en el menú contextual al hacer clic con el botón secundario en *Main. cpp* en **Explorador de soluciones**. Depende de un equipo remoto llamado `ubuntu` en el **Administrador de conexiones**. La tarea copia la carpeta abierta actual en Visual Studio en el directorio `sample` del equipo remoto y, a continuación, invoca g + + para compilar el programa.

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
|`verbosity`|cadena| Especifica los valores verbosityAllowed de salida de la compilación del proyecto de MSBuild: "Quiet", "minimal", "normal", "detailed", "Diagnostic".|
|`toolsVersion`|cadena| Especifica la versión del conjunto de herramientas para compilar el proyecto, por ejemplo "2,0", "3,5", "4,0", "actual". El valor predeterminado es "Current".|
|`globalProperties`|Objeto de|Especifica una lista de valores de clave de las propiedades globales que se van a pasar al proyecto, por ejemplo, "Configuration": "release"|
|`properties`|Objeto de| Especifica una lista de valores de clave de propiedades de solo proyecto adicionales.|
|`targets`|matriz| Especifica la lista de destinos que se invocarán, en orden, en el proyecto. Si no se especifica ninguno, se usa el destino predeterminado del proyecto.|
