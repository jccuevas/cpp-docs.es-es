---
title: -OUT (nombre de archivo de salida) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
dev_langs:
- C++
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fd9ec1b1631104355e076071370f627a36b4037
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="out-output-file-name"></a>/OUT (Nombre del archivo de resultados)
```  
/OUT:filename  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *filename*  
 Un nombre especificado por el usuario para el archivo de salida. Reemplaza el nombre predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 La opción/out reemplaza el nombre predeterminado y la ubicación del programa que crea el vinculador.  
  
 De forma predeterminada, el vinculador compone el nombre del archivo con el nombre base del primer archivo .obj especificado y la extensión correspondiente (.exe o .dll).  
  
 Esta opción, el nombre base predeterminado para una biblioteca .mapfile o importación. Para obtener más información, consulte [generar archivo de asignaciones](../../build/reference/map-generate-mapfile.md) (/Map) y [/IMPLIB](../../build/reference/implib-name-import-library.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **General** página de propiedades.  
  
4.  Modificar el **archivo de salida** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)