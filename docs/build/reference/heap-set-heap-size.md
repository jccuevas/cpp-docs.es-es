---
title: /HEAP (Establecer el tamaño del montón)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 500e1eca9385697829edca46e5e703a5238684a7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422379"
---
# <a name="heap-set-heap-size"></a>/HEAP (Establecer el tamaño del montón)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Comentarios

La opción /HEAP establece el tamaño del montón en bytes. Esta opción es sólo para su uso al crear un archivo .exe.

El *reservar* argumento especifica la asignación del montón total de memoria virtual. El tamaño del montón predeterminado es 1 MB. El vinculador se redondea el valor especificado a los 4 bytes más cercanos.

El elemento opcional `commit` argumento especifica la cantidad de memoria física para asignar a la vez. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Una mayor `commit` valor ahorrará tiempo cuando la aplicación necesite más espacio del montón, pero aumentarán los requisitos de memoria y, posiblemente, el tiempo de inicio.

Especifique el *reservar* y `commit` valores en notación de lenguaje de C o decimal.

Esta funcionalidad también está disponible a través de un archivo de definición de módulo con [HEAPSIZE](../../build/reference/heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **sistema** página de propiedades.

1. Modificar el **confirmar tamaño del montón** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
