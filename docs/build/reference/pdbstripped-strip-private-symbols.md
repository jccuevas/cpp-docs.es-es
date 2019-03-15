---
title: /PDBSTRIPPED (Quitar símbolos privados)
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: 3ed36eca727a15a3c70bc51a07cd3c143d7f66da
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815221"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Quitar símbolos privados)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Argumentos

*pdb_file_name*<br/>
Un nombre especificado por el usuario para la base de datos de programa (PDB) que crea el enlazador.

## <a name="remarks"></a>Comentarios

La opción /PDBSTRIPPED crea un segundo archivo de programa (PDB) de la base de datos cuando se compilación la imagen del programa con cualquiera del compilador o vinculador opciones que generan un archivo PDB ([/DEBUG](debug-generate-debug-info.md), [/Z7](z7-zi-zi-debug-information-format.md), /Zd o /Zi). En este segundo archivo PDB se omiten los símbolos que no se desea suministrar a los clientes. El segundo archivo PDB solo contendrá:

- Símbolos públicos

- La lista de archivos objeto y las partes del archivo ejecutable al que contribuyen

- Registros de depuración de marco puntero optimización (FPO) usa para atravesar la pila

El archivo PDB no contendrá:

- Información de tipo

- Información de número de línea

- Símbolos de CodeView de archivo por cada objeto como los relativos a las funciones, variables locales y datos estáticos

El archivo PDB completo todavía se generará cuando se utiliza/PDBSTRIPPED.

Si no crea un archivo PDB, /PDBSTRIPPED se omite.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **depurar** página de propiedades.

1. Modificar el **quitar símbolos privados** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
