---
title: Referencia del esquema Launch. vs. JSONC++()
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 49b4f4e6c4359837e820684c29b0e102a08c3fd5
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556648"
---
# <a name="launchvsjson-schema-reference-c"></a>Referencia del esquema Launch. vs. JSONC++()

Use el archivo *Launch. vs. JSON* para configurar los parámetros de depuración. Para crear el archivo. Haga clic con el botón derecho en un archivo ejecutable en **Explorador de soluciones** y elija **configuración de depuración e inicio**. Elija la opción que más se aproxime al proyecto y, a continuación, use las siguientes propiedades para modificar la configuración según sea necesario:

## <a name="default-properties"></a>Propiedades predeterminadas

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`name`|cadena|Especifica el nombre de la entrada en la lista desplegable destino de depuración.|
|`type`|cadena|Especifica si el proyecto es una DLL o un archivo. exe (el valor predeterminado es. exe)|
|`project`|cadena|Especifica la ruta de acceso relativa al archivo de proyecto.|
|`projectTarget`|cadena|Especifica el destino opcional invocado al compilar `project`. Este `projectTarget` ya debe existir y coincidir con el nombre en la lista desplegable **destino de depuración** .|
|`debugType`|cadena|Especifica el modo de depuración según el tipo de código (nativo, administrado o mixto). Se detectará automáticamente a menos que se establezca este parámetro. Valores permitidos: "Native", "Managed", "Mixed".|
|`inheritEnvironments`|matriz|Especifica un conjunto de variables de entorno heredadas de varios orígenes. Puede definir algunas variables en archivos como *CMakeSettings. JSON* o *CppProperties. JSON* y hacer que estén disponibles para depurar el contexto.  **Visual Studio 16,4:** : especifique las variables de entorno por destino mediante la sintaxis de `env.VARIABLE_NAME`. Para anular la definición de una variable, establézcala en "null".|
|`args`|matriz|Especifica los argumentos de línea de comandos que se pasan al programa iniciado.|
|`currentDir`|cadena|Especifica la ruta de acceso completa al directorio para el destino de compilación. Se detectará automáticamente a menos que se establezca este parámetro.|
|`noDebug`|booleano|Especifica si se va a depurar el programa iniciado. El valor predeterminado de este parámetro es `false` si no se especifica.|
|`stopOnEntry`|booleano|Especifica si se debe interrumpir un instante a medida que se inicia el proceso y se adjunta el depurador. El valor predeterminado de este parámetro es `false`.|
|`remoteMachine`|cadena|Especifica el nombre del equipo remoto en el que se inicia el programa.|
|`env`|matriz| Especifica una lista de valores de clave de variables de entorno personalizadas. ENV: {"myEnv": "myVal"}.|
|`portName`|cadena|Especifica el nombre del puerto al asociarse a un proceso en ejecución.|
|`buildConfigurations`|matriz| Par clave-valor que especifica el nombre del modo de compilación para aplicar las configuraciones. Por ejemplo, `Debug` o `Release` y las configuraciones que se van a usar según el modo de compilación seleccionado.

## <a name="c-linux-properties"></a>C++Propiedades de Linux

||||
|-|-|-|
|**Property**|**Type**|**Descripción**|
|`program`|cadena|Ruta de acceso completa al ejecutable del programa en el equipo remoto. Al utilizar CMake, la macro `${debugInfo.fullTargetPath}` se puede usar como valor de este campo.|
|`processId`|enteros|IDENTIFICADOR de proceso opcional al que adjuntar el depurador.|
|`sourceFileMap`|Objeto de|Asignaciones de archivo de origen opcionales que se pasan al motor de depuración. Format: `{ "\<Compiler source location>": "\<Editor source location>" }` o `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Ejemplo: `{ "/home/user/foo": "C:\\foo" }` o `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Consulte [Opciones de asignación de archivos de código fuente](#source_file_map_options).|
|`additionalProperties`|cadena|Uno de los sourceFileMapOptions. (Vea a continuación).|
|`MIMode`|cadena|Indica el tipo de depurador de consola habilitado para MI al que se conectará el MIDebugEngine. Los valores permitidos son "gdb", "lldb".|
|`args`|matriz|Argumentos de línea de comandos que se pasan al programa.|
|`environment`|matriz|Variables de entorno que se van a agregar al entorno para el programa. Ejemplo: [{"Name": "Squid", "Value": "almeja"}].|
|`targetArchitecture`|cadena|La arquitectura del código que se está depurando. Se detectará automáticamente a menos que se establezca este parámetro. Los valores permitidos son x86, ARM, arm64, MIPS, x64, AMD64 x86_64.|
|`visualizerFile`|cadena|archivo. natvis que se va a usar al depurar este proceso. Esta opción no es compatible con la impresión con sangría GDB. Consulte "showDisplayString" si se usa esta opción.|
|`showDisplayString`|booleano|Cuando se especifica visualizerFile, showDisplayString habilitará la cadena de presentación. Activar esta opción puede ralentizar el rendimiento durante la depuración.|
|`remoteMachineName`|cadena|El equipo de Linux remoto que hospeda gdb y el programa que se va a depurar. Use el Administrador de conexiones para agregar nuevas máquinas Linux. Al utilizar CMake, la macro `${debugInfo.remoteMachineName}` se puede usar como valor de este campo.|
|`cwd`|cadena|Directorio de trabajo del destino en el equipo remoto. Al utilizar CMake, la macro `${debugInfo.defaultWorkingDirectory}` se puede usar como valor de este campo. El valor predeterminado es la raíz del área de trabajo remota, a menos que se invalide en el archivo *archivo CMakeLists. txt* .|
|`miDebuggerPath`|cadena|La ruta de acceso al depurador habilitado para MI (como GDB). Si no se especifica, buscará primero la ruta de acceso del depurador.|
|`miDebuggerServerAddress`|cadena|Dirección de red del servidor del depurador habilitado para MI al que conectarse. Ejemplo: localhost: 1234.|
|`setupCommands`|matriz|Uno o más comandos GDB/LLDB para ejecutar con el fin de configurar el depurador subyacente. Ejemplo: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Consulte [iniciar comandos de instalación](#launch_setup_commands).|
|`customLaunchSetupCommands`|matriz|Si se proporciona, reemplaza los comandos predeterminados que se usan para iniciar un destino con otros comandos. Por ejemplo, puede ser "-Target-Attach" para asociar a un proceso de destino. Una lista de comandos vacía reemplaza los comandos de inicio sin nada, lo que puede resultar útil si se proporcionan las opciones de inicio del depurador como opciones de línea de comandos. Ejemplo: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|cadena|Comando que se va a ejecutar después de que el depurador esté totalmente configurado, para que el proceso de destino se ejecute. Los valores permitidos son "Exec-Run", "Exec-Continue", "none". El valor predeterminado es "Exec-Run".|
|`debugServerPath`|cadena|Ruta de acceso completa opcional para el servidor de depuración que se va a iniciar. Su valor predeterminado es NULL.|
|`debugServerArgs`|cadena|Argumentos opcionales del servidor de depuración. Su valor predeterminado es NULL.|
|`filterStderr`|booleano|Busque el flujo stderr para el patrón iniciado por el servidor y registre stderr para depurar la salida. Tiene como valor predeterminado `false`.|
|`coreDumpPath`|cadena|Ruta de acceso completa opcional a un archivo de volcado de memoria principal para el programa especificado. Su valor predeterminado es NULL.|
externalConsole|booleano|Si es true, se inicia una consola para el código que se está depurando. Si `false`, no se inicia ninguna consola. Tiene como valor predeterminado `false`. Nota: esta opción se omite en algunos casos por motivos técnicos.|
|`pipeTransport`|cadena|Cuando está presente, indica al depurador que se conecte a un equipo remoto mediante otro ejecutable como una canalización que retransmitirá la entrada/salida estándar entre Visual Studio y el depurador habilitado para MI (como GDB). Valores permitidos: una o más [Opciones de transporte de canalización](#pipe_transport_options).|


## <a name="launch_setup_commands"></a>Iniciar comandos de instalación

Se utiliza con la propiedad `setupCommands`:

||||
|-|-|-|
|`text`|cadena|Comando del depurador que se va a ejecutar.|
|`description`|cadena|Descripción opcional del comando.|
|`ignoreFailures`|booleano|Si es true, se deben omitir los errores del comando. Tiene como valor predeterminado `false`.|

## <a name = "pipe_transport_options"></a>Opciones de transporte de canalización

Se utiliza con la propiedad `pipeTransport`:

||||
|-|-|-|
|`pipeCwd`|cadena|Ruta de acceso completa al directorio de trabajo del programa de canalización.|
|`pipeProgram`|cadena|Comando de canalización completo que se va a ejecutar.|
|`pipeArgs`|matriz|Argumentos de la línea de comandos que se pasan al programa de canalización para configurar la conexión.|
|`debuggerPath`|cadena|La ruta de acceso completa al depurador en el equipo de destino, por ejemplo/usr/bin/gdb.|
|`pipeEnv`|Objeto de|Variables de entorno que se pasan al programa de canalización.|
|`quoteArgs`|booleano|Si los argumentos individuales contienen caracteres (como espacios o tabulaciones), ¿debe incluirse entre comillas? Si `false`, el comando del depurador ya no se incluirá automáticamente entre comillas. El valor predeterminado es `true`.|

## <a name="source_file_map_options"></a>Opciones de asignación de archivos de origen

Use con la propiedad `sourceFileMap`:

||||
|-|-|-|
|`editorPath`|cadena|Ubicación del código fuente del editor que se va a buscar.|
|`useForBreakpoints`|booleano|Al establecer puntos de interrupción, se debe usar esta asignación de origen. Si `false`, solo se usa el nombre de archivo y el número de línea para establecer los puntos de interrupción. Si `true`, los puntos de interrupción se establecerán con la ruta de acceso completa al archivo y el número de línea solo cuando se use esta asignación de origen. De lo contrario, solo se usará el nombre de archivo y el número de línea al establecer los puntos de interrupción. El valor predeterminado es `true`.|
