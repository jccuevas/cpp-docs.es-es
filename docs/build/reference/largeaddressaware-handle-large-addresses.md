---
title: /LARGEADDRESSAWARE (Procesar direcciones largas)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 81a560ebf083e2f93d9bb514fc401186291d7f41
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808123"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Procesar direcciones largas)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Comentarios

La opción /LARGEADDRESSAWARE indica al vinculador que la aplicación puede controlar direcciones superiores a 2 gigabytes. En los compiladores de 64 bits, esta opción está habilitada de forma predeterminada. En los compiladores de 32 bits, / LARGEADDRESSAWARE: no está habilitado si /LARGEADDRESSAWARE no se especifica en la línea del vinculador.

Si una aplicación se vinculó con /LARGEADDRESSAWARE, DUMPBIN [/HEADERS](headers.md) mostrará información al respecto.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **sistema** página de propiedades.

1. Modificar el **habilitar direcciones largas** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
