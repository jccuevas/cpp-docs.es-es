---
title: -TLBOUT (nombre. Archivo TLB) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c44028f834d2b3200b970fdc613d0bf4d4efd29
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702863"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Dar nombre a un archivo .TLB)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>Argumentos

*path*<br/>
Una especificación de ruta de acceso absoluta o relativa para donde se debe crear el archivo. tlb.

*filename*<br/>
Especifica el nombre del archivo .tlb creado por el compilador MIDL. No se supone que ninguna extensión de archivo; especificar *filename*.tlb si desea que una extensión .tlb.

## <a name="remarks"></a>Comentarios

La opción /TLBOUT especifica el nombre y la extensión del archivo .tlb.

El compilador de MIDL es llamado por el vinculador de Visual C++ al vincular los proyectos que tengan el [módulo](../../windows/module-cpp.md) atributo.

Si no se especifica TLBOUT, el archivo .tlb obtendrá su nombre de [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*. Si no se especifica/IDLOUT, se llamará el archivo .tlb vc70.tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **IDL incrustado** página de propiedades.

1. Modificar el **biblioteca de tipos** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[/IGNOREIDL (no procesar atributos en MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)
[/MIDL (especificar las opciones de línea de comandos MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)
[compilar programas con atributos](../../windows/building-an-attributed-program.md)