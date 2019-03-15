---
title: /IDLOUT (Dar nombre a los archivos de resultados de MIDL)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: 3816bb85cb3c711075e3fefeec2d706c2f8cc2ff
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821474"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Dar nombre a los archivos de resultados de MIDL)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>Parámetros

*path*<br/>
Una especificación de ruta de acceso absoluta o relativa. Al especificar una ruta de acceso, afectan a solo la ubicación de un archivo .idl; todos los demás archivos se colocan en el directorio del proyecto.

*filename*<br/>
Especifica el nombre del archivo .idl creado por el compilador MIDL. No se supone que ninguna extensión de archivo; especificar *filename*.idl si desea que una extensión de IDL.

## <a name="remarks"></a>Comentarios

La opción /IDLOUT especifica el nombre y la extensión del archivo. idl.

Se llama el compilador de MIDL por el vinculador MSVC al vincular los proyectos que tengan el [módulo](../../windows/module-cpp.md) atributo.

/IDLOUT también especifica los nombres de los otros archivos de salida asociados con el compilador de MIDL:

- *filename*.tlb

- *filename*_p.c

- *filename*_i.c

- *filename*.h

*nombre de archivo* es el parámetro que pasa a/IDLOUT. Si [TLBOUT](tlbout-name-dot-tlb-file.md) se especifica, el archivo .tlb obtendrá su nombre de TLBOUT *filename*.

Si especifica/IDLOUT ni TLBOUT, el vinculador creará vc70.tlb, vc70.idl, vc70_p.c, vc70_i.c y vc70.h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **IDL incrustado** página de propiedades.

1. Modificar el **combinar nombre de archivo Base IDL** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)<br/>
[/IGNOREIDL (No procesar atributos en MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Especificar las opciones de la línea de comandos de MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Compilación de programas con atributos](../../windows/building-an-attributed-program.md)
