---
title: C++Depurar páginas de propiedades
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: 5f7a7bc0e2c696365daa38696fde6f1a480644b4
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927737"
---
# <a name="c-debugging-property-pages"></a>C++Depurar páginas de propiedades

Estas páginas de propiedades se encuentran**en propiedades de** > **configuración** > del **proyecto** > **depuración**. Elija el tipo de depurador en el control desplegable. Para obtener más información sobre la C++ depuración [de código, vea Tutorial: Aprenda a depurar C++ código mediante](/visualstudio/debugger/getting-started-with-the-debugger-cpp) Visual Studio y [depurar código nativo](/visualstudio/debugger/debugging-native-code).

## <a name="local-windows-debugger-property-page"></a>Página de propiedades del depurador local de Windows

### <a name="command"></a>Get-Help

Comando de depuración para ejecutar.

### <a name="command-arguments"></a>Argumentos de comando

Argumentos de la línea de comandos que se van a pasar a la aplicación.

### <a name="working-directory"></a>Directorio de trabajo

El directorio de trabajo de la aplicación. De forma predeterminada, el directorio que contiene el archivo de proyecto.

### <a name="attach"></a>Attach

Especifica si el depurador debe intentar asociarse a un proceso existente cuando se inicia la depuración.

### <a name="debugger-type"></a>Tipo de depurador

Especifica el tipo de depurador que se va a usar. Cuando se establece en automático, el tipo de depurador se seleccionará en función del contenido del archivo exe.

**Posibilidad**

- **Solo nativo** : solo nativo
- Solo **administrado** : solo administrado
- Mezclado mixto
- **Auto-auto** automática
- **Script-script**
- **Solo GPU (C++ amp)** -GPU (C++ amp)

### <a name="environment"></a>Entorno

Especifica el entorno para el programa que se va a depurar o las variables que se van a combinar con el entorno existente.

### <a name="debugging-accelerator-type"></a>Tipo de acelerador de depuración

Tipo de acelerador de depuración que se va a usar para depurar el código de GPU. (Disponible cuando el depurador de GPU está activo).

### <a name="gpu-default-breakpoint-behavior"></a>Comportamiento de punto de interrupción predeterminado de GPU

Establece la frecuencia con la que se interrumpe el depurador de GPU.

**Posibilidad**

- **Interrumpir una vez por** deformación: interrumpir una vez por alabeo
- **Interrumpir para cada subproceso (como el comportamiento de la CPU)** -interrumpir para cada subproceso (como el comportamiento de la CPU)

### <a name="merge-environment"></a>Combinar entorno

Combinar variables de entorno especificadas con el entorno existente.

### <a name="sql-debugging"></a>Depuración de SQL

Adjunte el depurador de SQL.

### <a name="amp-default-accelerator"></a>Acelerador predeterminado de AMP

Invalide C++ la selección del acelerador predeterminado del amp. La propiedad no se aplica al depurar código administrado.

## <a name="remote-windows-debugger-property-page"></a>Página de propiedades del Depurador remoto de Windows

Para obtener más información sobre la depuración remota, vea [depuración remota de un proyecto de Visual C++ en Visual Studio](/visualstudio/debugger/remote-debugging-cpp).

### <a name="remote-command"></a>Comando remoto

Comando de depuración para ejecutar.

### <a name="remote-command-arguments"></a>Argumentos de comando remoto

Argumentos de la línea de comandos que se van a pasar a la aplicación.

### <a name="working-directory"></a>Directorio de trabajo

El directorio de trabajo de la aplicación. De forma predeterminada, el directorio que contiene el archivo de proyecto.

### <a name="remote-server-name"></a>Nombre de servidor remoto

Especifica un nombre de servidor remoto.

### <a name="connection"></a>Conexión

Especifica el tipo de conexión.

**Posibilidad**

- **Remoto con autenticación de Windows** : remoto con [autenticación de Windows](/windows-server/security/windows-authentication/windows-authentication-overview).
- **Remoto sin autenticación** : remoto sin autenticación.

### <a name="debugger-type"></a>Tipo de depurador

Especifica el tipo de depurador que se va a usar. Cuando se establece en automático, el tipo de depurador se seleccionará en función del contenido del archivo exe.

**Posibilidad**

- **Solo nativo** : solo nativo
- Solo **administrado** : solo administrado
- Mezclado mixto
- **Auto-auto** automática
- **Script-script**
- **Solo GPU (C++ amp)** -GPU (C++ amp)

### <a name="environment"></a>Entorno

Especifica el entorno para el programa que se va a depurar o las variables que se van a combinar con el entorno existente.

### <a name="debugging-accelerator-type"></a>Tipo de acelerador de depuración

Tipo de acelerador de depuración que se va a usar para depurar el código de GPU. (Disponible cuando el depurador de GPU está activo).

### <a name="gpu-default-breakpoint-behavior"></a>Comportamiento de punto de interrupción predeterminado de GPU

Establece la frecuencia con la que se interrumpe el depurador de GPU.

**Posibilidad**

- **Interrumpir una vez por** deformación: interrumpir una vez por alabeo
- **Interrumpir para cada subproceso (como el comportamiento de la CPU)** -interrumpir para cada subproceso (como el comportamiento de la CPU)

### <a name="attach"></a>Attach

Especifica si el depurador debe intentar asociarse a un proceso existente cuando se inicia la depuración.

### <a name="sql-debugging"></a>Depuración de SQL

Adjunte el depurador de SQL.

### <a name="deployment-directory"></a>Directorio de implementación

Al depurar en un equipo remoto, si desea que el contenido del resultado del proyecto (excepto los archivos PDB) se copie en el equipo remoto, especifique la ruta de acceso aquí.

### <a name="additional-files-to-deploy"></a>Archivos adicionales para implementar

Al depurar en una máquina remota, los archivos y directorios especificados aquí (además del resultado del proyecto) se copian en el directorio de implementación si se ha especificado uno.

### <a name="deploy-visual-c-debug-runtime-libraries"></a>Implementar las bibliotecas de depuración en tiempo de ejecución de Visual C++

Especifica si se implementan las bibliotecas en tiempo de ejecución de depuración para la plataforma activa (Win32, x64 o ARM).

### <a name="amp-default-accelerator"></a>Acelerador predeterminado de AMP

Invalide C++ la selección del acelerador predeterminado del amp. La propiedad no se aplica al depurar código administrado.

## <a name="web-browser-debugger-property-page"></a>Página de propiedades del depurador del explorador Web

### <a name="http-url"></a>URL HTTP

Especifica la dirección URL del proyecto.

### <a name="debugger-type"></a>Tipo de depurador

Especifica el tipo de depurador que se va a usar. Cuando se establece en automático, el tipo de depurador se seleccionará en función del contenido del archivo exe.

**Posibilidad**

- **Solo nativo** : solo nativo
- Solo **administrado** : solo administrado
- Mezclado mixto
- **Auto-auto** automática
- **Script-script**

## <a name="web-service-debugger-property-page"></a>Página de propiedades del depurador del servicio Web

### <a name="http-url"></a>URL HTTP

Especifica la dirección URL del proyecto.

### <a name="debugger-type"></a>Tipo de depurador

Especifica el tipo de depurador que se va a usar. Cuando se establece en automático, el tipo de depurador se seleccionará en función del contenido del archivo exe.

**Posibilidad**

- **Solo nativo** : solo nativo
- Solo **administrado** : solo administrado
- Mezclado mixto
- **Auto-auto** automática
- **Script-script**

### <a name="sql-debugging"></a>Depuración de SQL

Adjunte el depurador de SQL.