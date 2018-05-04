---
title: -DEFAULTLIB (especificar la biblioteca predeterminada) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e48db05ea50917a09e618c782d86dace73a1bf7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Especificar la biblioteca predeterminada)
```  
/DEFAULTLIB:library  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *Biblioteca de*  
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