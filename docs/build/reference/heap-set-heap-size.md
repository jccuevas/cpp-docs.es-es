---
title: -HEAP (establecer el tamaño de montón) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
dev_langs:
- C++
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b968b3c8e9063eea897c70d4ae2a62a9a232d6b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="heap-set-heap-size"></a>/HEAP (Establecer el tamaño del montón)
```  
/HEAP:reserve[,commit]  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /HEAP establece el tamaño del montón en bytes. Esta opción es únicamente para su uso cuando se crea un archivo .exe.  
  
 El *reservar* argumento especifica la asignación del montón total de memoria virtual. El tamaño del montón predeterminado es 1 MB. El vinculador se redondea el valor especificado a los 4 bytes más cercanos.  
  
 Opcional `commit` argumento especifica la cantidad de memoria física para asignar a la vez. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Una mayor `commit` valor, ahorrará tiempo cuando la aplicación necesite más espacio del montón, pero aumentarán los requisitos de memoria y, posiblemente, el tiempo de inicio.  
  
 Especifique el *reservar* y `commit` valores en formato decimal o notación del lenguaje c.  
  
 Esta funcionalidad también está disponible a través de un archivo de definición de módulo con [HEAPSIZE](../../build/reference/heapsize.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **System** página de propiedades.  
  
4.  Modificar el **tamaño dedicado del montón** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)