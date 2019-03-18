---
title: /IMPLIB (Asignar nombre a la biblioteca de importación)
ms.date: 11/04/2016
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
ms.openlocfilehash: dc9a9220d55f7831a00f70ec155cc5b57a695818
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821318"
---
# <a name="implib-name-import-library"></a>/IMPLIB (Asignar nombre a la biblioteca de importación)

> /IMPLIB:*filename*

## <a name="parameters"></a>Parámetros

*filename*<br/>
Un nombre especificado por el usuario para la biblioteca de importación. Reemplaza el nombre predeterminado.

## <a name="remarks"></a>Comentarios

La opción/IMPLIB invalida el nombre predeterminado de la biblioteca de importación que el vínculo se crea cuando compila un programa que contiene exportaciones. El nombre predeterminado se forma a partir el nombre base del archivo de salida principal y la extensión. lib. Un programa contiene exportaciones si se especifican uno o varios de los siguientes:

- El [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) palabra clave en el código fuente

- [EXPORTACIONES](exports.md) instrucción en un archivo .def

- Un [/EXPORT](export-exports-a-function.md) especificación en un comando LINK

LINK omite/IMPLIB cuando no se está creando una biblioteca de importación. Si no se especifica ninguna exportación, el vínculo no crea una biblioteca de importación. Si se usa un archivo de exportación en la compilación, vínculo se supone que ya existe una biblioteca de importación y no crea uno. Para obtener información sobre las bibliotecas de importación y exportación de archivos, consulte [referencia de LIB](lib-reference.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **avanzadas** página de propiedades.

1. Modificar el **biblioteca de importación** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
