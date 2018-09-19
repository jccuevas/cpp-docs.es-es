---
title: -IGNORE (Ignorar advertencias específicas) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /OVERWRITE
dev_langs:
- C++
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aee498951c01c332dffe720dbd6e3b77c8121aa5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705866"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorar advertencias específicas)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parámetros

*warning*<br/>
El número de advertencia del vinculador que se debe suprimir, en el intervalo de 4000 a 4999.

## <a name="remarks"></a>Comentarios

De manera predeterminada, LINK informa de todas las advertencias. Especificar **/omitir:** `warning` para indicarle al vinculador para suprimir un número de advertencia específico. Para ignorar varias advertencias, separe los números de advertencia con comas.

El vinculador no permite omitir algunas advertencias. Esta tabla enumeran las advertencias que no se han suprimido por **/omitir**:

|Advertencia del vinculador||
|--------------------|-|
|LNK4017|no se admite la instrucción `keyword` para la plataforma de destino; se ha omitido|
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|opción no reconocida '`option`'; se ha omitido|
|LNK4062|'`option`'no es compatible con'`architecture`' equipo de destino; opción omitida|
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|se omite "`option1`" debido a la especificación "`option2`"|
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|el punto de entrada '`function`' no es __stdcall con '`number`' bytes de argumentos; es posible que la imagen no se pueda ejecutar|
|LNK4088|la imagen se está generando debido a la opción /FORCE; es posible que la imagen no se pueda ejecutar|
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|ningún argumento especificado con la opción '`option`'; se omite el modificador|
|LNK4203|error al leer la base de datos '`filename`' del programa; se vinculará el objeto sin tener en cuenta información de depuración|
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`' no tiene información de depuración para hacer referencia al módulo; se vinculará el objeto como si no hay información de depuración|
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`' falta información de depuración actual para hacer referencia al módulo; se vinculará el objeto como si no hay información de depuración|
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|no se encontró información de tipo precompilado; '`filename`' no vinculado o reemplazado; se vinculará el objeto sin tener en cuenta información de depuración|
|LNK4207|'`filename`' compilado /Yc /Yu/Z7; no se puede crear PDB; vuelva a compilar con /Zi; se vinculará el objeto como si no hay información de depuración|
|LNK4208|formato PDB incompatible en '`filename`'; elimine y genere de nuevo; se vinculará el objeto sin tener en cuenta información de depuración|
|LNK4209|información de depuración dañada; compile de nuevo el módulo; se vinculará el objeto sin tener en cuenta información de depuración|
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` ya no se admite; se omite|
|LNK4228|'`option`' no válido para un archivo DLL; se ha omitido|
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|se encontró la directiva /`directive` no válida; se ha omitido|

En general, las advertencias del vinculador que no se pueden omitir representan errores de compilación, errores de la línea de comandos o errores de configuración que se deben corregir.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. En el **vinculador** carpeta, seleccione el **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.