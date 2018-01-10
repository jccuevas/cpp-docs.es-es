---
title: -LIBPATH (directorios de bibliotecas adicionales) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs: C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 452158c2767ec4f0bf30a88df17b7c01496e24e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (Directorios de bibliotecas adicionales)
```  
/LIBPATH:dir  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 `dir`  
 Especifica una ruta de acceso que el vinculador buscará antes de que busca en la ruta de acceso especificada en la opción de entorno LIB.  
  
## <a name="remarks"></a>Comentarios  
 Use la opción/libpath para invalidar la ruta de acceso de la biblioteca de entorno. El vinculador se buscar primero en la ruta de acceso especificada por esta opción y, a continuación, buscar en la ruta de acceso especificada en la variable de entorno LIB. Puede especificar solo un directorio para cada opción /LIBPATH que especifique. Si desea especificar más de un directorio, debe especificar varias opciones/LIBPATH. El vinculador buscará los directorios especificados en orden.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **General** página de propiedades.  
  
4.  Modificar el **directorios de bibliotecas adicionales** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)