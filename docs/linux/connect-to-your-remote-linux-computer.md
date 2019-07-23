---
title: Conexión al sistema Linux de destino en Visual Studio
description: En este artículo se describe cómo conectarse a una máquina remota Linux o WSL desde un proyecto de Visual Studio C++.
ms.date: 06/19/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: cd107f096e4395f93775ee80b889cc0efd627166
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313428"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Conexión al sistema Linux de destino en Visual Studio

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

Puede configurar un proyecto de Linux que tenga como destino una máquina remota o el subsistema Windows para Linux (WSL). Para las máquinas remotas y para WSL en Visual Studio 2017, deberá configurar una conexión remota. 

## <a name="connect-to-a-remote-linux-computer"></a>Conexión a un equipo remoto Linux

Al crear un proyecto de Linux C++ en Visual Studio para un sistema Linux (sea una máquina virtual o un equipo físico), el código fuente de Linux se copia en el equipo remoto Linux y, después, se compila según la configuración de Visual Studio.

Para configurar esta conexión remota:

1. Compile el proyecto por primera vez o cree manualmente una nueva entrada al seleccionar **Herramientas > Opciones** y, luego, abrir el nodo **Multiplataforma > Administrador de conexiones** y hacer clic en el botón **Agregar**.

   ![Administrador de conexiones](media/settings_connectionmanager.png)

   En cualquier caso, aparecerá la ventana **Conectar con el sistema remoto**.

   ![Conectar con el sistema remoto](media/connect.png)

1. Especifique la siguiente información:

   | Entrada | DESCRIPCIÓN
   | ----- | ---
   | **Nombre de host**           | Nombre o dirección IP del dispositivo de destino
   | **Puerto**                | Puerto en el que se ejecuta el servicio SSH, normalmente 22
   | **Nombre de usuario**           | Usuario como el que se autentica
   | **Tipo de autenticación** | Se admite contraseña o clave privada
   | **Contraseña**            | Contraseña para el nombre de usuario especificado
   | **Archivo de clave privada**    | Archivo de clave privada creado para la conexión ssh
   | **Frase de contraseña**          | Frase de contraseña usada con la clave privada seleccionada anteriormente

   Puede utilizar una contraseña o un archivo de claves y una frase de contraseña para la autenticación. Para muchos escenarios de desarrollo, la autenticación de contraseña es suficiente. Si prefiere usar un archivo de claves públicas y privadas, puede crear uno nuevo o [usar uno existente](https://security.stackexchange.com/questions/10203/reusing-private-public-keys). Actualmente, se admiten solo claves RSA y DSA. 
   
   Siga estos pasos para crear un archivo de claves privadas RSA:

    1. En la máquina Windows, cree el par de claves ssh con `ssh-keygen -t rsa`. Esto creará una clave pública y una clave privada. De forma predeterminada, las claves se colocan en `C:\Users\%USERNAME%\.ssh` con los nombres `id_rsa.pub` y `id_rsa`.

    1. En Windows, copie la clave pública a la máquina Linux: `scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`.

    1. En el sistema Linux, agregue la clave a la lista de claves autorizadas (y asegúrese de que el archivo tiene los permisos correctos): `cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. Haga clic en el botón **Conectar** para intentar la conexión con el equipo remoto. 

   Si la conexión se realiza correctamente, Visual Studio empezará a configurar IntelliSense para usar los encabezados remotos. Para más información, consulte [IntelliSense para los encabezados en sistemas remotos](configure-a-linux-project.md#remote_intellisense).

   Si se produce un error en la conexión, se marcan en rojo los cuadros de entrada que deben cambiarse.

   ![Error del Administrador de conexiones](media/settings_connectionmanagererror.png)

   Si está utilizando archivos de claves para la autenticación, asegúrese de que el servidor SSH de la máquina de destino se esté ejecutando y esté configurada correctamente.

   ::: moniker-end

   ::: moniker range="vs-2019"

   Vaya a **Herramientas > Opciones > Multiplataforma > Registro** para habilitar el registro y ayudar a solucionar problemas de conexión:

   ![Registro remoto](media/remote-logging-vs2019.png)

   Los registros incluyen las conexiones, todos los comandos enviados a la máquina remota (su texto, código de salida y tiempo de ejecución) y toda la salida de Visual Studio al shell. El registro funciona para cualquier proyecto CMake multiplataforma o proyecto Linux basado en MSBuild en Visual Studio.

   Puede configurar la salida para que vaya a un archivo o al panel **Registro multiplataforma** en la Ventana de salida. Para proyectos Linux basados en MSBuild, los comandos emitidos a la máquina remota por MSBuild no se enrutan a la **Ventana de salida** porque se emiten fuera de proceso. En su lugar, se registran en un archivo con el prefijo "msbuild_".

   ::: moniker-end

## <a name="connect-to-wsl"></a>Conexión a WSL

::: moniker range="vs-2017"

En Visual Studio 2017, se conecta a WSL mediante los mismos pasos que la conexión a una máquina Linux remota, tal como se describió anteriormente en este artículo. Utilice **localhost** para el **nombre de host**.

::: moniker-end

::: moniker range="vs-2019"

La versión 16.1 de Visual Studio 2019 incorpora compatibilidad nativa para usar C++ con el [subsistema de Windows para Linux (WSL)](https://docs.microsoft.com/windows/wsl/about).  Esto quiere decir que ya no es necesario agregar una conexión remota ni configurar SSH para la compilación y depuración en la instalación local de WSL. Encontrará más detalles sobre [cómo instalar WSL](https://docs.microsoft.com/windows/wsl/install-win10) aquí.

Para configurar la instalación de WSL de modo que funcione con Visual Studio, se necesitan las herramientas gcc, gdb, make, rsync y zip. Puede instalarlas en distribuciones que usen apt con este comando: 

```bash
sudo apt install g++ gdb make rsync zip
```

Para configurar el proyecto para WSL, consulte [Configuración de un proyecto Linux](configure-a-linux-project.md) o [Configuración de un proyecto de CMake de Linux](cmake-linux-project.md), en función del tipo de proyecto que tenga. Para seguir las instrucciones paso a paso para crear una aplicación de consola sencilla con WSL, consulte esta entrada introductoria del blog sobre [C++ con Visual Studio 2019 y el subsistema de Windows para Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

::: moniker-end

## <a name="see-also"></a>Otras referencias

[Configuración de un proyecto de Linux](configure-a-linux-project.md)<br />
[Configuración de un proyecto de CMake en Linux](cmake-linux-project.md)<br />
[Implementar, ejecutar y depurar el proyecto de Linux](deploy-run-and-debug-your-linux-project.md)<br />




