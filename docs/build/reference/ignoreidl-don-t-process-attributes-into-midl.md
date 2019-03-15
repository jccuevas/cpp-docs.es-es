---
title: /IGNOREIDL (Don&#39;t procesar atributos en MIDL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: 210778adecd87ffdd5f2702c10106f12bd5a1b79
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820434"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t procesar atributos en MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Comentarios

La opción /IGNOREIDL especifica que cualquier [atributos IDL](../../windows/idl-attributes.md) en origen no se debe procesar código en un archivo. idl.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **IDL incrustado** página de propiedades.

1. Modificar el **Omitir IDL incrustado** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)<br/>
[/IDLOUT (Dar nombre a los archivos de resultados de MIDL)](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (Dar nombre a un archivo .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (Especificar las opciones de la línea de comandos de MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Compilación de programas con atributos](../../windows/building-an-attributed-program.md)
