---
title: Referencia de esquema launch.vs.json (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323056"
---
# <a name="launchvsjson-schema-reference-c"></a>Referencia de esquema launch.vs.json (C++)

Utilice el archivo *launch.vs.json* para configurar los parámetros de depuración. Para crear el archivo. Haga clic con el botón derecho en un archivo ejecutable en el **Explorador** de soluciones y elija **Depurar e iniciar configuración**. Elija la opción que coincida más estrechamente con el proyecto y, a continuación, utilice las siguientes propiedades para modificar la configuración según sea necesario. Para obtener más información sobre la depuración de proyectos CMake, vea [Configurar sesiones de depuración](/cpp/build/configure-cmake-debugging-sessions)de CMake .

## <a name="default-properties"></a>Propiedades predeterminadas

||||
|-|-|-|
|**Propiedad**|**Tipo**|**Descripción**|
|`name`|string|Especifica el nombre de la entrada en la lista desplegable Destino de depuración.|
|`type`|string|Especifica si el proyecto es un archivo dll o .exe (valor predeterminado es .exe)|
|`project`|string|Especifica la ruta de acceso relativa al archivo de proyecto.|
|`projectTarget`|string|Especifica el destino opcional `project`invocado al compilar . Esto `projectTarget` ya debe existir y coincide con el nombre en la lista desplegable Destino de **depuración.**|
|`debugType`|string|Especifica el modo de depuración según el tipo de código (nativo, administrado o mixto). Esto se detectará automáticamente a menos que se establezca este parámetro. Valores permitidos: "native", "managed", "mixed".|
|`inheritEnvironments`|array|Especifica un conjunto de variables de entorno heredadas de varios orígenes. Puede definir algunas variables en archivos como *CMakeSettings.json* o *CppProperties.json* y ponerlas a disposición del contexto de depuración.  **Visual Studio 16.4:**: especifique las variables de `env.VARIABLE_NAME` entorno por destino mediante la sintaxis. Para desestablecer una variable, establézcala en "null".|
|`args`|array|Especifica los argumentos de línea de comandos pasados al programa iniciado.|
|`currentDir`|string|Especifica la ruta de acceso completa del directorio al destino de compilación. Esto se detectará automáticamente a menos que se establezca este parámetro.|
|`noDebug`|boolean|Especifica si se debe depurar el programa iniciado. El valor predeterminado para `false` este parámetro es si no se especifica.|
|`stopOnEntry`|boolean|Especifica si se debe interrumpir un solo momento en que se inicia el proceso y se adjunta el depurador. El valor predeterminado para `false`este parámetro es .|
|`remoteMachine`|string|Especifica el nombre del equipo remoto donde se inicia el programa.|
|`env`|array| Especifica una lista clave-valor de variables de entorno personalizadas. env:-"myEnv":"myVal".|
|`portName`|string|Especifica el nombre del puerto al asociarse a un proceso en ejecución.|
|`buildConfigurations`|array| Un par clave-valor que especifica el nombre del modo de compilación para aplicar las configuraciones. Por `Debug` ejemplo, `Release` o y las configuraciones que se utilizarán según el modo de compilación seleccionado.

## <a name="c-linux-properties"></a>Propiedades de C++ Linux

||||
|-|-|-|
|**Propiedad**|**Tipo**|**Descripción**|
|`program`|string|Ruta de acceso completa al ejecutable del programa en el equipo remoto. Cuando se utiliza CMake, la macro `${debugInfo.fullTargetPath}` se puede utilizar como valor de este campo.|
|`processId`|integer|IDENTIFICADOR de proceso opcional al que asociar el depurador.|
|`sourceFileMap`|object|Asignaciones de archivos de origen opcionales pasadas al motor de depuración. Formato: `{ "\<Compiler source location>": "\<Editor source location>" }` `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`o . Ejemplo: `{ "/home/user/foo": "C:\\foo" }` o `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Consulte [Opciones de mapa de archivos](#source_file_map_options)de origen .|
|`additionalProperties`|string|Uno de los sourceFileMapOptions. (Vea a continuación).|
|`MIMode`|string|Indica el tipo de depurador de consola habilitado para MI al que se conectará MIDebugEngine. Los valores permitidos son "gdb", "lldb".|
|`args`|array|Argumentos de línea de comandos pasados al programa.|
|`environment`|array|Variables de entorno que se agregaron al entorno del programa. Ejemplo: [ á "nombre": "calamar", "valor": "almeja" á ].|
|`targetArchitecture`|string|La arquitectura del depurador. Esto se detectará automáticamente a menos que se establezca este parámetro. Los valores permitidos son x86, arm, arm64, mips, x64, amd64 x86_64.|
|`visualizerFile`|string|.natvis que se utilizará al depurar este proceso. Esta opción no es compatible con la impresión bonita de GDB. Consulte "showDisplayString" si usa esta configuración.|
|`showDisplayString`|boolean|Cuando se especifica un visualizerFile, showDisplayString habilitará la cadena de presentación. Activar esta opción puede provocar un rendimiento más lento durante la depuración.|
|`remoteMachineName`|string|La máquina Linux remota que aloja gdb y el programa que se va a depurar. Use el Administrador de conexiones para agregar nuevas máquinas Linux. Cuando se utiliza CMake, la macro `${debugInfo.remoteMachineName}` se puede utilizar como valor de este campo.|
|`cwd`|string|El directorio de trabajo del destino en el equipo remoto. Cuando se utiliza CMake, la macro `${debugInfo.defaultWorkingDirectory}` se puede utilizar como valor de este campo. El valor predeterminado es la raíz del área de trabajo remota, a menos que se invalide en el archivo *CMakeLists.txt.*|
|`miDebuggerPath`|string|La ruta de acceso al depurador habilitado para MI (como gdb). Cuando no se especifica, buscará PATH primero para el depurador.|
|`miDebuggerServerAddress`|string|Dirección de red del servidor del depurador habilitado para MI al que conectarse. Ejemplo: localhost:1234.|
|`setupCommands`|array|Uno o más comandos GDB/LLDB para ejecutar para configurar el depurador subyacente. Ejemplo: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Consulte [Iniciar comandos de configuración](#launch_setup_commands).|
|`customLaunchSetupCommands`|array|Si se proporciona, esto reemplaza los comandos predeterminados utilizados para iniciar un destino con algunos otros comandos. Por ejemplo, esto puede ser "-target-attach" para adjuntar a un proceso de destino. Una lista de comandos vacía reemplaza los comandos de lanzamiento por nada, lo que puede ser útil si se proporcionan opciones de inicio al depurador como opciones de línea de comandos. Ejemplo: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|string|El comando que se ejecuta después de que el depurador esté completamente configurado para que se ejecute el proceso de destino. Los valores permitidos son "exec-run", "exec-continue", "None". El valor predeterminado es "exec-run".|
|`debugServerPath`|string|Ruta de acceso completa opcional al servidor de depuración que se va a iniciar. El valor predeterminado es null.|
|`debugServerArgs`|string|Argumentos de servidor de depuración opcionales. El valor predeterminado es null.|
|`filterStderr`|boolean|Busque la secuencia stderr para el patrón iniciado por el servidor y registre stderr para depurar la salida. Su valor predeterminado es `false`.|
|`coreDumpPath`|string|Ruta de acceso completa opcional a un archivo de volcado de memoria para el programa especificado. El valor predeterminado es null.|
externalConsole|boolean|Si es true, se inicia una consola para el depurador. Si `false`, no se inicia ninguna consola. Su valor predeterminado es `false`. NOTA: Esta opción se omite en algunos casos por razones técnicas.|
|`pipeTransport`|string|Cuando está presente, esto indica al depurador que se conecte a un equipo remoto mediante otro ejecutable como una canalización que retransmitirá la entrada/salida estándar entre Visual Studio y el depurador habilitado para MI (como gdb). Valores permitidos: una o más opciones de transporte de [tuberías](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>Iniciar comandos de configuración

Utilizado con `setupCommands` la propiedad:

||||
|-|-|-|
|`text`|string|El comando del depurador que se va a ejecutar.|
|`description`|string|Descripción opcional para el comando.|
|`ignoreFailures`|boolean|Si es true, se deben omitir los errores del comando. Su valor predeterminado es `false`.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>Opciones de transporte de tuberías

Utilizado con `pipeTransport` la propiedad:

||||
|-|-|-|
|`pipeCwd`|string|La ruta de acceso completa al directorio de trabajo para el programa de tuberías.|
|`pipeProgram`|string|El comando de canalización completo que se va a ejecutar.|
|`pipeArgs`|array|Argumentos de línea de comandos pasados al programa de canalización para configurar la conexión.|
|`debuggerPath`|string|La ruta de acceso completa al depurador en el equipo de destino, por ejemplo /usr/bin/gdb.|
|`pipeEnv`|object|Variables de entorno pasadas al programa de tuberías.|
|`quoteArgs`|boolean|Si los argumentos individuales contienen caracteres (como espacios o tabulaciones), ¿debe citarse? Si `false`, el comando del depurador ya no se citará automáticamente. El valor predeterminado es `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>Opciones de mapa de archivos de origen

Usar con `sourceFileMap` la propiedad:

||||
|-|-|-|
|`editorPath`|string|La ubicación del código fuente para el editor que se va a localizar.|
|`useForBreakpoints`|boolean|Al establecer puntos de interrupción, se debe utilizar esta asignación de origen. Si `false`, solo se utiliza el nombre de archivo y el número de línea para establecer puntos de interrupción. Si `true`, los puntos de interrupción se establecerán con la ruta de acceso completa al archivo y al número de línea solo cuando se utilice esta asignación de origen. De lo contrario, solo se utilizarán el nombre de archivo y el número de línea al establecer puntos de interrupción. El valor predeterminado es `true`.|
