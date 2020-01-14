---
title: Configuración de sesiones de depuración de CMake en Visual Studio
description: Describe cómo usar Visual Studio para configurar las opciones del depurador de CMake
ms.date: 01/13/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: ff1de8241c2489e675f82f469f1cf697a72f5034
ms.sourcegitcommit: 275b71219d2a8bd5d78f87e21dd909e9968c2f44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2020
ms.locfileid: "75946807"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurar sesiones de depuración de CMake

::: moniker range="vs-2015"

La compatibilidad con CMake nativa está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

Todos los destinos de CMake ejecutables se muestran en la lista desplegable **Elemento de inicio** en la barra de herramientas **General**. Para empezar una sesión de depuración, seleccione una e inicie el depurador.

![Desplegable de elemento de inicio de CMake](media/cmake-startup-item-dropdown.png "Desplegable de elemento de inicio de CMake")

También puede iniciar una sesión de depuración desde Explorador de soluciones. En primer lugar, cambie a la **vista de destinos de CMake** en la ventana **Explorador de soluciones** .

![Botón de vista de destinos de CMake](media/cmake-targets-view.png  "Elemento de menú de vista de destinos de CMake")

A continuación, haga clic con el botón derecho en cualquier archivo ejecutable y seleccione **depurar** o **depurar e iniciar configuración**. **Debug** inicia automáticamente la depuración del destino seleccionado, en función de la configuración activa. La **configuración de depuración e inicio** abre el archivo *Launch. vs. JSON* y agrega una nueva configuración de depuración para el destino seleccionado.

## <a name="customize-debugger-settings"></a>Personalización de la configuración del depurador

Puede personalizar la configuración del depurador para cualquier destino de CMake ejecutable en el proyecto en un archivo denominado *Launch. vs. JSON*. Hay tres puntos de entrada a este archivo:

- Seleccione **Depurar > la configuración de depuración e inicio de $ {activeDebugTarget}** en el menú principal para editar la configuración de depuración específica de su destino de depuración activo. Si no tiene un destino activo seleccionado, esta opción estará atenuada.

- Vaya a la **vista destinos** en explorador de soluciones. A continuación, haga clic con el botón derecho en un destino de depuración y seleccione **depurar e iniciar configuración** para editar la configuración de depuración específica del destino seleccionado.

- Haga clic con el botón secundario en un archivo CMakeLists. txt raíz y seleccione **depurar e iniciar configuración** para abrir el cuadro de diálogo **seleccionar un depurador** . El cuadro de diálogo le permite agregar cualquier configuración de depuración, pero debe especificar manualmente el destino CMake que se va a invocar a través de la propiedad `projectTarget`.

Para hacer referencia a cualquier clave en un archivo *CMakeSettings. JSON* , colóquelo delante `cmake.` en *Launch. vs. JSON*. En el ejemplo siguiente se muestra un archivo *Launch. vs. JSON* simple que extrae el valor de la clave `remoteCopySources` en el archivo *CMakeSettings. JSON* para la configuración seleccionada actualmente:

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

Al guardar el archivo *Launch. vs. JSON* , Visual Studio crea una entrada para el nuevo nombre en el menú desplegable del **elemento de inicio** . Puede editar el archivo *Launch. vs. JSON* para crear varias configuraciones de depuración, para cualquier número de destinos CMake.

## <a name="launchvsjson-reference"></a>Referencia de Launch. vs. JSON

Hay muchas propiedades *Launch. vs. JSON* para admitir todos los escenarios de depuración. Las siguientes propiedades son comunes a todas las configuraciones de depuración, tanto remotas como locales:

- `projectTarget`: especifica el destino CMake que se va a invocar al compilar el proyecto. Visual Studio rellena automáticamente esta propiedad si escribe *Launch. vs. JSON* en **Debug > la configuración de depuración e inicio de la vista de destinos $ {activeDebugTarget}** .

- `program`: ruta de acceso completa al ejecutable del programa en el sistema remoto. Puede usar la macro `${debugInfo.fullTargetPath}` aquí.

- `args`: argumentos de la línea de comandos que se pasan al programa para depurar.

## <a name="launchvsjson-reference-for-remote-linux-projects"></a>Referencia de Launch. vs. JSON para proyectos remotos de Linux

Las siguientes propiedades son específicas de las **configuraciones de depuración remota**. También puede [enviar comandos directamente a GDB](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands) y [Habilitar el registro de MIEngine](https://github.com/microsoft/MIEngine/wiki/Logging). Estas propiedades permiten ver qué comandos se envían a gdb, qué resultados gdb devuelve y cuánto tiempo toma cada comando.

- `cwd`: directorio de trabajo actual para buscar dependencias y otros archivos en la máquina remota. Se puede usar la macro `${debugInfo.defaultWorkingDirectory}`. El valor predeterminado es la raíz del área de trabajo remota, a menos que se invalide en *archivo CMakeLists. txt*. Esta propiedad solo se utiliza para las configuraciones remotas; `currentDir` se usa para establecer el directorio actual de la aplicación de inicio para un proyecto local.

- `environment`: variables de entorno adicionales que se van a agregar al entorno para el programa con esta sintaxis:

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

- `pipeArgs`: argumentos de la línea de comandos que se pasan al programa de canalización para configurar la conexión. El programa de canalización se usa para retransmitir la entrada/salida estándar entre Visual Studio y gdb. El comando `${debuggerCommand}` inicia gdb en el sistema remoto y se puede modificar para:

  - Exporte el valor de la variable de entorno que se muestra en el sistema Linux. En el ejemplo siguiente, este valor es `:1`.

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

  - Ejecute un script antes de la ejecución de gdb. Asegúrese de que los permisos de ejecución están establecidos en el script.

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

- `stopOnEntry`: un valor booleano que especifica si se debe interrumpir en cuanto se inicie el proceso. El valor predeterminado es false.

- `visualizerFile`: un [archivo. natvis](/visualstudio/debugger/create-custom-views-of-native-objects) que se utilizará al depurar este proceso. Esta opción es incompatible con la impresión con sangría gdb. Establezca también `showDisplayString` cuando establezca esta propiedad.

- `showDisplayString`: un valor booleano que habilita la cadena de presentación cuando se especifica un `visualizerFile`. La configuración de esta opción en `true` puede ralentizar el rendimiento durante la depuración.

- `setupCommands`: uno o más comandos gdb que se van a ejecutar para configurar el depurador subyacente.

- `externalConsole`: un valor booleano que especifica si se inicia una consola para el código que se está depurando.

- `miDebuggerPath`: ruta de acceso completa a GDB. Cuando no se especifica, Visual Studio busca primero la ruta de acceso para el depurador.

::: moniker-end

::: moniker range="vs-2017"

- `remoteMachineName`: el sistema Linux remoto que hospeda gdb y el programa que se va a depurar.

::: moniker-end

::: moniker range="vs-2019"

Las siguientes propiedades se pueden usar para separar el **sistema de compilación remoto** del **sistema de depuración remota**. Para obtener más información, vea [especificar diferentes máquinas para compilar y depurar](../linux/deploy-run-and-debug-your-linux-project.md#cmake-projects).

- `remoteMachineName`: el sistema Linux remoto que hospeda gdb y el programa que se va a depurar. No es necesario que esta entrada coincida con el sistema Linux remoto que se usa para la compilación especificada en *CMakeSettings. JSON*. Presione **CTRL + barra espaciadora** para ver una lista de todas las conexiones remotas almacenadas en el [Administrador de conexiones](../linux/connect-to-your-remote-linux-computer.md).

- `disableDeploy`: indica si la separación de compilación y depuración está deshabilitada. Cuando está habilitada, esta característica permite que la compilación y la depuración se realicen en dos máquinas independientes.

- `deployDirectory`: el directorio del equipo de depuración remota (especificado por `remoteMachineName`) en el que se copiará el archivo ejecutable.

- `deploy`: una matriz de valores de implementación avanzada. Solo tiene que configurar estos valores si desea un control más granular sobre el proceso de implementación. De forma predeterminada, solo los archivos necesarios para depurar el proceso se implementarán en la máquina de depuración remota.

  - `sourceMachine`: la máquina desde la que se copiará el archivo o el directorio. Presione **CTRL + barra espaciadora** para ver una lista de todas las conexiones remotas almacenadas en el administrador de conexiones.

  - `targetMachine`: el equipo en el que se copiará el archivo o el directorio. Presione **CTRL + barra espaciadora** para ver una lista de todas las conexiones remotas almacenadas en el administrador de conexiones.

  - `sourcePath`: la ubicación del archivo o directorio en `sourceMachine`.

  - `targetPath`: la ubicación del archivo o directorio en `targetMachine`.

  - `deploymentType`: Descripción del tipo de implementación. se admiten `LocalRemote` y `RemoteRemote`. `LocalRemote` significa copiar del sistema de archivos local al sistema remoto especificado por `remoteMachineName` en *Launch. vs. JSON*. `RemoteRemote` significa copiar del sistema de compilación remoto especificado en *CMakeSettings. JSON* en el sistema remoto especificado en *Launch. vs. JSON*.

  - `executable`: indica si el archivo implementado es un ejecutable.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="attach-to-a-remote-process"></a>Asociar a un proceso remoto

Puede asociar a un proceso que se ejecuta en el sistema Linux estableciendo `processId` en el identificador de proceso al que adjuntar el depurador. Para obtener más información, consulte [solución de problemas de conexión a procesos mediante gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

::: moniker-end

::: moniker range="vs-2019"

## <a name="debug-on-linux-using-gdbserver"></a>Depuración en Linux con gdbserver

Visual Studio 2019 versión 16,5 Preview 1 o posterior admite la depuración remota de proyectos de CMake con gdbserver. Para obtener más información, consulte [depuración de proyectos de cmake de Linux con gdbserver](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Vea también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)\
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)\
[Conéctese al equipo Linux remoto](../linux/connect-to-your-remote-linux-computer.md)\
[Personalizar la configuración de compilación de CMake](customize-cmake-settings.md)\
[Configurar sesiones de depuración CMake](configure-cmake-debugging-sessions.md)\
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
