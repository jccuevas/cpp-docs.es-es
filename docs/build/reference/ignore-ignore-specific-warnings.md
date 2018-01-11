---
title: "-Omitir (Ignorar advertencias específicas) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /OVERWRITE
dev_langs: C++
helpviewer_keywords: /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d8815438ce56629bd120c30b0d0db9fef96916d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorar advertencias específicas)
```  
/IGNORE:warning[,warning]  
```  
  
## <a name="parameters"></a>Parámetros  
 `warning`  
 El número de advertencia del vinculador que se debe suprimir, en el intervalo de 4000 a 4999.  
  
## <a name="remarks"></a>Comentarios  
 De manera predeterminada, LINK informa de todas las advertencias. Especifique **/omitir:** `warning` para indicarle al vinculador para suprimir un número específico de advertencia. Para ignorar varias advertencias, separe los números de advertencia con comas.  
  
 El vinculador no permite omitir algunas advertencias. Esta tabla enumeran las advertencias que no se han suprimido por **/omitir**:  
  
|Advertencia del vinculador||  
|--------------------|-|  
|LNK4017|no se admite la instrucción `keyword` para la plataforma de destino; se ha omitido|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|opción no reconocida '`option`'; se ha omitido|  
|LNK4062|'`option`'no es compatible con'`architecture`' de la máquina de destino; opción omitida|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|se omite "`option1`" debido a la especificación "`option2`"|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|el punto de entrada '`function`' no es __stdcall con '`number`' bytes de argumentos; es posible que la imagen no se pueda ejecutar|  
|LNK4088|la imagen se está generando debido a la opción /FORCE; es posible que la imagen no se pueda ejecutar|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|ningún argumento especificado con la opción '`option`'; se omite el modificador|  
|LNK4203|error al leer la base de datos '`filename`' del programa; se vinculará el objeto sin tener en cuenta información de depuración|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`' falta información de depuración para hacer referencia al módulo; se vinculará el objeto sin información de depuración|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`' falta información de depuración actual para hacer referencia al módulo; se vinculará el objeto sin información de depuración|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|no se encontró información de tipo precompilado; '`filename`' no vinculado o reemplazado; se vinculará el objeto sin tener en cuenta información de depuración|  
|LNK4207|'`filename`' compiló /Yc /Yu/Z7; no se puede crear PDB; volver a compilar con/Zi, objeto de vinculación como si no hay información de depuración|  
|LNK4208|formato PDB incompatible en '`filename`'; elimine y genere de nuevo; se vinculará el objeto sin tener en cuenta información de depuración|  
|LNK4209|información de depuración dañada; compile de nuevo el módulo; se vinculará el objeto sin tener en cuenta información de depuración|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` ya no se admite; se omite|  
|LNK4228|'`option`' no válido para un archivo DLL; se ha omitido|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|se encontró la directiva /`directive` no válida; se ha omitido|  
  
 En general, las advertencias del vinculador que no se pueden omitir representan errores de compilación, errores de la línea de comandos o errores de configuración que se deben corregir.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el **vinculador** carpeta, seleccione la **línea de comandos** página de propiedades.  
  
3.  Modificar el **opciones adicionales** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.