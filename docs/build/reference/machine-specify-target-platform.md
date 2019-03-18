---
title: /MACHINE (Especificar la plataforma de destino)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
ms.openlocfilehash: e64aa7b2ca9e50ebdc0760f64a9b25e851b45310
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818133"
---
# <a name="machine-specify-target-platform"></a>/MACHINE (Especificar la plataforma de destino)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>Comentarios

La opción /MACHINE especifica la plataforma de destino para el programa.

Normalmente, no tiene que especificar la opción /MACHINE. LINK infiere el tipo de equipo a partir de los archivos .obj. Sin embargo, en algunas circunstancias, LINK no puede determinar el tipo de equipo y los problemas de un [las herramientas del vinculador LNK1113 error](../../error-messages/tool-errors/linker-tools-error-lnk1113.md). Si se produce un error de este tipo, especifique /MACHINE.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **avanzadas** página de propiedades.

1. Modificar el **máquina de destino** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
