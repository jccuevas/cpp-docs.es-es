---
title: Configuración de sesiones de depuración de CMake en Visual Studio
description: Describe cómo usar Visual Studio para configurar las opciones del depurador de CMake.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328857"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurar sesiones de depuración de CMake

::: moniker range="vs-2015"

La compatibilidad con CMake nativo está disponible en Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control de selector de **Versión** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end

::: moniker range=">=vs-2017"

Todos los destinos de CMake ejecutables se muestran en la lista desplegable **Elemento de inicio** en la barra de herramientas **General**. Seleccione una para empezar una sesión de depuración e iniciar el depurador.

![Lista desplegable de elemento de inicio de CMake](media/cmake-startup-item-dropdown.png "Lista desplegable de elemento de inicio de CMake")

También se puede iniciar una sesión de depuración desde el Explorador de soluciones. En primer lugar, cambie a **Vista de destinos de CMake** en la ventana **Explorador de soluciones**.

![Botón de vista de destinos de CMake](media/cmake-targets-view.png  "Elemento de menú Vista de destinos de CMake")

Después, haga clic con el botón derecho en un ejecutable y seleccione **Depurar**. Este comando inicia automáticamente la depuración del destino seleccionado en función de la configuración activa.

## <a name="customize-debugger-settings"></a>Personalización de la configuración del depurador

Se puede personalizar la configuración del depurador para cualquier destino de CMake ejecutable en el proyecto. Se encuentran en un archivo de configuración denominado *launch.vs.json*, ubicado en una carpeta *`.vs`* en la raíz del proyecto. Un archivo de configuración de inicio resulta útil en la mayoría de los escenarios de depuración, ya que se pueden configurar y guardar la información de configuración de la depuración. Hay tres puntos de entrada a este archivo:

- **Menú Depurar**: seleccione **Depurar > Configuración de depuración e inicio para ${activeDebugTarget}** en el menú principal para personalizar la configuración de depuración específica de su destino de depuración activo. Si no se tiene un destino de depuración seleccionado, esta opción aparece atenuada.

![Punto de entrada del menú Depurar](media/cmake-debug-menu.png "Punto de entrada del menú Depurar")

- **Vista de destinos**: vaya a **Vista de destinos** en el Explorador de soluciones. Luego, haga clic con el botón derecho en un destino de depuración y seleccione **Agregar configuración de depuración** para personalizar la configuración de depuración específica para el destino seleccionado.

![Punto de entrada de vista de destinos](media/cmake-targets-add-debug-configuration.png "Punto de entrada de vista de destinos")

- **Raíz CMakeLists.txt**: Haga clic con el botón derecho en una raíz *CMakeLists.txt* y seleccione **Agregar configuración de depuración** para abrir el cuadro de diálogo **Seleccionar un depurador**. El cuadro de diálogo permite agregar *cualquier* tipo de configuración de depuración, pero debe especificar manualmente el destino de CMake que se va a invocar a través de la propiedad `projectTarget`.

![Cuadro de diálogo Seleccionar un depurador](media/cmake-select-a-debugger.png "Cuadro de diálogo Seleccionar un depurador")

Se puede editar el archivo *launch.vs.json* a fin de crear configuraciones de depuración para cualquier número de destinos de CMake. Al guardar el archivo, Visual Studio crea una entrada para cada configuración nueva en la lista desplegable **Elemento de inicio**.

## <a name="reference-keys-in-cmakesettingsjson"></a>Claves de referencia en CMakeSettings.json

Para hacer referencia a cualquier clave en un archivo *CMakeSettings.json*, debe anteponer `cmake.` a este en *launch.vs.json*. En el ejemplo siguiente se muestra un archivo *launch.vs.json* simple que extrae el valor de la clave `remoteCopySources` en el archivo *CMakeSettings.json* para la configuración seleccionada actualmente:

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

Las **variables de entorno** definidas en *CMakeSettings.json* también se pueden usar en launch.vs.json con la sintaxis `${env.VARIABLE_NAME}`. En Visual Studio 2019, versión 16.4 y posteriores, los destinos de depuración se inician automáticamente con el entorno que se especifique en *CMakeSettings.json*. Se puede desactivar una variable de entorno al establecerla en **Null**.

## <a name="launchvsjson-reference"></a>Referencia de launch.vs.json

Hay muchas propiedades de *launch.vs.json* para admitir todos los escenarios de depuración. Las propiedades siguientes son comunes a todas las configuraciones de depuración, tanto remotas como locales:

- `projectTarget`: especifica el destino de CMake que se va a invocar al compilar el proyecto. Visual Studio rellena automáticamente esta propiedad si escribe *launch.vs.json* desde el **Menú Depurar** o **Vista de destinos**. Este valor debe coincidir con el nombre de un destino de depuración existente que aparezca en la lista desplegable **Elemento de inicio**.

- `env`: variables de entorno adicionales que se van a agregar con la sintaxis:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: argumentos de la línea de comandos que se pasan al programa que se va a depurar.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Referencia de launch.vs.json para proyectos remotos y WSL

En la versión 16.6 de Visual Studio 2019 hemos agregado una nueva configuración de depuración de `type: cppgdb` para simplificar la depuración en sistemas remotos y WSL. Todavía se admiten las configuraciones de depuración antiguas de `type: cppdbg`.

### <a name="configuration-type-cppgdb"></a>Tipo de configuración `cppgdb`

- `name`: nombre descriptivo para identificar la configuración en la lista desplegable **Elemento de inicio**.
- `project`: especifica la ruta de acceso relativa al archivo del proyecto. Normalmente, no es necesario cambiar esta ruta de acceso al depurar un proyecto de CMake.
- `projectTarget`: especifica el destino de CMake que se va a invocar al compilar el proyecto. Visual Studio rellena automáticamente esta propiedad si escribe *launch.vs.json* desde el **Menú Depurar** o **Vista de destinos**. Este valor de destino debe coincidir con el nombre de un destino de depuración existente que aparezca en la lista desplegable **Elemento de inicio**.
- `debuggerConfiguration`: indica el conjunto de valores predeterminados de depuración que se va a usar. En la versión 16.6 de Visual Studio 2019, la única opción válida es `gdb`. Las versiones anteriores también admiten `gdbserver`.
- `args`: argumentos de la línea de comandos que se pasan al programa que se va a depurar.
- `env`: variables de entorno adicionales que se pasan al programa que se va a depurar. Por ejemplo: `{"DISPLAY": "0.0"}`.
- `processID`: id. de proceso de Linux al que se va a adjuntar. Solo se usa cuando se adjunta a un proceso remoto. Para obtener más información, vea [Solución de problemas de asociación a procesos mediante GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Opciones adicionales para la configuración de `gdb`

- `program`: Tiene como valor predeterminado `"${debugInfo.fullTargetPath}"`. Ruta de acceso de Unix a la aplicación que se va a depurar. Solo es necesaria si es diferente del ejecutable de destino en la ubicación de compilación o implementación.
- `remoteMachineName`: Tiene como valor predeterminado `"${debugInfo.remoteMachineName}"`. Nombre del sistema remoto que hospeda el programa que se va a depurar. Solo es necesaria si es diferente del sistema de compilación. Debe tener una entrada existente en el [Administrador de conexiones](../linux/connect-to-your-remote-linux-computer.md). Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas existentes.
- `cwd`: Tiene como valor predeterminado `"${debugInfo.defaultWorkingDirectory}"`. Ruta de acceso de Unix al directorio del sistema remoto donde se ejecuta `program`. El directorio debe existir.
- `gdbpath`: Tiene como valor predeterminado `/usr/bin/gdb`. Ruta de acceso completa de Unix al elemento `gdb` que se usa para depurar. Solo es necesaria si se usa una versión personalizada de `gdb`.
- `preDebugCommand`: comando de Linux para ejecutar inmediatamente antes de invocar `gdb`. `gdb` no se inicia hasta que se completa el comando. Se puede usar la opción para ejecutar un script antes de la ejecución de `gdb`.

#### <a name="deployment-options"></a>Opciones de implementación

Use las opciones siguientes para separar la máquina de compilación (definida en CMakeSettings.json) de la máquina de depuración remota.

- `remoteMachineName`: máquina de depuración remota. Solo es necesaria si es diferente de la máquina de compilación. Debe tener una entrada existente en el [Administrador de conexiones](../linux/connect-to-your-remote-linux-computer.md). Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas existentes.
- `disableDeploy`: Tiene como valor predeterminado `false`. Indica si la separación entre la compilación y la depuración está deshabilitada. Cuando su valor es `false`, esta opción permite que la compilación y la depuración se produzcan en dos máquinas independientes.
- `deployDirectory`: ruta de acceso completa de Unix al directorio en el elemento `remoteMachineName` en el que se copia el archivo ejecutable.
- `deploy`: matriz de configuración de implementación avanzada. Solo se tienen que configurar estos valores si se quiere un control más granular sobre el proceso de implementación. De forma predeterminada, solo los archivos necesarios para depurar el proceso se implementan en la máquina de depuración remota.
  - `sourceMachine`: máquina desde la que se copia el archivo o directorio. Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas almacenadas en el Administrador de conexiones. Al compilar de forma nativa en WSL, se omite esta opción.
  - `targetMachine`: máquina a la que se copia el archivo o directorio. Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas almacenadas en el Administrador de conexiones.
  - `sourcePath`: ubicación del archivo o directorio en `sourceMachine`.
  - `targetPath`: ubicación del archivo o directorio en `targetMachine`.
  - `deploymentType`: descripción del tipo de implementación. Se admiten `LocalRemote` y `RemoteRemote`. `LocalRemote` significa copiar del sistema de archivos local al sistema remoto que especifica `remoteMachineName` en *launch.vs.json*. `RemoteRemote` significa copiar del sistema de compilación remoto especificado en *CMakeSettings.json* al sistema remoto especificado en *launch.vs.json*.
  - `executable`: indica si el archivo implementado es un ejecutable.

### <a name="execute-custom-gdb-commands"></a>Ejecución de comandos de `gdb` personalizados

Visual Studio admite la ejecución de comandos de `gdb` personalizados para interactuar directamente con el depurador subyacente. Para obtener más información, vea [Ejecución de los comandos de lldb `gdb` personalizados](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Habilite el registro

Habilite el registro de MIEngine para ver qué comandos se envían a `gdb`, qué salida `gdb` devuelve y cuánto tiempo tarda cada comando. [Más información](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Tipo de configuración `cppdbg`

Se pueden usar las opciones siguientes al depurar en un sistema remoto o WSL con el tipo de configuración `cppdbg`. En la versión 16.6, o una posterior, de Visual Studio 2019, se recomienda el tipo de configuración `cppgdb`.

- `name`: nombre descriptivo para identificar la configuración en la lista desplegable **Elemento de inicio**.

- `project`: especifica la ruta de acceso relativa al archivo del proyecto. Normalmente, no es necesario cambiar este valor al depurar un proyecto de CMake.

- `projectTarget`: especifica el destino de CMake que se va a invocar al compilar el proyecto. Visual Studio rellena automáticamente esta propiedad si escribe *launch.vs.json* desde el **Menú Depurar** o la **Vista de destinos**. Este valor debe coincidir con el nombre de un destino de depuración existente que aparezca en la lista desplegable **Elemento de inicio**.

- `args`: argumentos de la línea de comandos que se pasan al programa que se va a depurar.

- `processID`: id. de proceso de Linux al que se va a adjuntar. Solo se usa cuando se adjunta a un proceso remoto. Para obtener más información, vea [Solución de problemas de asociación a procesos mediante GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: Tiene como valor predeterminado `"${debugInfo.fullTargetPath}"`. Ruta de acceso de Unix a la aplicación que se va a depurar. Solo es necesaria si es diferente del ejecutable de destino en la ubicación de compilación o implementación.

- `remoteMachineName`:  Tiene como valor predeterminado `"${debugInfo.remoteMachineName}"`. Nombre del sistema remoto que hospeda el programa que se va a depurar. Solo es necesaria si es diferente del sistema de compilación. Debe tener una entrada existente en el [Administrador de conexiones](../linux/connect-to-your-remote-linux-computer.md). Presione **Ctrl+Espacio** para ver una lista de todas las conexiones remotas existentes.

- `cwd`: Tiene como valor predeterminado `"${debugInfo.defaultWorkingDirectory}"`. Ruta de acceso de Unix al directorio del sistema remoto donde se ejecuta `program`. El directorio debe existir.

- `environment`: variables de entorno adicionales que se pasan al programa que se va a depurar. Por ejemplo,

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

- `pipeArgs`: matriz de argumentos de la línea de comandos que se pasa al programa de canalización para configurar la conexión. El programa de canalización se usa para retransmitir la entrada/salida estándar entre Visual Studio y `gdb`. **No es necesario personalizar** la mayor parte de esta matriz al depurar proyectos de CMake. La excepción es `${debuggerCommand}`, que inicia `gdb` en el sistema remoto. Se puede modificar a lo siguiente:

  - Exportar el valor de la variable de entorno DISPLAY en el sistema Linux. En el ejemplo siguiente, este valor es `:1`.

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

  - Ejecutar un script antes de la ejecución de `gdb`. Asegúrese de que los permisos de ejecución están establecidos en el script.

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

- `stopOnEntry`: valor booleano que especifica si se debe interrumpir en cuanto se inicie el proceso. El valor predeterminado es false.

- `visualizerFile`: [archivo .natvis](/visualstudio/debugger/create-custom-views-of-native-objects) que se va a usar al depurar este proceso. Esta opción no es compatible con la impresión con sangría `gdb`. Establezca también `showDisplayString` al establecer esta propiedad.

- `showDisplayString`: valor booleano que habilita la cadena para mostrar cuando se especifica un elemento `visualizerFile`. Establecer esta opción en `true` puede ralentizar el rendimiento durante la depuración.

- `setupCommands`: uno o más comandos de `gdb` que se van a ejecutar para configurar el depurador subyacente.

- `miDebuggerPath`: ruta de acceso completa a `gdb`. Cuando no se especifica, Visual Studio busca en primer lugar PATH para el depurador.

- Por último, el tipo de configuración `cppdbg` también puede usar todas las opciones de implementación definidas para el tipo de configuración `cppgdb`.

### <a name="debug-using-gdbserver"></a>Depuración mediante `gdbserver`

La configuración de `cppdbg` se puede configurar para depurar con `gdbserver`. Puede encontrar más detalles y una configuración de inicio de ejemplo en la entrada del Blog del equipo de Microsoft C++ [Depuración de proyectos de CMake en Linux con `gdbserver`](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Vea también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)\
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)\
[Conexión al equipo remoto Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)\
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)\
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
