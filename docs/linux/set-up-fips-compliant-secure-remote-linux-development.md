---
title: Configuración del desarrollo de Linux remoto seguro compatible con FIPS
description: Cómo configurar una conexión criptográfica compatible con FIPS entre Visual Studio y una máquina Linux de desarrollo remoto.
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "76520466"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>Configuración del desarrollo de Linux remoto seguro compatible con FIPS

::: moniker range="<=vs-2017"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores. El desarrollo remoto seguro de Linux compatible con FIPS está disponible en Visual Studio 2019, versión 16.5 y posteriores.

::: moniker-end

::: moniker range="vs-2019"

La publicación del Estándar federal de procesamiento de información (FIPS) 140-2 es un estándar del gobierno de EE. UU. para los módulos criptográficos. NIST valida las implementaciones del estándar. Windows ofrece [soporte técnico validado para los módulos criptográficos compatibles con FIPS](/windows/security/threat-protection/fips-140-validation). En Visual Studio 2019, versión 16.5 y posteriores, puede usar una conexión criptográfica segura compatible con FIPS para su sistema Linux de desarrollo remoto.

Aquí se muestra cómo configurar una conexión segura compatible con FIPS entre Visual Studio y el sistema Linux remoto. Esta guía es aplicable al compilar proyectos de CMake o MSBuild de Linux en Visual Studio. Este artículo es la versión compatible con FIPS de las instrucciones de conexión en [Conexión al equipo remoto Linux](connect-to-your-remote-linux-computer.md).

## <a name="prepare-a-fips-compliant-connection"></a>Preparación de una conexión compatible con FIPS

Se requiere alguna preparación para usar una conexión SSH criptográficamente segura y compatible con FIPS entre Visual Studio y el sistema Linux remoto. Para el cumplimiento con FIPS-140-2, Visual Studio solo admite claves RSA.

En los ejemplos de este artículo se usa Ubuntu 18.04 LTS con el servidor OpenSSH, versión7.6. No obstante, las instrucciones deben ser iguales para cualquier distribución que use una versión bastante reciente de OpenSSH.

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>Para configurar el servidor SSH en el sistema remoto

1. En el sistema Linux, instale e inicie el servidor OpenSSH:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. Si desea que el servidor SSH se inicie automáticamente al arrancar el sistema, habilítelo mediante systemctl:

   ```bash
   sudo systemctl enable ssh
   ```

1. Abra */etc/ssh/sshd_config* como raíz. Edite las líneas siguientes (o agréguelas si no existen):

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa e el único algoritmo de claves de host compatible con FIPS que VS admite. Los algoritmos aes\*-ctr también son compatibles con FIPS, pero la implementación en Visual Studio no está aprobada. Los algoritmos de intercambio de claves de\* ECDH son conformes a FIPS, pero Visual Studio no los admite.

   No está limitado a estas opciones. Puede configurar SSH para usar cifrados adicionales, algoritmos de claves de host, etc. Algunas otras opciones de seguridad importantes que se pueden considerar son `PermitRootLogin`, `PasswordAuthentication` y `PermitEmptyPasswords`. Para obtener más información, consulte la página man de sshd_config o el artículo sobre la [configuración del servidor SSH](https://www.ssh.com/ssh/sshd_config).

1. Después de guardar y cerrar sshd_config, reinicie el servidor SSH para aplicar la nueva configuración:

   ```bash
   sudo service ssh restart
   ```

A continuación, creará un par de claves RSA en el equipo Windows. A continuación, copiará la clave pública en el sistema Linux remoto para que la use SSH.

### <a name="to-create-and-use-an-rsa-key-file"></a>Para crear y usar un archivo de clave RSA

1. En la máquina Windows, genere un par de claves RSA pública y privada mediante este comando:

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   Este comando creará una clave pública y una clave privada. De forma predeterminada, las claves se guardan en *%USERPROFILE%\\.ssh\\id_rsa* y *%USERPROFILE%\\.ssh\\id_rsa.pub*. (En PowerShell, use `$env:USERPROFILE` en lugar de la macro cmd `%USERPROFILE%`). Si cambia el nombre de la clave, utilice el nombre cambiado en los pasos siguientes.  Se recomienda usar una frase de contraseña para aumentar la seguridad.

1. En Windows, copie la clave pública en la máquina Linux:

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. En el sistema Linux, agregue la clave a la lista de claves autorizadas y asegúrese de que el archivo tiene los permisos correctos:

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. Ahora, puede realizar una prueba para ver si la nueva clave funciona en SSH. Úsela para iniciar sesión desde Windows:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

Ha configurado correctamente SSH, creado e implementado claves de cifrado y probado la conexión. Ya está preparado para configurar la conexión de Visual Studio.

## <a name="connect-to-the-remote-system-in-visual-studio"></a>Conexión al sistema remoto en Visual Studio

1. En Visual Studio, elija **Herramientas > Opciones** en la barra de menús para abrir el cuadro de diálogo **Opciones**. A continuación, seleccione **Multiplataforma > Administrador de conexiones** para abrir el cuadro de diálogo Administrador de conexiones.

   Si no ha configurado anteriormente una conexión en Visual Studio, al crear el proyecto por primera vez, Visual Studio abre automáticamente el cuadro de diálogo Administrador de conexiones.

1. En el cuadro de diálogo Administrador de conexiones, elija el botón **Agregar** para agregar una nueva conexión.

   ![Administrador de conexiones](media/settings_connectionmanager.png)

   Se muestra la ventana **Conectar con el sistema remoto**.

   ![Conectar con el sistema remoto](media/connect.png)

1. En el cuadro de diálogo **Conectar con el sistema remoto**, escriba los detalles de conexión de la máquina remota.

   | Entrada | Descripción
   | ----- | ---
   | **Nombre de host**           | Nombre o dirección IP del dispositivo de destino
   | **Puerto**                | Puerto en el que se ejecuta el servicio SSH, normalmente 22
   | **Nombre de usuario**           | Usuario como el que se autentica
   | **Tipo de autenticación** | Elección de la clave privada para una conexión compatible con FIPS
   | **Archivo de clave privada**    | Archivo de clave privada creado para la conexión ssh
   | **Frase de contraseña**          | Frase de contraseña usada con la clave privada seleccionada anteriormente

   Cambie el tipo de autenticación a **Clave privada**. Escriba la ruta de acceso a la clave privada en el campo **Archivo de clave privada**. Puede usar el botón **Examinar** para ir al archivo de clave privada en su lugar. A continuación, escriba la frase de contraseña usada para cifrar el archivo de clave privada en el campo **Frase de contraseña**.

1. Seleccione el botón **Conectar** para intentar la conexión con el equipo remoto.

   Si la conexión se realiza correctamente, Visual Studio configura IntelliSense para usar los encabezados remotos. Para más información, consulte [IntelliSense para los encabezados en sistemas remotos](configure-a-linux-project.md#remote_intellisense).

   Si se produce un error en la conexión, se marcan en rojo los cuadros de entrada que deben cambiarse.

   ![Error del Administrador de conexiones](media/settings_connectionmanagererror.png)

   Para obtener más información sobre la solución de problemas de conexión, consulte [Conexión al equipo remoto Linux](connect-to-your-remote-linux-computer.md).

## <a name="command-line-utility-for-the-connection-manager"></a>Utilidad de línea de comandos para el Administrador de conexiones  

**Visual Studio 2019, versión 16.5 o posterior**: ConnectionManager.exe es una utilidad de línea de comandos para administrar conexiones de desarrollo remotas fuera de Visual Studio. Resulta útil para tareas como el aprovisionamiento de una nueva máquina de desarrollo. O bien, puede usarla para configurar Visual Studio para la integración continua. Para obtener ejemplos y una referencia completa al comando ConnectionManager, consulte [Referencia de ConnectionManager](connectionmanager-reference.md).  

## <a name="optional-enable-or-disable-fips-mode"></a>Opcional: Habilitar o deshabilitar el modo FIPS

Es posible habilitar el modo FIPS globalmente en Windows.

1. Para habilitar el modo FIPS, presione **Windows+R** para abrir el cuadro de diálogo Ejecutar y, a continuación, ejecute gpedit.msc.

1. Expanda **Directiva de equipo local > Configuración del equipo > Configuración de Windows > Configuración de seguridad > Directivas locales** y seleccione **Opciones de seguridad**.

1. En **Directiva**, seleccione **Criptografía de sistema: usar algoritmos que cumplan FIPS para cifrado, firma y operaciones hash** y, a continuación, presione **Entrar** para abrir el cuadro de diálogo correspondiente.

1. En la pestaña **Configuración de seguridad local**, seleccione **Habilitado** o **Deshabilitado** y, a continuación, elija **Aceptar** para guardar los cambios.

> [!WARNING]
> Al habilitar el modo FIPS, es posible que algunas aplicaciones se interrumpan o se comporten de forma inesperada. Para obtener más información, consulte la entrada de blog [Why We’re Not Recommending "FIPS mode" Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037) (Por qué ya no se recomienda el "modo FIPS").

## <a name="additional-resources"></a>Recursos adicionales

[Documentación de Microsoft sobre la validación de FIPS 140](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2: Security Requirements for Cryptographic Modules](https://csrc.nist.gov/publications/detail/fips/140/2/final) (Requisitos de seguridad para los módulos criptográficos), de NIST

[Cryptographic Algorithm Validation Program: Validation Notes](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes) (Programa de validación de algoritmos criptográficos: notas de validación), de NIST

Entrada de blog de Microsoft [Why We’re Not Recommending "FIPS mode" Anymore](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037) (Por qué ya no se recomienda el "modo FIPS")

[SSH Server Configuration](https://www.ssh.com/ssh/sshd_config) (Configuración del servidor SSH)

## <a name="see-also"></a>Vea también

[Configuración de un proyecto de Linux](configure-a-linux-project.md)\
[Configuración de un proyecto de CMake en Linux](cmake-linux-project.md)\
[Conexión al equipo remoto Linux](connect-to-your-remote-linux-computer.md)\
[Implementación, ejecución y depuración del proyecto de Linux](deploy-run-and-debug-your-linux-project.md)\
[Configuración de sesiones de depuración de CMake](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
