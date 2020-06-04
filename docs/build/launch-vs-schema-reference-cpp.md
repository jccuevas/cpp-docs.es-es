---
title: Referencia del esquema launch.vs.json (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323056"
---
# <a name="launchvsjson-schema-reference-c"></a>Referencia del esquema launch.vs.json (C++)

Use el archivo *launch.vs.json* para configurar parámetros de depuración. Para crear el archivo, haga clic con el botón derecho en un archivo ejecutable en el **Explorador de soluciones** y elija **Configuración de depuración e inicio**. Elija la opción que más se aproxime al proyecto y, a continuación, use las siguientes propiedades para modificar la configuración según sea necesario. Para obtener más información sobre la depuración de proyectos de CMake, vea [Configuración de sesiones de depuración de CMake](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Propiedades predeterminadas

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`name`|cadena|Especifica el nombre de la entrada en la lista desplegable del destino de depuración.|
|`type`|cadena|Especifica si el proyecto es un archivo DLL o un archivo .exe (el valor predeterminado es .exe).|
|`project`|cadena|Especifica la ruta de acceso relativa al archivo del proyecto.|
|`projectTarget`|cadena|Especifica el destino opcional invocado al compilar `project`. Este destino `projectTarget` debe existir y coincidir con el nombre de la lista desplegable **Destino de depuración**.|
|`debugType`|cadena|Especifica el modo de depuración según el tipo de código (nativo, administrado o mixto). Se detectará automáticamente a menos que se establezca este parámetro. Valores permitidos: "nativo", "administrado" y "mixto".|
|`inheritEnvironments`|array|Especifica un conjunto de variables de entorno heredadas de varios orígenes. Puede definir algunas variables en archivos como *CMakeSettings.json* o *CppProperties.json* y hacer que estén disponibles para depurar el contexto.  **Visual Studio 16.4:** Especifique las variables de entorno por destino mediante la sintaxis `env.VARIABLE_NAME`. Para anular la configuración de una variable, establézcala en "NULL".|
|`args`|array|Especifica los argumentos de línea de comandos que se pasan al programa iniciado.|
|`currentDir`|cadena|Especifica la ruta de acceso completa al directorio del destino de compilación. Se detectará automáticamente a menos que se establezca este parámetro.|
|`noDebug`|booleano|Especifica si se va a depurar el programa iniciado. Si no se especifica este parámetro, se usa el valor predeterminado `false`.|
|`stopOnEntry`|booleano|Especifica si se debe interrumpir en cuanto se inicie el proceso y se asocia el depurador. El valor predeterminado para este parámetro es `false`.|
|`remoteMachine`|cadena|Especifica el nombre de la máquina remota en la que se inicia el programa.|
|`env`|array| Especifica una lista de pares clave-valor de variables de entorno personalizadas. env:{"myEnv":"myVal"}.|
|`portName`|cadena|Especifica el nombre del puerto cuando se asocia a un proceso en ejecución.|
|`buildConfigurations`|array| Un par clave-valor que especifica el nombre del modo de compilación para aplicar las configuraciones. Por ejemplo, `Debug` o `Release` y las configuraciones que se van a usar según el modo de compilación seleccionado.

## <a name="c-linux-properties"></a>Propiedades de Linux para C++

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`program`|cadena|Ruta de acceso completa al ejecutable del programa en la máquina remota. Al usar CMake, la macro `${debugInfo.fullTargetPath}` se puede usar como valor de este campo.|
|`processId`|enteros|Identificador de proceso opcional al que se va a asociar el depurador.|
|`sourceFileMap`|objeto|Asignaciones de archivo de código fuente opcionales que se pasan al motor de depuración. Formato: `{ "\<Compiler source location>": "\<Editor source location>" }` o `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Ejemplo: `{ "/home/user/foo": "C:\\foo" }` o `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Consulte la sección [Opciones de asignación de archivos de código fuente](#source_file_map_options).|
|`additionalProperties`|cadena|Uno de los elementos sourceFileMapOptions. (Vea a continuación).|
|`MIMode`|cadena|Indica el tipo de depurador de consola habilitado para MI al que MIDebugEngine se conectará. Los valores permitidos son "gdb" y "lldb".|
|`args`|array|Argumentos de la línea de comandos que se pasan al programa.|
|`environment`|array|Variables de entorno que se agregan al entorno del programa. Ejemplo: [ { "name": "squid", "value": "clam" } ].|
|`targetArchitecture`|cadena|La arquitectura del depurado. Se detectará automáticamente a menos que se establezca este parámetro. Los valores permitidos son x86, arm, arm64, mips, x64, amd64 y x86_64.|
|`visualizerFile`|cadena|El archivo .natvis que se usará para depurar este proceso. Esta opción no es compatible con la impresión con sangría de GDB. Consulte "showDisplayString" si va a usar esta opción.|
|`showDisplayString`|booleano|Cuando se especifica visualizerFile, showDisplayString habilita la cadena para mostrar. La activación de esta opción puede ralentizar el rendimiento durante la depuración.|
|`remoteMachineName`|cadena|La máquina remota de Linux que hospeda gdb y el programa que se va a depurar. Use el Administrador de conexiones para agregar nuevas máquinas Linux. Al usar CMake, la macro `${debugInfo.remoteMachineName}` se puede usar como valor de este campo.|
|`cwd`|cadena|El directorio de trabajo del destino en la máquina remota. Al usar CMake, la macro `${debugInfo.defaultWorkingDirectory}` se puede usar como valor de este campo. El valor predeterminado es la raíz del área de trabajo remota, a menos que se reemplace en el archivo *CMakeLists.txt*.|
|`miDebuggerPath`|cadena|La ruta de acceso del depurador habilitado para MI (como gdb). Si no se especifica, buscará primero la variable PATH del depurador.|
|`miDebuggerServerAddress`|cadena|La dirección de red del servidor del depurador habilitado para MI al que debe conectarse. Ejemplo: localhost:1234.|
|`setupCommands`|array|Uno o más comandos GDB/LLDB que se ejecutarán para configurar el depurador subyacente. Ejemplo: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Vea [Comandos de configuración de inicio](#launch_setup_commands).|
|`customLaunchSetupCommands`|array|Si se proporciona, reemplaza los comandos predeterminados que se usan para iniciar un destino por otros comandos. Por ejemplo, puede ser "-target-attach" para asociar a un proceso de destino. Una lista de comandos vacía reemplaza los comandos de inicio por nada, lo que puede resultar útil si se proporcionan las opciones de inicio del depurador como opciones de línea de comandos. Ejemplo: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|cadena|El comando que se va a ejecutar después de que el depurador esté totalmente configurado, para que el proceso de destino se ejecute. Los valores permitidos son "exec-run", "exec-continue" y "None". El valor predeterminado es "exec-run".|
|`debugServerPath`|cadena|La ruta de acceso completa opcional al servidor de depuración que se va a iniciar. El valor predeterminado es NULL.|
|`debugServerArgs`|cadena|Argumentos opcionales del servidor de depuración. El valor predeterminado es NULL.|
|`filterStderr`|booleano|Busca la secuencia stderr para el patrón iniciado por el servidor y registra stderr en la salida de depuración. Tiene como valor predeterminado `false`.|
|`coreDumpPath`|cadena|La ruta de acceso completa opcional a un archivo de volcado de memoria básico para el programa especificado. El valor predeterminado es NULL.|
externalConsole|booleano|Si es "true", se inicia una consola para el depurado. Si es `false`, no se inicia ninguna consola. Tiene como valor predeterminado `false`. NOTA: Esta opción se omite en algunos casos por motivos técnicos.|
|`pipeTransport`|cadena|Cuando está presente, indica al depurador que se conecte a un equipo remoto usando otro ejecutable como canalización, que reenviará la entrada o salida estándar entre Visual Studio y el depurador habilitado para MI (como gdb). Valores permitidos: una o más [opciones de transporte de canalización](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a> Comandos de configuración de inicio

Se usan con la propiedad `setupCommands`:

||||
|-|-|-|
|`text`|cadena|El comando del depurador que se va a ejecutar.|
|`description`|cadena|Una descripción opcional del comando.|
|`ignoreFailures`|booleano|Si es "true", los errores del comando deben omitirse. Tiene como valor predeterminado `false`.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a> Opciones de transporte de canalización

Se usan con la propiedad `pipeTransport`:

||||
|-|-|-|
|`pipeCwd`|cadena|La ruta de acceso completa al directorio de trabajo del programa de canalización.|
|`pipeProgram`|cadena|El comando de canalización completo que se va a ejecutar.|
|`pipeArgs`|array|Argumentos de la línea de comandos que se pasan al programa de canalización para configurar la conexión.|
|`debuggerPath`|cadena|La ruta de acceso completa al depurador en la máquina de destino. Por ejemplo, /usr/bin/gdb.|
|`pipeEnv`|objeto|Variables de entorno que se pasan al programa de canalización.|
|`quoteArgs`|booleano|Si los argumentos individuales contienen caracteres (como espacios o tabulaciones), ¿debe incluirse entre comillas? Si es `false`, el comando del depurador ya no se incluirá automáticamente entre comillas. El valor predeterminado es `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a> Opciones de asignación de archivos de código fuente

Se usan con la propiedad `sourceFileMap`:

||||
|-|-|-|
|`editorPath`|cadena|La ubicación del código fuente del editor que se va a buscar.|
|`useForBreakpoints`|booleano|Al establecer puntos de interrupción, se debe usar esta asignación de código fuente. Si es `false`, solo se usan el nombre de archivo y el número de línea para establecer los puntos de interrupción. Si es `true`, los puntos de interrupción solo se establecerán con la ruta de acceso completa al archivo y el número de línea cuando se use esta asignación de código fuente. De lo contrario, solo se usarán el nombre de archivo y el número de línea para establecer los puntos de interrupción. El valor predeterminado es `true`.|
