---
title: -ERRORREPORT (informar de errores internos del enlazador) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
dev_langs:
- C++
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72e620e5347d422a8de66cba3ea9cfd601bb3f29
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374341"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Informar de los errores del compilador)

> **/errorreport:**[ **ninguno** | **símbolo del sistema** | **cola** | **enviar** ]

## <a name="arguments"></a>Argumentos

**none**  
No se recopilarán informes sobre errores internos del compilador ni se enviarán a Microsoft.

**prompt**  
Pregunta si desea enviar un informe cuando recibe un error interno del compilador. **símbolo del sistema** es el valor predeterminado cuando se compila una aplicación en el entorno de desarrollo.

**queue**  
Pone en cola el informe de error. Cuando inicie sesión con privilegios de administrador, aparece una ventana para que puede notificar los errores desde la última vez que se registraron en (no se le pedirá que envíe informes de errores más de una vez cada tres días). **cola** es el valor predeterminado cuando se compila una aplicación en un símbolo del sistema.

**send**  
Envía automáticamente informes de errores internos del compilador a Microsoft si el informe está habilitado por la configuración del servicio informe de errores de Windows.

## <a name="remarks"></a>Comentarios

El **/ERRORREPORT** opción le permite proporcionar información de sobre los errores internos del compilador directamente a Microsoft.

La opción **/errorreport: Send** envía automáticamente información de errores a Microsoft, si se habilita en la configuración del servicio de informe de errores de Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Abra la **propiedades de configuración** > **vinculador** > **avanzadas** página de propiedades.

1. Modificar el **informe de errores de** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Vea también

[/errorReport (Informar de los errores internos del compilador)](../../build/reference/errorreport-report-internal-compiler-errors.md)  
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
