---
title: -WINMD (generar metadatos de Windows) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e628713c8228675db3b34e70d670c88152462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376184"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generar metadatos de Windows)
Habilita la generación de un archivo de metadatos en tiempo de ejecución de Windows (.winmd).  
  
```  
/WINMD[:{NO|ONLY}]  
```  
  
## <a name="remarks"></a>Comentarios  
 /WINMD  
 La configuración predeterminada para las aplicaciones de la plataforma Universal de Windows. El enlazador genera el archivo ejecutable binario y el archivo de metadatos de winmd.  
  
 /WINMD:NO  
 El enlazador genera solo el archivo ejecutable binario, pero no es un archivo winmd.  
  
 / WINMD: SOLO  
 El enlazador genera solo el archivo .winmd, pero no el archivo ejecutable binario.  
  
 De forma predeterminada, el nombre de archivo de salida tiene la forma `binaryname`.winmd. Para especificar un nombre de archivo diferente, use la [/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) opción.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **metadatos de Windows** página de propiedades.  
  
4.  En el **generar metadatos de Windows** lista desplegable, seleccione la opción que desee.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)