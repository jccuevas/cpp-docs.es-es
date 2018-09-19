---
title: -IGNOREIDL (Don&#39;t procesar atributos en MIDL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs:
- C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7014440c3479016c89b774f9a80cc03fc4b5d4c3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708232"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t procesar atributos en MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Comentarios

La opción /IGNOREIDL especifica que cualquier [atributos IDL](../../windows/idl-attributes.md) en origen no se debe procesar código en un archivo. idl.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **IDL incrustado** página de propiedades.

1. Modificar el **Omitir IDL incrustado** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[/IDLOUT (dar nombre a los archivos de salida MIDL)](../../build/reference/idlout-name-midl-output-files.md)
[TLBOUT (nombre. Archivo TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)
[/MIDL (especificar las opciones de línea de comandos MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)
[compilar programas con atributos](../../windows/building-an-attributed-program.md)