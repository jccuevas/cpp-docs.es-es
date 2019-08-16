---
title: /TLBOUT (Dar nombre a un archivo .TLB)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 4e04514933a521bbf9d927fa6b47bacb87896353
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317645"
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

Se llama el compilador de MIDL por el vinculador MSVC al vincular los proyectos que tengan el [módulo](../../windows/module-cpp.md) atributo.

Si no se especifica TLBOUT, el archivo .tlb obtendrá su nombre de [/IDLOUT](idlout-name-midl-output-files.md) *filename*. Si no se especifica/IDLOUT, se llamará el archivo .tlb vc70.tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **IDL incrustado** página de propiedades.

1. Modificar el **biblioteca de tipos** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[/IGNOREIDL (No procesar atributos en MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Especificar las opciones de la línea de comandos de MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Compilación de programas con atributos](../../windows/building-an-attributed-program.md)
