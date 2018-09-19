---
title: -PDBSTRIPPED (quitar símbolos privados) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
dev_langs:
- C++
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0680f265214849c2e46c4ceb23dcb71bdff61c3f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710845"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Quitar símbolos privados)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Argumentos

*pdb_file_name*<br/>
Un nombre especificado por el usuario para la base de datos de programa (PDB) que crea el enlazador.

## <a name="remarks"></a>Comentarios

La opción /PDBSTRIPPED crea un segundo archivo de programa (PDB) de la base de datos cuando se compilación la imagen del programa con cualquiera del compilador o vinculador opciones que generan un archivo PDB ([/DEBUG](../../build/reference/debug-generate-debug-info.md), [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), /Zd o /Zi). En este segundo archivo PDB se omiten los símbolos que no se desea suministrar a los clientes. El segundo archivo PDB solo contendrá:

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **depurar** página de propiedades.

1. Modificar el **quitar símbolos privados** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)