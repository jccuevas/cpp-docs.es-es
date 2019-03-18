---
title: / NATVIS (agregar Natvis a PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: e758a49b41a17d805b752947cd1944087c8ff852
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809241"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (agregar Natvis a PDB)

> /NATVIS:*filename*

## <a name="parameters"></a>Parámetros

*filename*<br/>
Un archivo Natvis para agregar al archivo PDB. Las visualizaciones del depurador incrusta en el archivo .natvis en el archivo PDB.

## <a name="remarks"></a>Comentarios

La opción /NATVIS incrusta las visualizaciones del depurador definidas en el archivo Natvis *filename* en el archivo PDB generado por el vínculo. Esto permite al depurador mostrar las visualizaciones independientemente de que el archivo .natvis. Puede usar varias opciones /NATVIS para insertar más de un archivo Natvis en el archivo PDB generado.

LINK omite /NATVIS cuando un archivo PDB no se crea mediante el uso de un [/DEBUG](debug-generate-debug-info.md) opción. Para obtener información sobre la creación y uso de los archivos .natvis, consulte [crear vistas personalizadas de los objetos nativos en el depurador de Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **línea de comandos** página de propiedades de la **vinculador** carpeta.

1. Agregue la opción de /NATVIS el **opciones adicionales** cuadro de texto.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Esta opción no tiene un equivalente mediante programación.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
