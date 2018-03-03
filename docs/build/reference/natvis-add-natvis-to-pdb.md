---
title: -NATVIS (agregar Natvis a PDB) | Documentos de Microsoft
ms.date: 08/10/2017
ms.tgt_pltfrm: 
ms.technology:
- cpp-tools
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20715b48413a705aa2338e7e37538171e4141cad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (agregar Natvis a PDB)
  
> / NATVIS:*nombre de archivo*  
  
## <a name="parameters"></a>Parámetros  
  
*filename*  
Un archivo de Natvis para agregarlo al archivo PDB. Las visualizaciones del depurador inserta en el archivo Natvis desde el archivo PDB.  
  
## <a name="remarks"></a>Comentarios  
  
La opción /NATVIS incrusta las visualizaciones del depurador definidas en el archivo Natvis *filename* en el archivo PDB generado por LINK. Esto permite al depurador mostrar las visualizaciones independientemente del archivo .natvis. Puede utilizar varias opciones de /NATVIS para insertar más de un archivo de Natvis en el archivo PDB generado.  
  
LINK omite /NATVIS cuando un archivo PDB no se crea mediante el uso de un [/DEBUG](../../build/reference/debug-generate-debug-info.md) opción. Para obtener información sobre la creación y el uso de los archivos .natvis, consulte [crear vistas personalizadas de los objetos nativos en el depurador de Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **línea de comandos** página de propiedades de la **vinculador** carpeta.  
  
3.  Agregar la opción de /NATVIS el **opciones adicionales** cuadro de texto.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Esta opción no tiene un equivalente en programación.  
  
## <a name="see-also"></a>Vea también  
  
[Crear vistas personalizadas de los objetos nativos en el depurador de Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)  
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)