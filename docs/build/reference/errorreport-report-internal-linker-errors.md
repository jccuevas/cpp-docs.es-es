---
title: /ERRORREPORT (Informar de los errores del compilador)
ms.date: 12/28/2017
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 97d36e9db342e5873fc76a156b879e03af880dbf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447255"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Informar de los errores del compilador)

> **/ errorreport:**[ **ninguno** | **símbolo del sistema** | **cola** | **enviar** ]

## <a name="arguments"></a>Argumentos

**none**<br/>
No se recopilarán informes sobre errores internos del compilador ni se enviarán a Microsoft.

**prompt**<br/>
Pregunta si desea enviar un informe cuando recibe un error interno del compilador. **símbolo del sistema** es el valor predeterminado cuando se compila una aplicación en el entorno de desarrollo.

**queue**<br/>
Pone en cola el informe de error. Cuando inicie sesión con privilegios de administrador, se muestra una ventana para que se puede notificar los errores desde la última vez que se ha iniciado sesión (no se le indicará que envíe informes de errores más de una vez cada tres días). **cola** es el valor predeterminado cuando se compila una aplicación en un símbolo del sistema.

**send**<br/>
Envía automáticamente informes de errores internos del compilador a Microsoft si el informe está habilitado por la configuración del servicio informe de errores de Windows.

## <a name="remarks"></a>Comentarios

El **/errorreport** opción le permite proporcionar información de error (ICE) internos del compilador directamente a Microsoft.

La opción **/errorreport: Send** envía automáticamente información de errores a Microsoft, si se habilita en la configuración del servicio informe de errores de Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Abra el **propiedades de configuración** > **vinculador** > **avanzadas** página de propiedades.

1. Modificar el **Error Reporting** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Vea también

[/errorReport (Informar de los errores internos del compilador)](../../build/reference/errorreport-report-internal-compiler-errors.md)<br/>
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
