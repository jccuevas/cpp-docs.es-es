---
title: -NATVIS (agregar Natvis a PDB) | Microsoft Docs
ms.date: 08/10/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c1a20fef785c0267eb630bf044c8cb9609605e2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708128"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (agregar Natvis a PDB)

> / NATVIS:*nombre de archivo*

## <a name="parameters"></a>Parámetros

*filename*<br/>
Un archivo Natvis para agregar al archivo PDB. Las visualizaciones del depurador incrusta en el archivo .natvis en el archivo PDB.

## <a name="remarks"></a>Comentarios

La opción /NATVIS incrusta las visualizaciones del depurador definidas en el archivo Natvis *filename* en el archivo PDB generado por el vínculo. Esto permite al depurador mostrar las visualizaciones independientemente de que el archivo .natvis. Puede usar varias opciones /NATVIS para insertar más de un archivo Natvis en el archivo PDB generado.

LINK omite /NATVIS cuando un archivo PDB no se crea mediante el uso de un [/DEBUG](../../build/reference/debug-generate-debug-info.md) opción. Para obtener información sobre la creación y uso de los archivos .natvis, consulte [crear vistas personalizadas de los objetos nativos en el depurador de Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **línea de comandos** página de propiedades de la **vinculador** carpeta.

1. Agregue la opción de /NATVIS el **opciones adicionales** cuadro de texto.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Esta opción no tiene un equivalente mediante programación.

## <a name="see-also"></a>Vea también

[Crear vistas personalizadas de los objetos nativos en el depurador de Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)<br/>
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)