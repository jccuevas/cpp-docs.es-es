---
title: /OUT (Nombre del archivo de resultados)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: be5fe929bdcf52be19955a5bc2d7aa093e194f45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812426"
---
# <a name="out-output-file-name"></a>/OUT (Nombre del archivo de resultados)

```
/OUT:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
Un nombre especificado por el usuario para el archivo de salida. Reemplaza el nombre predeterminado.

## <a name="remarks"></a>Comentarios

La opción /OUT invalida el nombre predeterminado y la ubicación del programa que crea el enlazador.

De forma predeterminada, el vinculador constituye el nombre de archivo con el nombre base del primer archivo .obj especificado y la extensión correspondiente (.exe o .dll).

Esta opción, el nombre de la base predeterminada para una biblioteca .mapfile o importación. Para obtener más información, consulte [generar archivo de asignaciones](map-generate-mapfile.md) (/Map) y [/IMPLIB](implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **General** página de propiedades.

1. Modificar el **archivo de salida** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
