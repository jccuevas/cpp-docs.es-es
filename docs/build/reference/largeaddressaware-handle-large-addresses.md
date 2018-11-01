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
ms.openlocfilehash: 6a83ac89c6ddf14885107193b32d9b7fe7853659
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543060"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Procesar direcciones largas)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Comentarios

La opción /LARGEADDRESSAWARE indica al vinculador que la aplicación puede controlar direcciones superiores a 2 gigabytes. En los compiladores de 64 bits, esta opción está habilitada de forma predeterminada. En los compiladores de 32 bits, / LARGEADDRESSAWARE: no está habilitado si /LARGEADDRESSAWARE no se especifica en la línea del vinculador.

Si una aplicación se vinculó con /LARGEADDRESSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) mostrará información al respecto.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **sistema** página de propiedades.

1. Modificar el **habilitar direcciones largas** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)