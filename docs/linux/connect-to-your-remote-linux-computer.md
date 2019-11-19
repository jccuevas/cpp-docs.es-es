---
title: Conexión al sistema Linux de destino en Visual Studio
description: En este artículo se describe cómo conectarse a una máquina remota Linux o al Subsistema de Windows para Linux desde un proyecto de Visual Studio C++.
ms.date: 11/09/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6f7116ab5dc6c77f88d0787beac32d1c1e0a4716
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966576"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Conexión al sistema Linux de destino en Visual Studio

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

Puede configurar un proyecto de Linux que tenga como destino una máquina remota o el subsistema Windows para Linux (WSL). Para las máquinas remotas y para WSL en Visual Studio 2017, deberá configurar una conexión remota.

## <a name="connect-to-a-remote-linux-computer"></a>Conexión a un equipo remoto Linux

Al crear un proyecto de Linux C++ en Visual Studio para un sistema Linux remoto (sea una máquina virtual o un equipo físico), el código fuente de Linux se copia en el equipo remoto Linux. Después, se compila según la configuración de Visual Studio.

Para configurar esta conexión remota:

1. Compile el proyecto por primera vez. O bien, puede crear una nueva entrada manualmente. Seleccione **Herramientas > Opciones**, abra el nodo **Multiplataforma > Administrador de conexiones** y, después, seleccione el botón **Agregar**.

   ![Administrador de conexiones](media/settings_connectionmanager.png)

   En cualquier caso, se muestra la ventana **Conectar con el sistema remoto**.

   ![Conectar con el sistema remoto](media/connect.png)

1. Especifique la siguiente información:

   | Entrada | DESCRIPCIÓN
   | ----- | ---
   | **Nombre de host**           | Nombre o dirección IP del dispositivo de destino
   | **Puerto**                | Puerto en el que se ejecuta el servicio SSH, normalmente 22
   | **Nombre de usuario**           | Usuario como el que se autentica
   | **Tipo de autenticación** | Se admite contraseña y clave privada
   | **Contraseña**            | Contraseña para el nombre de usuario especificado
   | **Archivo de clave privada**    | Archivo de clave privada creado para la conexión ssh
   | **Frase de contraseña**          | Frase de contraseña usada con la clave privada seleccionada anteriormente

   Puede utilizar una contraseña o un archivo de claves y una frase de contraseña para la autenticación. Para muchos escenarios de desarrollo, la autenticación de contraseña es suficiente. Si prefiere usar un archivo de claves públicas y privadas, puede crear uno nuevo o [usar uno existente](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Actualmente, se admiten solo claves RSA y DSA.

   Siga estos pasos para crear un archivo de claves privadas RSA:

   1. En la máquina Windows, cree el par de claves ssh con `ssh-keygen -t rsa`. Este comando creará una clave pública y una clave privada. De forma predeterminada, coloca las claves en `C:\Users\%USERNAME%\.ssh`, con los nombres `id_rsa.pub` y `id_rsa`.

   1. En Windows, copie la clave pública a la máquina Linux: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

   1. En el sistema Linux, agregue la clave a la lista de claves autorizadas (y asegúrese de que el archivo tiene los permisos correctos): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Seleccione el botón **Conectar** para intentar la conexión con el equipo remoto.

   Si la conexión se realiza correctamente, Visual Studio empezará a configurar IntelliSense para usar los encabezados remotos. Para más información, consulte [IntelliSense para los encabezados en sistemas remotos](configure-a-linux-project.md#remote_intellisense).

   Si se produce un error en la conexión, se marcan en rojo los cuadros de entrada que deben cambiarse.

   ![Error del Administrador de conexiones](media/settings_connectionmanagererror.png)

   Si usa archivos de claves para la autenticación, asegúrese de que el servidor SSH de la máquina de destino se esté ejecutando y esté configurada correctamente.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Vaya a **Herramientas > Opciones > Multiplataforma > Registro** para habilitar el registro y ayudar a solucionar problemas de conexión:

   ![Registro remoto](media/remote-logging-vs2019.png)

   Los registros incluyen las conexiones, todos los comandos enviados a la máquina remota (su texto, código de salida y tiempo de ejecución) y toda la salida de Visual Studio al shell. El registro funciona para cualquier proyecto CMake multiplataforma o proyecto Linux basado en MSBuild en Visual Studio.

   Puede configurar la salida para que vaya a un archivo o al panel **Registro multiplataforma** en la Ventana de salida. Para proyectos Linux basados en MSBuild, los comandos de MSBuild emitidos a la máquina remota no se enrutan a la **Ventana de salida** porque se emiten fuera de proceso. En su lugar, se registran en un archivo con el prefijo "msbuild_".

## <a name="tcp-port-forwarding"></a>Reenvío de puertos TCP

La compatibilidad con Linux de Visual Studio depende del reenvío de puertos TCP. **Rsync** y **gdbserver** se verán afectados si el reenvío de puertos TCP está deshabilitado en su sistema remoto. 

Tanto los proyectos de CMake como los de Linux basados en MSBuild usan rsync para [copiar encabezados de su sistema remoto en Windows, a fin de utilizarlos para IntelliSense](configure-a-linux-project.md#remote_intellisense). Si no puede habilitar el reenvío de puertos TCP, deshabilite la descarga automática de los encabezados remotos. Para deshabilitarla, vaya a **Herramientas > Opciones > Multiplataforma > Administrador de conexiones > Administrador de IntelliSense de encabezados remotos**. Si el sistema remoto no tiene habilitado el reenvío de puertos TCP, verá el siguiente error al comenzar la descarga de encabezados remotos para IntelliSense:

![Error de encabezados](media/port-forwarding-headers-error.png)

La compatibilidad con CMake de Visual Studio también usa rsync para copiar archivos de origen en el sistema remoto. So no puede habilitar el reenvío de puertos TCP, puede usar sftp como su método de copia de orígenes en remoto. sftp suele ser más lento que rsync, pero no depende del reenvío de puertos TCP. Puede administrar su método de copia de orígenes en remoto con la propiedad **remoteCopySourcesMethod** en el [Editor de configuración de CMake](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects). Si el reenvío de puertos TCP está deshabilitado en su sistema remoto, verá un error en la ventana de salida de CMake al invocarse rsync por primera vez.

![Error de Rsync](media/port-forwarding-copy-error.png)

gdbserver se puede usar para la depuración en dispositivos incrustados. Si no puede habilitar el reenvío de puertos TCP, tendrá que usar gdb para todos los escenarios de depuración remota. gdb se usa de forma predeterminada al depurar proyectos en un sistema remoto.

::: moniker-end

## <a name="connect-to-wsl"></a>Conexión a WSL

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

## <a name="see-also"></a>Otras referencias

[Configuración de un proyecto de Linux](configure-a-linux-project.md)\
[Configuración de un proyecto de CMake en Linux](cmake-linux-project.md)\
[Implementación, ejecución y depuración del proyecto de Linux](deploy-run-and-debug-your-linux-project.md)\
[Configuración de sesiones de depuración de CMake](../build/configure-cmake-debugging-sessions.md)
