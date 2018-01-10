---
title: -DEFAULTLIB (especificar la biblioteca predeterminada) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs: C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40fe07543dd9dc65d93cc9f79504f5fd324204dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Especificar la biblioteca predeterminada)
```  
/DEFAULTLIB:library  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *biblioteca de*  
 El nombre de una biblioteca para buscar al resolver referencias externas.  
  
## <a name="remarks"></a>Comentarios  
 La opción /DEFAULTLIB agrega uno *biblioteca* a la lista de bibliotecas que LINK busca durante la resolución de referencias. Se busca en una biblioteca especificada con DEFAULTLIB después bibliotecas especificadas en la línea de comandos y antes de las bibliotecas predeterminadas mencionadas en los archivos .obj.  
  
 El [omitir todas las bibliotecas predeterminadas](../../build/reference/nodefaultlib-ignore-libraries.md) (/ NODEFAULTLIB) opción reemplaza a/DEFAULTLIB:*biblioteca*. El [Omitir bibliotecas](../../build/reference/nodefaultlib-ignore-libraries.md) (/ NODEFAULTLIB:*biblioteca*) opción reemplaza a/DEFAULTLIB:*biblioteca* cuando el mismo *biblioteca* nombre es especifica en ambos.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
-   Esta opción del vinculador no está disponible desde el entorno de desarrollo de Visual Studio. Para agregar una biblioteca a la fase de vinculación, use la **dependencias adicionales** propiedad desde el **entrada** página de propiedades.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)