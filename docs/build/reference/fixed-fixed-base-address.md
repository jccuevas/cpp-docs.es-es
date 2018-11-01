---
title: /FIXED (Dirección base fija)
ms.date: 11/04/2016
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
ms.openlocfilehash: 12ba2d977ecca4805aa01ade1a6ea8239e07716e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523037"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Dirección base fija)

```
/FIXED[:NO]
```

## <a name="remarks"></a>Comentarios

Indica al sistema operativo que solo debe cargar el programa en su dirección base preferida. Si dicha dirección base no está disponible, el sistema operativo no cargará el archivo. Para obtener más información, consulte [/BASE (dirección base)](../../build/reference/base-base-address.md).

/FIXED:NO es el valor predeterminado para un archivo DLL, mientras que /FIXED se utiliza para proyectos de cualquier otro tipo.

Si se especifica /FIXED, LINK no generará una sección de cambio de ubicación en el programa. En tiempo de ejecución, si el sistema operativo no logra cargar el programa en la dirección especificada, emitirá un mensaje de error y no lo cargará.

Si se especifica /FIXED:NO, se generará una sección de cambio de ubicación en el programa.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Escriba el nombre de opción y la configuración el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)