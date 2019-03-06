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
ms.openlocfilehash: 6a57e4eb23d40355094f4c8274a42ccb7e1b0e20
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420640"
---
# <a name="pdb-use-program-database"></a>/PDB (Utilizar la base de datos de programa)

```
/PDB:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
Un nombre especificado por el usuario para la base de datos de programa (PDB) que crea el enlazador. Reemplaza el nombre predeterminado.

## <a name="remarks"></a>Comentarios

De forma predeterminada, cuando [/DEBUG](../../build/reference/debug-generate-debug-info.md) se especifica, el vinculador crea una base de datos de programa (PDB) que contiene información de depuración. El nombre de archivo predeterminado para el archivo PDB tiene el nombre base del programa y el archivo .pdb de la extensión.

/ PDB:*filename* para especificar el nombre del archivo PDB. Si no se especifica/debug, se omite la opción/PDB.

Un archivo PDB puede ser de hasta 2GB.

Para obtener más información, consulte [archivos .pdb como entrada del vinculador](../../build/reference/dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **depurar** página de propiedades.

1. Modificar el **generar archivo de base de datos de programa** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
