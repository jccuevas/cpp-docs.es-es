---
title: /IGNORE (ignorar advertencias específicas)
ms.date: 11/04/2016
f1_keywords:
- /OVERWRITE
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
ms.openlocfilehash: c1f9374c168e5b21dfd761f8c984f00ceae9f1bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170623"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorar advertencias específicas)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parámetros

*advertencia*<br/>
El número de advertencia del vinculador que se debe suprimir, en el intervalo de 4000 a 4999.

## <a name="remarks"></a>Observaciones

De manera predeterminada, LINK informa de todas las advertencias. Especifique **/Ignore:** `warning` para indicar al vinculador que suprima un número de advertencia específico. Para ignorar varias advertencias, separe los números de advertencia con comas.

El vinculador no permite omitir algunas advertencias. En esta tabla se enumeran las advertencias que no se suprimen mediante **/Ignore**:

|Advertencia del vinculador||
|--------------------|-|
|LNK4017|no se admite la instrucción `keyword` para la plataforma de destino; se ha omitido|
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|opción no reconocida '`option`'; se ha omitido|
|LNK4062|'`option`' no es compatible con el equipo de destino '`architecture`'; opción omitida|
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|se omite "`option1`" debido a la especificación "`option2`"|
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|el punto de entrada '`function`' no es __stdcall con '`number`' bytes de argumentos; es posible que la imagen no se pueda ejecutar|
|LNK4088|la imagen se está generando debido a la opción /FORCE; es posible que la imagen no se pueda ejecutar|
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|ningún argumento especificado con la opción '`option`'; se omite el modificador|
|LNK4203|error al leer la base de datos '`filename`' del programa; se vinculará el objeto sin tener en cuenta información de depuración|
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|falta la información de depuración de '`filename`' para hacer referencia al módulo; vincular objeto como si no hubiera información de depuración|
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|falta la información de depuración actual en '`filename`' para hacer referencia al módulo; vincular objeto como si no hubiera información de depuración|
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|no se encontró información de tipo precompilado; '`filename`' no vinculado o reemplazado; se vinculará el objeto sin tener en cuenta información de depuración|
|LNK4207|'`filename`' compiló/YC/Yu/Z7; no se puede crear PDB; volver a compilar con/Zi; vincular objeto como si no hubiera información de depuración|
|LNK4208|formato PDB incompatible en '`filename`'; elimine y genere de nuevo; se vinculará el objeto sin tener en cuenta información de depuración|
|LNK4209|información de depuración dañada; compile de nuevo el módulo; se vinculará el objeto sin tener en cuenta información de depuración|
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` ya no se admite; se omite|
|LNK4228|'`option`' no es válido para un archivo DLL; tendrán|
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|se encontró la directiva /`directive` no válida; se ha omitido|

En general, las advertencias del vinculador que no se pueden omitir representan errores de compilación, errores de la línea de comandos o errores de configuración que se deben corregir.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. En la carpeta **vinculador** , seleccione la página de propiedades **línea de comandos** .

1. Modifique la propiedad **opciones adicionales** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.
