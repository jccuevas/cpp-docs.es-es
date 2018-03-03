---
title: -ERRORREPORT (informar de errores internos del enlazador) | Documentos de Microsoft
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ddf65ed2a17dae2d86b0dc4582f1d3158328898
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
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

[/errorReport (informar de errores de compilador interno)](../../build/reference/errorreport-report-internal-compiler-errors.md)  
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
