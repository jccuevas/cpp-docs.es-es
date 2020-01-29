---
title: Conexión al sistema Linux de destino en Visual Studio
description: En este artículo se describe cómo conectarse a una máquina remota Linux o al Subsistema de Windows para Linux desde un proyecto de Visual Studio C++.
ms.date: 01/17/2020
ms.openlocfilehash: d0065b63d7a81d3ae3d68b26184c88aca77f601c
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518223"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Conexión al sistema Linux de destino en Visual Studio

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range="vs-2017"

Puede configurar un proyecto de Linux que tenga como destino una máquina remota o el subsistema Windows para Linux (WSL). Para las máquinas remotas y para WSL, debe configurar una conexión remota en Visual Studio 2017.

::: moniker-end

::: moniker range="vs-2019"

Puede configurar un proyecto de Linux que tenga como destino una máquina remota o el subsistema Windows para Linux (WSL). Para una máquina remota, debe configurar una conexión remota en Visual Studio. Para conectarse a WSL, vaya directamente a la sección [Conexión a WSL](#connect-to-wsl).

::: moniker-end

::: moniker range=">=vs-2017"

Si se usa una conexión remota, Visual Studio crea proyectos de C++ para Linux en la máquina remota. No es importante si se trata de una máquina física, una VM en la nube o WSL.
Para crear el proyecto, Visual Studio copia el código fuente en el equipo Linux remoto. A continuación, el código se compila según la configuración de Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019, versión 16.5 y posteriores, también admite conexiones criptográficas compatibles con el Estándar federal de procesamiento de información (FIPS) 140-2 para sistemas Linux de desarrollo remoto. Para usar una conexión compatible con FIPS, siga los pasos que se describen en [Configuración del desarrollo de Linux remoto seguro compatible con FIPS](set-up-fips-compliant-secure-remote-linux-development.md) en su lugar.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>Configuración del servidor SSH en el sistema remoto

Si SSH todavía no está configurado y en ejecución en el sistema Linux, siga estos pasos para instalarlo. En los ejemplos de este artículo se usa Ubuntu 18.04 LTS con el servidor OpenSSH, versión7.6. No obstante, las instrucciones deben ser iguales para cualquier distribución que use una versión bastante reciente de OpenSSH.

1. En el sistema Linux, instale e inicie el servidor OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Si desea que el servidor SSH se inicie automáticamente al arrancar el sistema, habilítelo mediante systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>Configuración de la conexión remota

1. En Visual Studio, elija **Herramientas > Opciones** en la barra de menús para abrir el cuadro de diálogo **Opciones**. A continuación, seleccione **Multiplataforma > Administrador de conexiones** para abrir el cuadro de diálogo Administrador de conexiones.

   Si no ha configurado anteriormente una conexión en Visual Studio, al crear el proyecto por primera vez, Visual Studio abre automáticamente el cuadro de diálogo Administrador de conexiones.

1. En el cuadro de diálogo Administrador de conexiones, elija el botón **Agregar** para agregar una nueva conexión.

   ![Administrador de conexiones](media/settings_connectionmanager.png)

   En cualquier caso, se muestra la ventana **Conectar con el sistema remoto**.

   ![Conectar con el sistema remoto](media/connect.png)

1. Especifique la siguiente información:

   | Entrada | Descripción
   | ----- | ---
   | **Nombre de host**           | Nombre o dirección IP del dispositivo de destino
   | **Puerto**                | Puerto en el que se ejecuta el servicio SSH, normalmente 22
   | **Nombre de usuario**           | Usuario como el que se autentica
   | **Tipo de autenticación** | Se admite contraseña y clave privada
   | **Contraseña**            | Contraseña para el nombre de usuario especificado
   | **Archivo de clave privada**    | Archivo de clave privada creado para la conexión ssh
   | **Frase de contraseña**          | Frase de contraseña usada con la clave privada seleccionada anteriormente

   Puede utilizar una contraseña o un archivo de claves y una frase de contraseña para la autenticación. Para muchos escenarios de desarrollo, la autenticación de contraseña es suficiente, pero los archivos de clave son más seguros. Si ya tiene un par de claves, puede reutilizarlo. Actualmente, Visual Studio solo admite las claves RSA y DSA para las conexiones remotas.

1. Seleccione el botón **Conectar** para intentar la conexión con el equipo remoto.

   Si la conexión se realiza correctamente, Visual Studio configura IntelliSense para usar los encabezados remotos. Para más información, consulte [IntelliSense para los encabezados en sistemas remotos](configure-a-linux-project.md#remote_intellisense).

   Si se produce un error en la conexión, se marcan en rojo los cuadros de entrada que deben cambiarse.

   ![Error del Administrador de conexiones](media/settings_connectionmanagererror.png)

   Si usa archivos de claves para la autenticación, asegúrese de que el servidor SSH de la máquina de destino se esté ejecutando y esté configurada correctamente.

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>Registro de las conexiones remotas

   Puede habilitar el registro para ayudar a solucionar problemas de conexión. En la barra de menús, seleccione **Herramientas > Opciones**. En el cuadro de diálogo **Opciones**, seleccione **Multiplataforma > Registro**:

   ![Registro remoto](media/remote-logging-vs2019.png)

   Los registros incluyen las conexiones, todos los comandos enviados a la máquina remota (su texto, código de salida y tiempo de ejecución) y toda la salida de Visual Studio al shell. El registro funciona para cualquier proyecto CMake multiplataforma o proyecto Linux basado en MSBuild en Visual Studio.

   Puede configurar la salida para que vaya a un archivo o al panel **Registro multiplataforma** en la Ventana de salida. Para proyectos Linux basados en MSBuild, los comandos de MSBuild emitidos a la máquina remota no se enrutan a la **Ventana de salida** porque se emiten fuera de proceso. En su lugar, se registran en un archivo con el prefijo "msbuild_".

## <a name="command-line-utility-for-the-connection-manager"></a>Utilidad de línea de comandos para el Administrador de conexiones  

**Visual Studio 2019, versión 16.5 o posterior**: ConnectionManager.exe es una utilidad de línea de comandos para administrar conexiones de desarrollo remotas fuera de Visual Studio. Resulta útil para tareas como el aprovisionamiento de una nueva máquina de desarrollo. O bien, puede usarla para configurar Visual Studio para la integración continua. Para obtener ejemplos y una referencia completa al comando ConnectionManager, consulte [Referencia de ConnectionManager](connectionmanager-reference.md).  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>Reenvío de puertos TCP

La compatibilidad con Linux de Visual Studio depende del reenvío de puertos TCP. **Rsync** y **gdbserver** se ven afectados si el reenvío de puertos TCP está deshabilitado en su sistema remoto. Si se ve afectado por esta dependencia, puede votar este [vale de sugerencia](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html) en Developer Community.

Tanto los proyectos de CMake como los de Linux basados en MSBuild usan rsync para [copiar encabezados de su sistema remoto en Windows, a fin de utilizarlos para IntelliSense](configure-a-linux-project.md#remote_intellisense). Si no puede habilitar el reenvío de puertos TCP, deshabilite la descarga automática de los encabezados remotos. Para deshabilitarla, vaya a **Herramientas > Opciones > Multiplataforma > Administrador de conexiones > Administrador de IntelliSense de encabezados remotos**. Si el sistema remoto no tiene habilitado el reenvío de puertos TCP, verá el siguiente error al comenzar la descarga de encabezados remotos para IntelliSense:

![Error de encabezados](media/port-forwarding-headers-error.png)

La compatibilidad con CMake de Visual Studio también usa rsync para copiar archivos de origen en el sistema remoto. So no puede habilitar el reenvío de puertos TCP, puede usar sftp como su método de copia de orígenes en remoto. sftp suele ser más lento que rsync, pero no depende del reenvío de puertos TCP. Puede administrar su método de copia de orígenes en remoto con la propiedad **remoteCopySourcesMethod** en el [Editor de configuración de CMake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Si el reenvío de puertos TCP está deshabilitado en su sistema remoto, verá un error en la ventana de salida de CMake al invocarse rsync por primera vez.

![Error de Rsync](media/port-forwarding-copy-error.png)

gdbserver se puede usar para la depuración en dispositivos incrustados. Si no puede habilitar el reenvío de puertos TCP, tendrá que usar gdb para todos los escenarios de depuración remota. gdb se usa de forma predeterminada al depurar proyectos en un sistema remoto.

## <a name="connect-to-wsl"></a>Conexión a WSL

::: moniker-end

::: moniker range="vs-2017"

En Visual Studio 2017, se usan los mismos pasos para conectarse a WSL que para un equipo Linux remoto. Utilice **localhost** para el **nombre de host**.

::: moniker-end

::: moniker range="vs-2019"

La versión 16.1 de Visual Studio 2019 incorpora compatibilidad nativa para usar C++ con el [subsistema de Windows para Linux (WSL)](/windows/wsl/about). Esto significa que puede compilar y depurar directamente en la instalación local de WSL. Ya no es necesario agregar una conexión remota ni configurar SSH. Encontrará más detalles sobre [cómo instalar WSL](/windows/wsl/install-win10) aquí.

Para configurar la instalación de WSL de modo que funcione con Visual Studio, se necesitan las herramientas gcc o clang, gdb, make, rsync y zip. Puede instalarlos en distribuciones que usan apt mediante este comando, que también instala el compilador g++:

```bash
sudo apt install g++ gdb make rsync zip
```

Para más información, vea [Descargar, instalar y configurar la carga de trabajo de Linux](download-install-and-setup-the-linux-development-workload.md).

Para configurar un proyecto de MSBuild para WSL, consulte [Configuración de un proyecto de Linux](configure-a-linux-project.md). Para configurar un proyecto de CMake para WSL, consulte [Configuración de un proyecto de CMake en Linux](cmake-linux-project.md). Para seguir las instrucciones paso a paso para crear una aplicación de consola sencilla con WSL, consulte esta entrada introductoria del blog sobre [C++ con Visual Studio 2019 y el subsistema de Windows para Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Vea también

[Configuración de un proyecto de Linux](configure-a-linux-project.md)\
[Configuración de un proyecto de CMake en Linux](cmake-linux-project.md)\
[Implementación, ejecución y depuración del proyecto de Linux](deploy-run-and-debug-your-linux-project.md)\
[Configuración de sesiones de depuración de CMake](../build/configure-cmake-debugging-sessions.md)
