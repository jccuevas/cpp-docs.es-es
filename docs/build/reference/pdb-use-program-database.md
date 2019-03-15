---
title: /PDB (Utilizar la base de datos de programa)
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: ddcf83cafd5f499158f3116f04e40397b7f8d0a8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821513"
---
# <a name="pdb-use-program-database"></a>/PDB (Utilizar la base de datos de programa)

```
/PDB:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
Un nombre especificado por el usuario para la base de datos de programa (PDB) que crea el enlazador. Reemplaza el nombre predeterminado.

## <a name="remarks"></a>Comentarios

De forma predeterminada, cuando [/DEBUG](debug-generate-debug-info.md) se especifica, el vinculador crea una base de datos de programa (PDB) que contiene información de depuración. El nombre de archivo predeterminado para el archivo PDB tiene el nombre base del programa y el archivo .pdb de la extensión.

/ PDB:*filename* para especificar el nombre del archivo PDB. Si no se especifica/debug, se omite la opción/PDB.

Un archivo PDB puede ser de hasta 2GB.

Para obtener más información, consulte [archivos .pdb como entrada del vinculador](dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **depurar** página de propiedades.

1. Modificar el **generar archivo de base de datos de programa** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
