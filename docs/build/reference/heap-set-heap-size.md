---
title: /HEAP (Establecer el tamaño del montón)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: f155ad56ec1a90479b402e38e7ec7f3e3d80e470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439527"
---
# <a name="heap-set-heap-size"></a>/HEAP (Establecer el tamaño del montón)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Observaciones

La opción/HEAP establece el tamaño del montón en bytes. Esta opción solo se usa al compilar un archivo. exe.

El argumento *Reserve* especifica la asignación total del montón en la memoria virtual. El tamaño del montón predeterminado es 1 MB. El enlazador redondea el valor especificado a los 4 bytes más cercanos.

El argumento opcional `commit` especifica la cantidad de memoria física que se va a asignar a la vez. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Un valor `commit` mayor ahorra tiempo cuando la aplicación necesita más espacio en el montón, pero aumenta los requisitos de memoria y, posiblemente, el tiempo de inicio.

Especifique los valores *Reserve* y `commit` en notación decimal o en el lenguaje C.

Esta funcionalidad también está disponible a través de un archivo de definición de módulo con [HEAPSIZE](heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **Enlazador**.

1. Haga clic en la página de propiedades **sistema** .

1. Modifique la propiedad **tamaño de confirmación del montón** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
