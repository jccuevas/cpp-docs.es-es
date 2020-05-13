---
title: Configuración de sesiones de depuración de CMake en Visual Studio
description: Describe cómo usar Visual Studio para configurar la configuración del depurador de CMake.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328857"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurar sesiones de depuración de CMake

::: moniker range="vs-2015"

La compatibilidad con CMake nativo está disponible en Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end

::: moniker range=">=vs-2017"

Todos los destinos de CMake ejecutables se muestran en la lista desplegable **Elemento de inicio** en la barra de herramientas **General**. Seleccione uno para iniciar una sesión de depuración e iniciar el depurador.

![Lista desplegable de elementos de inicio de CMake](media/cmake-startup-item-dropdown.png "Lista desplegable de elementos de inicio de CMake")

También puede iniciar una sesión de depuración desde el Explorador de soluciones. En primer lugar, cambie a **la vista de destinos de CMake** en la ventana **Explorador** de soluciones.

![Botón de vista de destinos de CMake](media/cmake-targets-view.png  "CMake Targets Ver elemento de menú")

A continuación, haga clic con el botón derecho en un ejecutable y seleccione **Depurar**. Este comando inicia automáticamente la depuración del destino seleccionado en función de la configuración activa.

## <a name="customize-debugger-settings"></a>Personalización de la configuración del depurador

Puede personalizar la configuración del depurador para cualquier destino CMake ejecutable en el proyecto. Se encuentran en un archivo de configuración denominado *launch.vs.json*, ubicado en una *`.vs`* carpeta de la raíz del proyecto. Un archivo de configuración de inicio es útil en la mayoría de los escenarios de depuración, ya que puede configurar y guardar los detalles de configuración de depuración. Hay tres puntos de entrada a este archivo:

- **Menú Depurar:** Seleccione **Depurar > Depurar e Iniciar configuración para $-activeDebugTarget en** el menú principal para personalizar la configuración de depuración específica para el destino de depuración activo. Si no tiene un destino de depuración seleccionado, esta opción aparece atenuada.

![Punto de entrada del menú Depurar](media/cmake-debug-menu.png "Punto de entrada del menú Depurar")

- **Vista de objetivos:** Vaya a **la vista Destinos** en el Explorador de soluciones. A continuación, haga clic con el botón derecho en un destino de depuración y seleccione Agregar configuración de **depuración** para personalizar la configuración de depuración específica del destino seleccionado.

![Los objetivos ven el punto de entrada](media/cmake-targets-add-debug-configuration.png "Los objetivos ven el punto de entrada")

- **Raíz CMakeLists.txt:** Haga clic con el botón derecho en una *raíz CMakeLists.txt* y seleccione Agregar configuración de **depuración** para abrir el cuadro de diálogo **Seleccionar un depurador.** El cuadro de diálogo permite agregar *cualquier* tipo de configuración de depuración, `projectTarget` pero debe especificar manualmente el destino CMake para invocar a través de la propiedad.

![Seleccione un cuadro de diálogo del depurador](media/cmake-select-a-debugger.png "Seleccione un cuadro de diálogo del depurador")

Puede editar el archivo *launch.vs.json* para crear configuraciones de depuración para cualquier número de destinos CMake. Al guardar el archivo, Visual Studio crea una entrada para cada nueva configuración en el elemento de **inicio** desplegable.

## <a name="reference-keys-in-cmakesettingsjson"></a>Claves de referencia en CMakeSettings.json

Para hacer referencia a cualquier clave de un `cmake.` archivo *CMakeSettings.json,* anteponga a ella en *launch.vs.json*. En el ejemplo siguiente se muestra un archivo *launch.vs.json* simple que extrae el valor de la `remoteCopySources` clave en el archivo *CMakeSettings.json* para la configuración seleccionada actualmente:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

**Las variables** de entorno definidas en *CMakeSettings.json* también se `${env.VARIABLE_NAME}`pueden utilizar en launch.vs.json utilizando la sintaxis . En Visual Studio 2019 versión 16.4 y versiones posteriores, los destinos de depuración se inician automáticamente con el entorno especificado en *CMakeSettings.json*. Puede desestablecer una variable de entorno estableciéndola en **null**.

## <a name="launchvsjson-reference"></a>Referencia Launch.vs.json

Hay muchas propiedades *launch.vs.json* para admitir todos los escenarios de depuración. Las siguientes propiedades son comunes a todas las configuraciones de depuración, tanto remotas como locales:

- `projectTarget`: especifica el destino CMake que se va a invocar al compilar el proyecto. Visual Studio rellena automáticamente esta propiedad si escribe *launch.vs.json* desde el **menú Depurar** o **la vista de destinos**. Este valor debe coincidir con el nombre de un destino de depuración existente que aparece en la lista desplegable Elemento de **inicio.**

- `env`: Variables de entorno adicionales para agregar utilizando la sintaxis:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: argumentos de línea de comandos pasados al programa para depurar.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Referencia Launch.vs.json para proyectos remotos y WSL

En Visual Studio 2019 versión 16.6, `type: cppgdb` agregamos una nueva configuración de depuración para simplificar la depuración en sistemas remotos y WSL. Las configuraciones `type: cppdbg` de depuración antiguas de todavía se soportan.

### <a name="configuration-type-cppgdb"></a>Tipo de configuración`cppgdb`

- `name`: un nombre descriptivo para identificar la configuración en el menú desplegable Elemento de **inicio.**
- `project`: especifica la ruta relativa al archivo de proyecto. Normalmente, no es necesario cambiar esta ruta de acceso al depurar un proyecto CMake.
- `projectTarget`: especifica el destino CMake que se va a invocar al compilar el proyecto. Visual Studio rellena automáticamente esta propiedad si escribe *launch.vs.json* desde el **menú Depurar** o **la vista de destinos**. Este valor de destino debe coincidir con el nombre de un destino de depuración existente que aparece en la lista desplegable Elemento de **inicio.**
- `debuggerConfiguration`: indica qué conjunto de valores predeterminados de depuración se van a utilizar. En Visual Studio 2019 versión 16.6, la única opción válida es `gdb`. Las versiones `gdbserver`anteriores también admiten archivos .
- `args`: argumentos de línea de comandos pasados al inicio al programa que se está depurando.
- `env`: variables de entorno adicionales pasadas al programa que se está depurando. Por ejemplo, `{"DISPLAY": "0.0"}`.
- `processID`: ID de proceso de Linux al que adjuntar. Solo se utiliza cuando se conecta a un proceso remoto. Para obtener más información, consulte [Solución de problemas de asociación a procesos mediante GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Opciones adicionales `gdb` para la configuración

- `program`: El `"${debugInfo.fullTargetPath}"`valor predeterminado es . La ruta de acceso de Unix a la aplicación para depurar. Solo es necesario si es diferente del ejecutable de destino en la ubicación de compilación o implementación.
- `remoteMachineName`: El `"${debugInfo.remoteMachineName}"`valor predeterminado es . Nombre del sistema remoto que hospeda el programa que se va a depurar. Solo es necesario si es diferente que el sistema de compilación. Debe tener una entrada existente en [Connection Manager](../linux/connect-to-your-remote-linux-computer.md). Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas existentes.
- `cwd`: El `"${debugInfo.defaultWorkingDirectory}"`valor predeterminado es . La ruta de acceso de Unix `program` al directorio en el sistema remoto donde se ejecuta. El directorio debe existir.
- `gdbpath`: El `/usr/bin/gdb`valor predeterminado es . Ruta completa de `gdb` Unix a la utilizada para depurar. Solo es necesario si `gdb`se utiliza una versión personalizada de .
- `preDebugCommand`: un comando de Linux `gdb`para ejecutarse inmediatamente antes de invocar . `gdb`no se inicia hasta que se completa el comando. Puede utilizar la opción para ejecutar un `gdb`script antes de la ejecución de .

#### <a name="deployment-options"></a>Opciones de implementación

Utilice las siguientes opciones para separar el equipo de compilación (definido en CMakeSettings.json) del equipo de depuración remoto.

- `remoteMachineName`: Máquina de depuración remota. Solo es necesario si es diferente de la máquina de compilación. Debe tener una entrada existente en [Connection Manager](../linux/connect-to-your-remote-linux-computer.md). Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas existentes.
- `disableDeploy`: El `false`valor predeterminado es . Indica si la separación de compilación/depuración está deshabilitada. Cuando `false`, esta opción permite que se produzcan la compilación y la depuración en dos equipos independientes.
- `deployDirectory`: Ruta completa de `remoteMachineName` Unix al directorio en el que se copia el ejecutable.
- `deploy`: una serie de configuraciones de implementación avanzadas. Solo necesita configurar estas opciones cuando desee un control más detallado sobre el proceso de implementación. De forma predeterminada, solo los archivos necesarios para que el proceso de depuración se implementen en el equipo de depuración remoto.
  - `sourceMachine`: el equipo desde el que se copia el archivo o directorio. Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas almacenadas en Connection Manager. Al compilar de forma nativa en WSL, se omite esta opción.
  - `targetMachine`: el equipo en el que se copia el archivo o directorio. Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas almacenadas en Connection Manager.
  - `sourcePath`: la ubicación del `sourceMachine`archivo o directorio en .
  - `targetPath`: la ubicación del `targetMachine`archivo o directorio en .
  - `deploymentType`: una descripción del tipo de implementación. `LocalRemote`y `RemoteRemote` son compatibles. `LocalRemote`significa copiar desde el sistema de archivos local `remoteMachineName` al sistema remoto especificado por en *launch.vs.json*. `RemoteRemote`significa copiar desde el sistema de compilación remota especificado en *CMakeSettings.json* al sistema remoto diferente especificado en *launch.vs.json*.
  - `executable`: indica si el archivo implementado es un ejecutable.

### <a name="execute-custom-gdb-commands"></a>Ejecutar `gdb` comandos personalizados

Visual Studio admite `gdb` la ejecución de comandos personalizados para interactuar directamente con el depurador subyacente. Para obtener más información, consulte [Ejecución de comandos lldb personalizados. `gdb` ](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)

### <a name="enable-logging"></a>Habilitación del registro

Habilite el registro MIEngine para `gdb`ver qué `gdb` comandos se envían a , qué salida devuelve y cuánto tiempo tarda cada comando. [Más información](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Tipo de configuración`cppdbg`

Las siguientes opciones se pueden utilizar al depurar en un `cppdbg` sistema remoto o WSL mediante el tipo de configuración. En Visual Studio 2019 versión 16.6 o posterior, se recomienda el tipo `cppgdb` de configuración.

- `name`: un nombre descriptivo para identificar la configuración en el menú desplegable Elemento de **inicio.**

- `project`: especifica la ruta relativa al archivo de proyecto. Normalmente, no es necesario cambiar este valor al depurar un proyecto CMake.

- `projectTarget`: especifica el destino CMake que se va a invocar al compilar el proyecto. Visual Studio rellena automáticamente esta propiedad si escribe *launch.vs.json* desde el **menú Depurar** o **la vista de destinos**. Este valor debe coincidir con el nombre de un destino de depuración existente que aparece en la lista desplegable Elemento de **inicio.**

- `args`: argumentos de línea de comandos pasados al inicio al programa que se está depurando.

- `processID`: ID de proceso de Linux al que adjuntar. Solo se utiliza cuando se conecta a un proceso remoto. Para obtener más información, consulte [Solución de problemas de asociación a procesos mediante GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: El `"${debugInfo.fullTargetPath}"`valor predeterminado es . La ruta de acceso de Unix a la aplicación para depurar. Solo es necesario si es diferente del ejecutable de destino en la ubicación de compilación o implementación.

- `remoteMachineName`: El `"${debugInfo.remoteMachineName}"`valor predeterminado es . Nombre del sistema remoto que hospeda el programa que se va a depurar. Solo es necesario si es diferente que el sistema de compilación. Debe tener una entrada existente en [Connection Manager](../linux/connect-to-your-remote-linux-computer.md). Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas existentes.

- `cwd`: El `"${debugInfo.defaultWorkingDirectory}"`valor predeterminado es . Ruta de acceso completa de Unix `program` al directorio en el sistema remoto donde se ejecuta. El directorio debe existir.

- `environment`: variables de entorno adicionales pasadas al programa que se está depurando. Por ejemplo,

  ```json
    "environment": [
        {
          "name": "ENV1",
          "value": "envvalue1"
        },
        {
          "name": "ENV2",
          "value": "envvalue2"
        }
      ]
  ```

- `pipeArgs`: una matriz de argumentos de línea de comandos pasados al programa de canalización para configurar la conexión. El programa de canalización se utiliza para `gdb`retransmitir entrada/salida estándar entre Visual Studio y . La mayor parte de esta matriz **no necesita personalizarse al** depurar proyectos CMake. La excepción `${debuggerCommand}`es el `gdb` , que se inicia en el sistema remoto. Se puede modificar para:

  - Exporte el valor de la variable de entorno DISPLAY en su sistema Linux. En el ejemplo siguiente, `:1`este valor es .

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "export DISPLAY=:1;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

  - Ejecute un script antes `gdb`de la ejecución de . Asegúrese de que los permisos de ejecución se establecen en el script.

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`: un booleano que especifica si se debe romper tan pronto como se inicia el proceso. El valor predeterminado es false.

- `visualizerFile`: un [archivo .natvis](/visualstudio/debugger/create-custom-views-of-native-objects) que se usará al depurar este proceso. Esta opción no `gdb` es compatible con la impresión bonita. También `showDisplayString` se establece al establecer esta propiedad.

- `showDisplayString`: un booleano que habilita `visualizerFile` la cadena de visualización cuando se especifica a. Establecer esta `true` opción puede provocar un rendimiento más lento durante la depuración.

- `setupCommands`: uno `gdb` o más comandos que se ejecutarán para configurar el depurador subyacente.

- `miDebuggerPath`: La ruta `gdb`completa a . Cuando no se especifica, Visual Studio busca primero la ruta de acceso para el depurador.

- Por último, el tipo de `cppgdb` `cppdbg` configuración también puede utilizar todas las opciones de implementación definidas para el tipo de configuración.

### <a name="debug-using-gdbserver"></a>Depurar usando`gdbserver`

Puede configurar `cppdbg` la configuración `gdbserver`para depurar mediante . Puede encontrar más detalles y una configuración de lanzamiento de ejemplo en la entrada Del blog del equipo de Microsoft C++ Depuración de [proyectos de Linux CMake con `gdbserver` ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Consulte también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)\
[Configurar un proyecto de Linux CMake](../linux/cmake-linux-project.md)\
[Conéctese a su ordenador Linux remoto](../linux/connect-to-your-remote-linux-computer.md)\
[Personalizar la configuración de compilación de CMake](customize-cmake-settings.md)\
[Configurar sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)\
[Implemente, ejecute y depure su proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
