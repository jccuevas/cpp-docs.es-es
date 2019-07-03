---
title: Implementación, ejecución y depuración de un proyecto en C++ de Linux en Visual Studio
description: En este artículo se describe cómo compilar, ejecutar y depurar código en el destino remoto desde un proyecto C++ de Linux en Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 70770385bde859d47532b130463a1cc54e32a570
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042767"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Implementar, ejecutar y depurar el proyecto de Linux

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

Una vez que haya creado un proyecto C++ de Linux en Visual Studio y se haya conectado a él mediante el [Administrador de conexiones de Linux](connect-to-your-remote-linux-computer.md), puede ejecutar y depurar el proyecto. Compile, ejecute y depure el código en el destino remoto.

::: moniker range="vs-2019"

**Visual Studio 2019 versión 16.1** Puede tener como destino distintos sistemas Linux para la depuración y compilación. Por ejemplo, puede realizar compilaciones cruzadas en x64 y llevar a cabo implementaciones en un dispositivo ARM cuando se eligen escenarios de IoT como destino. Para obtener más información, consulte [Especificación de distintas máquinas para compilar y depurar](#separate_build_debug) más adelante en este artículo.

::: moniker-end

Hay varias formas de interactuar con el proyecto de Linux y de depurarlo.

- Depure con las características tradicionales de Visual Studio, como son los puntos de interrupción, las ventanas Inspección y mantener el mouse sobre una variable. Con estos métodos, puede depurar como lo haría normalmente para otros tipos de proyecto.

- Vea la salida del equipo de destino en la ventana de la consola de Linux. También puede usar la consola para enviar la entrada al equipo de destino.

## <a name="debug-your-linux-project"></a>Depurar el proyecto de Linux

1. Seleccione el modo de depuración en la página de propiedades **Depuración**.
   
   ::: moniker range="vs-2019"

   GDB se usa para depurar aplicaciones que se ejecutan en Linux. Al depurar en un sistema remoto (no WSL), GDB se puede ejecutar en dos modos diferentes, que pueden seleccionarse desde la opción **Modo de depuración** de la página de propiedades **Depuración** del proyecto:

   ![Opciones de GDB](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB se usa para depurar aplicaciones que se ejecutan en Linux. GDB se puede ejecutar en dos modos diferentes, que pueden seleccionarse desde la opción **Modo de depuración** de la página de propiedades **Depuración** del proyecto:

   ![Opciones de GDB](media/vs2017-debugger-settings.png)

   ::: moniker-end


   - En modo **gdbserver**, GDB se ejecuta localmente, con lo que se conecta a gdbserver, en el sistema remoto.  Tenga en cuenta que este es el único modo que admite la ventana Consola Linux.

   - En el modo **gdb**, el depurador de Visual Studio controla GDB en el sistema remoto. Esta opción es más recomendable si la versión local de GDB no es compatible con la versión instalada en el equipo de destino. |

   > [!NOTE]
   > Si no es posible alcanzar puntos de interrupción en el modo de depuración gdbserver, pruebe el modo gdb. En primer lugar, gdb debe [instalarse](download-install-and-setup-the-linux-development-workload.md) en el destino remoto.

1. Seleccione el destino remoto a través de la barra de herramientas estándar **Depurar** de Visual Studio.

   Cuando el destino remoto está disponible, verá que aparece por nombre o dirección IP.

   ![Destino remoto](media/remote_target.png)

   Si aún no ha establecido conexión con el destino remoto, se le indicará que use el [administrador de conexiones de Linux](connect-to-your-remote-linux-computer.md) para conectarse al destino remoto.

   ![Arquitectura remota](media/architecture.png)

1. Establezca un punto de interrupción; para ello, haga clic en el margen interno izquierdo de una parte del código que sabe que se ejecutará.

   Un punto rojo aparece en la línea de código en la que estableció el punto de interrupción.

1. Presione **F5** (o **Depurar > Iniciar depuración**) para iniciar la depuración.

   Al iniciar la depuración, la aplicación se compila en el destino remoto antes de comenzar. Los posibles errores de compilación aparecerán en la ventana **Lista de errores**.

   Si no hay ningún error, la aplicación se iniciará y el depurador se detendrá en el punto de interrupción.

   ![Llegar a un punto de interrupción](media/hit_breakpoint.png)

   Ahora, puede interactuar con la aplicación en su estado actual, ver variables y recorrer el código mediante teclas de comando como **F10** o **F11**.

1. Si quiere usar la consola de Linux para interactuar con la aplicación, seleccione **Depurar > Consola de Linux**.

   ![Menú Consola Linux](media/consolemenu.png)

   Esta consola muestra cualquier salida de consola del equipo de destino y acepta entradas y las envía al equipo de destino.

   ![Ventana Consola Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Configuración de otras opciones de depuración (proyectos basados en MSBuild)

- Se pueden pasar argumentos de línea de comandos al ejecutable mediante el elemento **Argumentos de programa** de la página de propiedades **Depuración** del proyecto.

   ![Argumentos de programa](media/settings_programarguments.png)

- Se pueden pasar opciones concretas del depurador a GDB mediante la entrada **Comandos adicionales del depurador**.  Por ejemplo, es posible que quiera pasar por alto las señales SIGILL (instrucciones no válidas).  Podría usar el comando **handle** para lograr esto agregando lo siguiente a la entrada **Comandos adicionales del depurador** como se muestra arriba:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Configuración de otras opciones de depuración (proyectos de CMake)

Puede especificar argumentos de línea de comandos adicionales para un proyecto de CMake en el archivo launch.vs.json. Para obtener más información, consulte el artículo sobre [depuración de proyectos CMake](cmake-linux-project.md#debug_cmake_project).

## <a name="debug-with-attach-to-process"></a>Depurar con la opción Asociar al proceso

La página de propiedades [Depuración](prop-pages/debugging-linux.md) de los proyectos de Visual Studio y la configuración **Launch.vs.json** de los proyectos de CMake tienen ambas una opción que permite establecer una asociación con un proceso en ejecución. Si necesita más control del que se proporciona en esta opción, puede colocar un archivo denominado `Microsoft.MIEngine.Options.xml` en la raíz de la solución o del área de trabajo. A continuación se incluye un ejemplo sencillo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

**AttachOptionsForConnection** tiene la mayoría de los atributos que probablemente necesite. En el ejemplo anterior se muestra cómo especificar una ubicación para buscar más bibliotecas .so. El elemento secundario **ServerOptions** permite asociar al proceso remoto con gdbserver en su lugar. Para ello, deberá especificar un cliente de gdb local (arriba se muestra el que venía incluido en Visual Studio 2017) y una copia local del archivo binario con símbolos. El elemento **SetupCommands** permite pasar comandos directamente a gdb. Puede encontrar todas las opciones disponibles en el [esquema LaunchOptions.xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) en GitHub.

::: moniker range="vs-2019"

## <a name="separate_build_debug"></a> Especificación de distintas máquinas para compilar y depurar

En Visual Studio 2019, versión 16.1, puede separar la máquina de compilación remota de la máquina de depuración remota para proyectos de Linux basados en MSBuild y CMake cuyo destino sea una máquina Linux remota. Por ejemplo, ahora puede realizar compilaciones cruzadas en x64 y llevar a cabo implementaciones en un dispositivo ARM cuando se destinen a escenarios de IoT.

### <a name="msbuild-based-projects"></a>Proyectos basados en MSBuild

De forma predeterminada, la máquina de depuración remota es la misma que la máquina de compilación remota (**Propiedades de configuración** > **General** > **Equipo de compilación remoto**). Para especificar una nueva máquina de depuración remota, haga clic con el botón derecho en el proyecto, en el **Explorador de soluciones** y vaya a **Propiedades de configuración** > **Depuración** > **Equipo de depuración remoto**.  

![Máquina de depuración remota Linux](media/linux-remote-debug-machine.png)

El menú desplegable **Equipo de depuración remoto** se rellena con todas las conexiones remotas establecidas. Para agregar una nueva conexión remota, vaya a **Herramientas** > **Opciones** > **Multiplataforma**  >  **Administrador de conexiones** o busque "Administrador de conexiones" en **Inicio rápido**. También puede especificar un nuevo directorio de implementación remota en las páginas de propiedades del proyecto (**Propiedades de configuración** > **General** > **Directorio de implementación remota**).

De forma predeterminada, solo los archivos necesarios para depurar el proceso se implementarán en la máquina de depuración remota. Puede usar el **Explorador de soluciones** para configurar qué archivos de origen se implementarán en la máquina de depuración remota. Al hacer clic en un archivo de origen, verá una vista previa de las propiedades directamente debajo del Explorador de soluciones.

![Archivos implementables de Linux](media/linux-deployable-content.png)

La propiedad **Content** especifica si el archivo se implementará en la máquina de depuración remota. Puede deshabilitar por completo la implementación accediendo a **Páginas de propiedades** > **Configuration Manager** y desactivando **Implementar** en la configuración deseada.

En algunos casos, es posible que necesite más control sobre la implementación del proyecto. Por ejemplo, algunos archivos que desea implementar podrían estar fuera de la solución o querrá personalizar el directorio de implementación remoto por archivo o directorio. En estos casos, anexe los bloques de código siguientes al archivo .vcxproj y reemplace "example.cpp" con los nombres de archivo real:

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>Proyectos de CMake

Para los proyectos de CMake que tienen como destino una máquina remota Linux, puede especificar una nueva máquina de depuración remota en launch.vs.json. De forma predeterminada, el valor de "remoteMachineName" está sincronizado con la propiedad "remoteMachineName" en CMakeSettings.json, que corresponde a la máquina de compilación remota. Estas propiedades ya no tienen que coincidir y el valor de "remoteMachineName" en launch.vs.json determinará qué máquina remota se usa para implementar y depurar.

![Máquina de depuración remota CMake](media/cmake-remote-debug-machine.png)

IntelliSense le sugerirá una lista de todas las conexiones remotas establecidas. Puede agregar una nueva conexión remota accediendo a **Herramientas** > **Opciones** > **Multiplataforma**  >  **Administrador de conexiones** o busque "Administrador de conexiones" en **Inicio rápido**.

Si desea un control completo sobre la implementación, puede anexar los siguientes bloques de código en el archivo launch.vs.json. Reemplace los valores del marcador de posición con los reales:

```json

"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]

```
::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

- Para depurar dispositivos ARM en Linux, consulte la entrada de blog [Debugging an embedded ARM device in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/) (Depuración de un dispositivo ARM insertado en Visual Studio).

## <a name="see-also"></a>Vea también

[Propiedades de depuración de C++ (C++ para Linux)](prop-pages/debugging-linux.md)
