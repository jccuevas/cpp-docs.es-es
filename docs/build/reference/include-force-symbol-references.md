---
title: /INCLUDE (Forzar referencias de símbolos)
ms.date: 11/04/2016
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
ms.openlocfilehash: 389bd16829c2466b02cb879c8bc8d43c9efa6fb4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421225"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Forzar referencias de símbolos)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>Parámetros

*symbol*<br/>
Especifica un símbolo que debe agregarse a la tabla de símbolos.

## <a name="remarks"></a>Comentarios

La opción /INCLUDE indica al vinculador que agregue un símbolo especificado a la tabla de símbolos.

Para especificar varios símbolos, escriba una coma (,), un punto y coma (;) o un espacio entre los nombres de símbolo. En la línea de comandos, especifique/include:`symbol` una vez para cada símbolo.

El vinculador resuelve `symbol` agregando el objeto que contiene la definición del símbolo en el programa. Esta característica resulta útil para incluir un objeto de biblioteca que de lo contrario no podría vincularse al programa.

Especificación de un símbolo con esta opción reemplaza la eliminación de ese símbolo por [/OPT: ref](../../build/reference/opt-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **entrada** página de propiedades.

1. Modificar el **forzar referencias de símbolos** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
